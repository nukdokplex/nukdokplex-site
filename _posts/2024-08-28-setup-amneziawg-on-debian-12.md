---
title: "Установка AmneziaWG на сервер Debian 12 Bookworm"
date: '2024-08-28 06:00:00 +0300'
categories: [Технические шоколадки]
tags: [техника, логика, энциклопедия]
image:
  path: /assets/img/posts/setup-amneziawg-on-debian.webp
  alt: Фото автора Andrey Metelev по лицензии Unsplash
toc: true
---

## Введение

ДАННАЯ СТАТЬЯ НЕ РАССКАЗЫВАЕТ О СПОСОБАХ ОБХОДА БЛОКИРОВОК К ЗАПРЕЩЕННЫМ РЕСУРСАМ В КАКОЙ ЛИБО ИЗ СТРАН. АВТОР НИКАК НЕ ПОДРАЗУМЕВАЕТ ИСПОЛЬЗОВАНИЕ ТЕХНОЛОГИЙ, ОПИСАННЫХ В СТАТЬЕ, В КАЧЕСТВЕ СПОСОБА ОБХОДА БЛОКИРОВОК ЗАПРЕЩЕННЫХ РЕСУРСОВ. ЦЕЛЬ СТАТЬИ - РАССКАЗАТЬ О СПОСОБЕ ЗАЩИТЫ СОЕДИНЕНИЯ.

Доброго времени суток, дорогой читатель. Если ты здесь, то наверняка ты ищешь информацию про Wireguard, Amnezia, ну и в частности про AmneziaWG (далее AWG), пропатченный Wireguard, который работает в условиях DPI.

Использование AWG актуально в построении виртуальных частных сетей между устройствами. В этой статье я расскажу про то, как поднять сервер AWG на Debian 12 "Bookworm".

## Установка

Прежде всего нам понадобится добавить репозиторий с AWG в `sources.list` пакетного менеджера `apt`.

Для этого нам понадобится установить несколько пакетов:

```shell
sudo apt install -y software-properties-common python3-launchpadlib gnupg2 linux-headers-$(uname -r)
```

Теперь добавим ключ Ubuntu в `apt`, так как репозиторий с AWG находится в сервисе Launchpad:

```shell
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 57290828
```

Добавляем репозиторий в `sources.list`:

```shell
echo "deb https://ppa.launchpadcontent.net/amnezia/ppa/ubuntu focal main" | sudo tee -a /etc/apt/sources.list
echo "deb-src https://ppa.launchpadcontent.net/amnezia/ppa/ubuntu focal main" | sudo tee -a /etc/apt/sources.list
```

Обновляем репозитории и устанавливаем AWG:

```shell
sudo apt-get update
sudo apt-get install -y amneziawg amneziawg-tools
```

На данный момент установку можно считать завершенной.

## Настройка

Люди, которые уже настраивали Wireguard сейчас ощутят чувство дежавю, ведь AWG является форком Wireguard, поэтому в целом настройка AWG во многом схожа, но я все равно распишу всё полностью, чтобы у вас не возникло проблем.

Файлы конфигурации AWG хранятся в директории `/etc/amnezia/amneziawg`. Давайте начнем создавать файлы конфигурации. Для начала сгенерируем приватный и публичный ключ сервера.

```shell
sudo mkdir -p /etc/amnezia/amneziawg
wg genkey | sudo tee /etc/amnezia/amneziawg/privatekey | wg pubkey | sudo tee /etc/amnezia/amneziawg/publickey
```

После этого вы сможете посмотреть эти ключи и скопировать:

```shell
sudo cat /etc/amnezia/amneziawg/privatekey
sudo cat /etc/amnezia/amneziawg/publickey
```

Далее, давайте создадим файл конфигурации, используйте свой любимый текстовый редактор:

```shell
sudo nano /etc/amnezia/amneziawg/wg0.conf
```

Ну и давайте наконец настроим AWG:

```service
[Interface]
Address = 10.0.8.1/24 # Подсеть, которая будет испол
ListenPort = 33733 # Порт сервера
PrivateKey = # Вместо этого комментария вставьте содержимое приватного ключа /etc/amnezia/amneziawg/privatekey
# Если вы хотите, чтобы через этот сервер можно было выходить в Интернет, раскомментируйте следующие строчки и вместо interface_name впишите название интерфейса, через который ваш сервер выходит в Интернет
#PostUp = iptables -A FORWARD -i wg0 -j ACCEPT; iptables -t nat -A POSTROUTING -o ens3 -j MASQUERADE
#PostDown = iptables -D FORWARD -i wg0 -j ACCEPT; iptables -t nat -D POSTROUTING -o ens3 -j MASQUERADE

# Далее идет список специальных настроек "мусора", добавленных в AWG
Jc = # Количество мусорных пакетов, рекомендуется число от 3 до 10 включительно
Jmin = 50 # Минимальный размер мусорного пакета, рекомендованно значение 50
Jmax = 1000 # Максимальный размер мусорного пакета, рекомендовано значение 1000
S1 = # Начальный размер мусорного пакета, рекомендовано число от 15 до 150 включительно
S2 = # Размер ответного мусорного пакета, рекомендовано число от 15 до 150 включительно
# Разработчки AWG утверждают, что значения, при которых S1 + 56 = S2 не рекомендуются
# Следующие H1/H2/H3/H4 НЕ ДОЛЖНЫ БЫТЬ ОДИНАКОВЫМИ, это должны быть случайные числа от 5 до 2147483647
H1 = # Заголовок пакета инициализации 
H2 = # Заголовок пакета ответа
H3 = # Заголовок пакета под нагрузкой
H4 = # Заголовок транспортного пакета

# Типовая настройка пира
[Peer]
PublicKey = # Публичный ключ пира
AllowedIPs = 10.0.8.2/32
```

**Замечу, что все настройки мусора (кроме Jc) должны быть одинаковыми на всех пирах!**

*Примечание: для того чтобы был доступ в интернет внутри сети, нужно включить IP Forwarding, как это сделать, вы можете посмотреть [здесь](https://web.archive.org/web/https://thelinuxcode.com/enable_ip_forwarding_ipv4_debian_linux/).*

## Запуск

К сожалению AWG не обладает интеграцию с `systemd`, поэтому нам придется сделать её самостоятельно:

```shell
sudo nano /etc/systemd/system/awg-quick@.service
```

И вставим следующее содержимое:

```service
[Unit]
Description=WireGuard via awg-quick(8) for %I
After=network-online.target nss-lookup.target
Wants=network-online.target nss-lookup.target
Documentation=man:awg-quick(8)
Documentation=man:awg(8)
Documentation=https://www.wireguard.com/
Documentation=https://www.wireguard.com/quickstart/
Documentation=https://git.zx2c4.com/wireguard-tools/about/src/man/wg-quick.8
Documentation=https://git.zx2c4.com/wireguard-tools/about/src/man/wg.8

[Service]
Type=oneshot
RemainAfterExit=yes
ExecStart=/usr/bin/awg-quick up %i
ExecStop=/usr/bin/awg-quick down %i
ExecReload=/bin/bash -c 'exec /usr/bin/awg syncconf %i <(exec /usr/bin/awg-quick strip %i)'
Environment=WG_ENDPOINT_RESOLUTION_RETRIES=infinity

[Install]
WantedBy=multi-user.target
```

Перезагрузим демон `systemd`:

```shell
sudo systemctl daemon-reload
```

И наконец запустим:

```shell
sudo systemctl start awg-quick@wg0.service
```

После запуска можно проверить статус сервиса: 

```shell
sudo systemctl status awg-quick@wg0.service
```

Ну и проверить наличие интерфейса Wireguard:

```shell
ip a
```

## Заключение

На этом я завершаю эту статью. Если у вас возникли вопросы, вы можете оставить в комментариях, возможно я их прочитаю.