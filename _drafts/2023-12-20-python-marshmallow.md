---
title: "Marshmallow в Python: Автомагическая валидация и (де)сериализация"
date: '2023-12-19 15:00:00 +0300'
categories: [Дзен]
tags: [эмпатия, лимбическая система, внутренняя империя]
image: 
  path: /assets/img/posts/tale-of-the-little-computer.webp
  alt: Изображение сгенерировано нейросетью Stable Diffusion (модель ComfyrollAnime_v1_fp16_pruned)
toc: true
---

## Введение

[Marshmallow](https://marshmallow.readthedocs.io/) — это очень крутая библиотека для работы со структурами данных. Все проекты на Python, которые так или иначе работают с их валидацией и (де)сериализацией должны использовать именно эту библиотеку. В этом посте я хочу показать вам, почему это так.

Этот пост — **не документация**! Это просто ознакомительная статья для тех, кому нужен краткий обзор этой библиотеки.

## Объявление схем

В Marshmallow используется термин *Схема* (`Schema`) — это тип, который предоставляет вам весь функционал библиотеки. Схема состоит из *полей* (`fields`), которые могут быть самых разных типов. Их очень много, полный их список вы можете [рассмотреть здесь](https://marshmallow.readthedocs.io/en/stable/marshmallow.fields.html).

Давайте сразу объявим какую-нибудь *схему*, пусть это будет схема для объявления книг:

```python
from marshmallow import Schema, fields

class BookSchema(Schema):
  title = fields.Str(
    required=True,
    allow_none=False,
  )
  synopsis = fields.Str(
    required=False,
    allow_none=True,
  )
  isbn = fields.Str(
    required=True,
    allow_none=False
  )
  rating = fields.Float(
    required=True,
    allow_none=False,
    allow_nan=False,
  )
```

Отлично, мы объявили схему для книг. Как вы видите, здесь есть поля `title`, `synopsis`, `isbn` и `rating`. Также внутри них мы задали базовые аргументы для *валидации*:

 - `required` - задаёт, является ли поле обязательным в объекте. Если `required=True`, то наша схема проверит, есть ли такое поле в данных, которые мы предоставили, если такого поля нет, то она вернет исключение, о котором мы поговорим чуть позже;
 - `allow_none` - устанавливает, может ли поле быть `None`. Если `allow_none=False`, то схема не пропустит значение `None` в данном поле и вернет исключение.
 - `allow_nan` - тут так же всё просто, если `allow_nan=False`, то схема не пропустит в этом поле значения, не являющиеся числами.

Так, схему мы объявили настроили в ней базовую валидацию, что же теперь? Я бы посоветовал сразу же после объявления класса её проинициализировать и использовать только её проинициализированный экземпляр.

```python
book_schema = BookSchema()
```

Это нужно, чтобы каждый раз не инициализировать схему в рантайме, на это тратится время. Лучше проинициализировать схему в самом начале исполнения программы и потом использовать её экземпляр.

## Работаем со схемой

У нашей проинициализированной схемы есть два метода: `dump` и `load`. Они выполняют в чём то схожую функцию но путать их не стоит. `load` принимает данные, проверяет их, вызывает исключение, если что-то не так, конвертирует типы данных и возвращает проверенные и сконвертированные данные, готовые к вашей основной логике, этот метод полезен например для валидации запросов пользователя. `dump` в свою очередь занимается **только** конвертацией и не вызывает исключение если с вашими данными что-то не так, так как `dump` не занимается валидацией. Это нужно, например, когда требуется вернуть по запросу пользователя что-то из базы данных — просто засовываете в `dump` результат запроса из базы данных и она конвертирует данные и убирает лишние поля из результата.

Давайте рассмотрим на примерах:

```python
book_data = {
  'title': "Python - круто!",
  'synopsis': "Книга про то, что Python - это круто.",
  'isbn'
}


