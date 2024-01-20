---
title: "Смартфон - тотальный деблоат и FOSS. Библия цифроанархиста - Том 2."
date: '2024-01-20 19:00:00 +0300'
categories: [Технические шоколадки]
tags: [техника, логика]
image: 
  path: /assets/img/posts/digital-anarchist-android/post_photo.webp
  alt: Фото автора joey zanotti по лицензии CC BY 2.0 Deed
toc: true
---

## Преамбула

И снова вас приветствую, мои дорогие немногочисленные читатели, это второй том **"Библии цифроанархиста"**! В нём я бы хотел поконкретнее разобрать то, что у вас каждый день находится в руках — это ваш смартфон. Я постараюсь вам показать, как его приблизить к FOSS. Вся вводная часть находится в [первом томе](digital-anarchist-ecosystem), её чтение крайне рекомендуется для лучшего понимания того, что я хочу показать вам здесь и для чего это всё нужно в принципе.

Сразу скажу, что владельцев iPhone я вынесу за скобки, так как iPhone, в отличии от Android, является просто цитаделью так называемой "проприетарщины". Избавиться от сервисов Apple в их устройствах почти невозможно — всё буквально прибито гвоздями и вы никак не сможете искоренить дух старшего брата из вашего Яблока. Так что, если у вас вдруг iPhone и вам не всё равно на FOSS выкидывайте ваш iPhone и возвращайтесь с нормальным устройством (ну или просто закройте эту статью).

## Деблоат

### Прошивка

Первым делом, я хотел бы начать с того, что есть два пути для деблоата/дегуглофикации вашего устройства. Первый — искоренять мусор на стоковой прошивке. Я считаю, что этот метод нужно применять в самых крайних случаях, ибо это сложно и часто игра не стоит свеч. Тем более, когда можно установить изначально открытую и чистую прошивку.

Есть множество различных прошивок, которые могут подходить под наши критерии. Я, например, прямо сейчас использую на своём устройстве [crDroid](https://crdroid.net/), это хорошая чистая прошивка с открытым исходным кодом и множеством прикольных фич. Также вам может подойти множество других прошивок с открытым исходным кодом, таких как [LineageOS](https://lineageos.org/) (ранее CyanogenMod[^1]), [DivestOS](https://divestos.org/) и другие прошивки с открытым исходным кодом[^2].

Никаких гайдов по установке здесь вы не увидите, так как процесс может отличаться от устройства к устройству, главное что я хочу заметить — официальные сборки прошивок (маркируются как **OFFICIAL**) должны быть в приоритете, в отличии от неофициальных (самолепных) от какого-то Васи с 4PDA. Неофициальные сборки к установке я крайне не рекомендую, так как возможна угроза компрометации, мало ли что этот самый Вася закинул в сборку[^3], сам о таких инцидентах не слышал, но всякое возможно.

Итак мы выбрали прошивку и установили её. Что же дальше? Приятное осознание того, что вы наконец-то избавили свой смартфон от мусора Google и вендора вашего смартфона. Но что же делать дальше? А вот что, мы будем устанавливать FOSS приложения из открытого магазина.

## Приложения

Итак, начнем. Для начала устанавливаем приложение F-Droid по этой ссылке: [https://f-droid.org/FDroid.apk](https://f-droid.org/FDroid.apk) или отсканировав QR-код ниже (в большинство кастомных прошивок сейчас ставится приложение "Камера" со встроенным сканером QR-кодов):
![QR-код для скачивания F-Droid](/assets/img/posts/digital-anarchist-android/fdroid-qr.webp)

А пока F-Droid скачивается, я расскажу вам, что это такое. F-Droid — это каталог приложений FOSS для платформы Android. F-Droid упрощает просмотр, установку и отслеживание обновлений на вашем устройств. [^4] Проще говоря, это Google Play, который не принимает в себя закрытый исходный код. Вообще. В нём например нет Firefox, так как это браузер с полуоткрытым исходным кодом.

У некоторых приложений в этом магазине есть, так называемые, Анти-функции. [^5] Например реклама, или несвободные сетевые сервисы. F-Droid покажет вам, чем грешно то или иное приложение и вы сможете сделать выбор — устанавливать и пользоваться им или нет.

Ну что же, давайте я вам покажу свою подборку FOSS-приложений, которые вам могут пригодится.

### Aurora Store — неофициальный клиент Google Play

Aurora Store — это неофициальный FOSS-клиент для Google Play с элегантным дизайном и приватностью. Его главное преимущество — возможность скачивать приложения из Google Play без аккаунта Google, настоящая находка, ведь иногда всё же не получается найти FOSS-аналог для какого-нибудь приложения. Тогда идеальным вариантом для вас будет установить приложение из Google Play с помощью Aurora Store. Также в него есть интеграция с сервисом Exodus Privacy.

![Скриншот Aurora Store](/assets/img/posts/digital-anarchist-android/aurora_store_screenshot_1.webp){: width="150" .normal}![Скриншот Aurora Store](/assets/img/posts/digital-anarchist-android/aurora_store_screenshot_2.webp){: width="150" .normal}![Скриншот Aurora Store](/assets/img/posts/digital-anarchist-android/aurora_store_screenshot_3.webp){: width="150" .normal}![Скриншот Aurora Store](/assets/img/posts/digital-anarchist-android/aurora_store_screenshot_4.webp){: width="150" .normal}

Ссылка для скачивания: [https://f-droid.org/ru/packages/com.aurora.store/](https://f-droid.org/ru/packages/com.aurora.store/)
![QR-код Aurora Store в F-Droid](/assets/img/posts/digital-anarchist-android/aurora_store_qr.webp)

### Mull — веб-браузер, ориентированный на конфиденциальность

Mull — это ориентированный на приватность и деблобированный веб-браузер, основанный на технологии Mozilla. Он включает многие функции, реализованные в проекте [Tor Uplift](https://wiki.mozilla.org/Security/Tor_Uplift), используя конфигурацию из проекта [arkenfox-user.js](https://github.com/arkenfox/user.js). Это привычный Firefox, но только такой, каким он должен был быть.

![Скриншот Mull](/assets/img/posts/digital-anarchist-android/mull_screenshot_1.webp){: width="150" .normal}![Скриншот Mull](/assets/img/posts/digital-anarchist-android/mull_screenshot_2.webp){: width="150" .normal}![Скриншот Mull](/assets/img/posts/digital-anarchist-android/mull_screenshot_3.webp){: width="150" .normal}![Скриншот Mull](/assets/img/posts/digital-anarchist-android/mull_screenshot_4.webp){: width="150" .normal}

Ссылка для скачивания: [https://f-droid.org/ru/packages/us.spotco.fennec_dos/](https://f-droid.org/ru/packages/us.spotco.fennec_dos/)

![QR-код Mull в F-Droid](/assets/img/posts/digital-anarchist-android/mull_qr.webp)

### K-9 Mail — полнофункциональный почтовый клиент

K-9 Mail — это почтовый клиент с открытым исходным кодом который работает с абсолютно любым поставщиком электронной почты. Обладает крайне удобной папкой «Вся почта», которая собирает письма со всех ящиков. У меня например примерно пять ящиков и мне крайне неудобно проверять письма в каждом по отдельности, как это сделано в большинстве других ящиках. K-9 полностью решает эту проблему собирая всё в одной папке, что очень удобно.

![Скриншот K-9 Mail](/assets/img/posts/digital-anarchist-android/k9_screenshot_1.webp){: width="150" .normal}![Скриншот K-9 Mail](/assets/img/posts/digital-anarchist-android/k9_screenshot_2.webp){: width="150" .normal}![Скриншот K-9 Mail](/assets/img/posts/digital-anarchist-android/k9_screenshot_3.webp){: width="150" .normal}![Скриншот K-9 Mail](/assets/img/posts/digital-anarchist-android/k9_screenshot_4.webp){: width="150" .normal}

Ссылка для скачивания: [https://f-droid.org/ru/packages/com.fsck.k9/](https://f-droid.org/ru/packages/com.fsck.k9/)

![QR-код K-9 Mail в F-Droid](/assets/img/posts/digital-anarchist-android/k9_qr.webp)

### LibreTube — свободный клиент YouTube

LibreTube - это альтернативный фронтенд для YouTube. Он использует Piped API для загрузки данных и воспроизведения видео, поэтому ему не нужен аккаунт YT и сервисы Google на вашем устройстве.

В прошлой статье цикла я говорил про YouTube ReVanced[^6], но я хочу сказать, что это решение гораздо лучше подойдет, если вы обычный зритель, в нём нет ненужных функций, рекламы и прочего отвлекающего от просмотра мусора. Если вы заядлый зритель YouTube — смело ставьте.

![Скриншот LibreTube](/assets/img/posts/digital-anarchist-android/libretube_screenshot_1.webp){: width="150" .normal}![Скриншот LibreTube](/assets/img/posts/digital-anarchist-android/libretube_screenshot_2.webp){: width="150" .normal}![Скриншот LibreTube](/assets/img/posts/digital-anarchist-android/libretube_screenshot_3.webp){: width="150" .normal}![Скриншот LibreTube](/assets/img/posts/digital-anarchist-android/libretube_screenshot_4.webp){: width="150" .normal}

Ссылка для скачивания: [https://f-droid.org/ru/packages/com.github.libretube/](https://f-droid.org/ru/packages/com.github.libretube/)

![QR-код LibreTube в F-Droid](/assets/img/posts/digital-anarchist-android/libretube_qr.webp)

### OpenBoard — открытая клавиатура, которая не шпионит за тобой

OpenBoard - это на все сто процентов FOSS-клавиатура, основанная на AOSP, не зависящая от бинарных файлов Google и уважающая вашу конфиденциальность. Она хорошо кастомизируется, имеет функцию проверки правописания, настройку тем, ну и конечно же поддерживает Эмодзи, словом делает всё, что требуется от клавиатуры. На скриншотах английская раскладка, но русский язык тоже полностью поддерживается.

![Скриншот OpenBoard](/assets/img/posts/digital-anarchist-android/openboard_screenshot_1.webp){: width="150" .normal}![Скриншот OpenBoard](/assets/img/posts/digital-anarchist-android/openboard_screenshot_2.webp){: width="150" .normal}![Скриншот OpenBoard](/assets/img/posts/digital-anarchist-android/openboard_screenshot_3.webp){: width="150" .normal}![Скриншот OpenBoard](/assets/img/posts/digital-anarchist-android/openboard_screenshot_4.webp){: width="150" .normal}

Ссылка для скачивания: [https://f-droid.org/ru/packages/org.dslul.openboard.inputmethod.latin/](https://f-droid.org/ru/packages/org.dslul.openboard.inputmethod.latin/)

![QR-код OpenBoard в F-Droid](/assets/img/posts/digital-anarchist-android/openboard_qr.webp)

### KeePassDX — безопасный и открытый менеджер паролей

KeePassDX — мультиформатный менеджер паролей KeePass, приложение позволяет сохранять и использовать пароли, ключи и цифровые идентификаторы в безопасном режиме, интегрируя стандарты дизайна Android, и не требует подключения к Интернету.

Крайне крутое решение для хранения ваших аутентификационных данных любого формата. Думаю мне не стоит говорить, что хранение ваших логинов и паролей в браузере в высшей степени небезопасно — они там никак не шифруются! Большая часть малвари нацелена именно на данные браузера и хранить ваши пароли в нём всё равно что выставить свои данные с пометкой «бесплатно, подходи и бери на здоровье». Если ваши данные находятся в браузере — в срочном порядке выделите время на то, чтобы перенести их в нормальный менеджер паролей с шифрованием, коим наш KeePass и является. Я пользуюсь связкой KeePassDX на смартфоне и [KeePassXC](https://keepassxc.org/) на компьютере. Давайте вернёмся к KeePassXC:

- Создание файлов базы данных / записей и групп.
- Поддержка файлов .kdb и .kdbx (версии от 1 до 4) с алгоритмом AES - Twofish - ChaCha20 - Argon2.
- Совместимость с большинством альтернативных программ (KeePass, KeePassXC, KeeWeb, ...).
- Позволяет быстро открывать и копировать поля URI / URL.
- Биометрическое распознавание для быстрой разблокировки (отпечаток пальца / разблокировка по лицу / ...).
- Управление одноразовыми паролями (HOTP / TOTP) для двухфакторной аутентификации (2FA).
- Автозаполнение и интеграция.
- Клавиатура для заполнения полей.
- Динамические шаблоны.
- История каждой записи.

![Скриншот KeePassDX](/assets/img/posts/digital-anarchist-android/keepassdx_screenshot_1.webp){: width="150" .normal}![Скриншот KeePassDX](/assets/img/posts/digital-anarchist-android/keepassdx_screenshot_2.webp){: width="150" .normal}![Скриншот KeePassDX](/assets/img/posts/digital-anarchist-android/keepassdx_screenshot_3.webp){: width="150" .normal}![Скриншот KeePassDX](/assets/img/posts/digital-anarchist-android/keepassdx_screenshot_4.webp){: width="150" .normal}

Ссылка для скачивания: [https://f-droid.org/ru/packages/com.kunzisoft.keepass.libre/](https://f-droid.org/ru/packages/com.kunzisoft.keepass.libre/)

![QR-код KeePassDX в F-Droid](/assets/img/posts/digital-anarchist-android/keepassdx_qr.webp)

### Neo Backup — Инструмент создания 

Neo Backup — cоздаёт и восстанавливает резервные копии приложений на вашем устройстве и сохраняет их данные в место, доступное пользователю. Поддерживает резервирование и восстановление одного или нескольких приложений. Это приложение является продолжением проекта [OAndBackup (больше не разрабатывается)](https://f-droid.org/ru/packages/dk.jens.backup/).

Этим приложением я пользуюсь довольно давно, оно работает как магия, взял — и откатил свои приложение на день раньше, ну или например после переустановки прошивки можно быстро вернуть все приложения которые были установлены до переустановки. Причем в резервных копиях сохраняется полное состояние приложение, вместе с APK-файлом и всеми данными, есть приличный шанс, что сохранятся даже аутентификационные данные и вас не разлогинит из какого-то приложения. Работает это гораздо лучше, чем резервное копирование от Google. Также в этом приложении можно очень легко настроить резервное копирование по расписанию, я например поставил его ночью, чтобы резервное копирование происходило тогда, когда я не пользуюсь смартфоном. Короче говоря, очень мощное бэкап-решение.

![Скриншот NeoBackup](/assets/img/posts/digital-anarchist-android/neobackup_screenshot_1.webp){: width="150" .normal}![Скриншот NeoBackup](/assets/img/posts/digital-anarchist-android/neobackup_screenshot_2.webp){: width="150" .normal}![Скриншот NeoBackup](/assets/img/posts/digital-anarchist-android/neobackup_screenshot_3.webp){: width="150" .normal}![Скриншот NeoBackup](/assets/img/posts/digital-anarchist-android/neobackup_screenshot_4.webp){: width="150" .normal}

Ссылка для скачивания: [https://f-droid.org/ru/packages/com.machiav3lli.backup/](https://f-droid.org/ru/packages/com.machiav3lli.backup/)

![QR-код Neo Backup в F-Droid](/assets/img/posts/digital-anarchist-android/neobackup_qr.webp)

### Syncthing — синхронизация файлов

Syncthing заменяет проприетарные сервисы синхронизации и облачные сервисы на что-то открытое, надежное и децентрализованное. Ваши данные - это только ваши данные, и вы заслуживаете право выбирать, где они хранятся, передаются ли третьим лицам и каким образом передаются через Интернет.

Я не вижу смысла говорить больше про Syncthing, ведь я сказал уже очень много про это замечательное решение в своём первом томе библии цифроанархиста. [^6] Скажу только то, что Syncthing отлично сочетается с KeePass и NeoBackup, и ваши файлы перелетают между вашими устройствами как по волшебству. Банальный пример — я делаю фотографию на своём смартфоне и она моментально оказывается на моём компьютере, где я её могу открыть и отредактировать, а изменения окажутся сразу же в смартфоне.

![Скриншот Syncthing](/assets/img/posts/digital-anarchist-android/syncthing_screenshot_1.webp){: width="150" .normal}![Скриншот Syncthing](/assets/img/posts/digital-anarchist-android/syncthing_screenshot_2.webp){: width="150" .normal}![Скриншот Syncthing](/assets/img/posts/digital-anarchist-android/syncthing_screenshot_3.webp){: width="150" .normal}![Скриншот Syncthing](/assets/img/posts/digital-anarchist-android/syncthing_screenshot_4.webp){: width="150" .normal}

Ссылка для скачивания: [https://f-droid.org/ru/packages/com.nutomic.syncthingandroid/](https://f-droid.org/ru/packages/com.nutomic.syncthingandroid/)

![QR-код Syncthing в F-Droid](/assets/img/posts/digital-anarchist-android/syncthing_qr.webp)

### Symphony — оффлайн музыка теперь проста

Symphony - это легкий и элегантный музыкальный плеер, который улучшит ваши впечатления от прослушивания музыки в автономном режиме.

Пока что это самый удобный музыкальный плеер, что я нашел среди FOSS-решений. У него конечно нет встроенного эквалайзера, но он поддерживает все типы аудиофайлов. В общем, изучите его возможности и выберите свой музыкальный плеер.

![Скриншот Symphony](/assets/img/posts/digital-anarchist-android/symphony_screenshot_1.webp){: width="150" .normal}![Скриншот Symphony](/assets/img/posts/digital-anarchist-android/symphony_screenshot_2.webp){: width="150" .normal}![Скриншот Symphony](/assets/img/posts/digital-anarchist-android/symphony_screenshot_3.webp){: width="150" .normal}![Скриншот Symphony](/assets/img/posts/digital-anarchist-android/symphony_screenshot_4.webp){: width="150" .normal}

Ссылка для скачивания: [https://f-droid.org/ru/packages/io.github.zyrouge.symphony/](https://f-droid.org/ru/packages/io.github.zyrouge.symphony/)

![QR-код Symphony в F-Droid](/assets/img/posts/digital-anarchist-android/symphony_qr.webp)

### Галерея Fossify — простая галерея с редактором

Откройте воспоминания, а не личные данные. Fossify Gallery - это лучшее приложение для работы с фото и видео, которое настолько же мощно, насколько и конфиденциально. Никакой рекламы, никаких лишних разрешений - только удобство, созданное специально для вас.

Это простое приложение галереи, которое заменит собой немощное стоковое. Здесь есть удобный редактор фото. Приложение поддерживает все популярные форматы изображений и видео. Ну и Fossify Gallery выполнено в стиле Material You и подстраивает свою цветовую схему с настройками системы.

![Скриншот Галереи Fossify](/assets/img/posts/digital-anarchist-android/fossify_gallery_screenshot_1.webp){: width="150" .normal}![Скриншот Галереи Fossify](/assets/img/posts/digital-anarchist-android/fossify_gallery_screenshot_2.webp){: width="150" .normal}![Скриншот Галереи Fossify](/assets/img/posts/digital-anarchist-android/fossify_gallery_screenshot_3.webp){: width="150" .normal}![Скриншот Галереи Fossify](/assets/img/posts/digital-anarchist-android/fossify_gallery_screenshot_4.webp){: width="150" .normal}

Ссылка для скачивания: [https://f-droid.org/ru/packages/org.fossify.gallery/](https://f-droid.org/ru/packages/org.fossify.gallery/)

![QR-код Галереи Fossify в F-Droid](/assets/img/posts/digital-anarchist-android/fossify_gallery_qr.webp)

### VLC — мощный медиа-проигрыватель

Ну и последним, но не по значению, я бы хотел вам представить VLC. Этот мощнейший и функциональный медиапроигрыватель не нуждается в представлении. Возможно для вас станет сюрпризом тот факт, что он является FOSS, но это действительно так, и поэтому он доступен в F-Droid.

Говорить про него мне нечего — установить не задумываясь ни секунды!

![Скриншот VLC](/assets/img/posts/digital-anarchist-android/vlc_screenshot_1.webp){: width="150" .normal}![Скриншот VLC](/assets/img/posts/digital-anarchist-android/vlc_screenshot_2.webp){: width="150" .normal}![Скриншот VLC](/assets/img/posts/digital-anarchist-android/vlc_screenshot_3.webp){: width="150" .normal}

Ссылка для скачивания: [https://f-droid.org/ru/packages/org.videolan.vlc/](https://f-droid.org/ru/packages/org.videolan.vlc/)

![QR-код VLC в F-Droid](/assets/img/posts/digital-anarchist-android/vlc_qr.webp)

### БОНУС: Forkgram - прокачанный Telegram-клиент

Forkgram — это форк официального приложения Telegram для Android, который обладает дополнительным функционалом. Он не является полностью открытым, но всё равно был включен в F-Droid. Во неполный список возможностей, которые открывает Forkgram по сравнению с оригинальным приложением:

- опция "Удалить для всех" включена по умолчанию;
- убран плавающий значок карандаша;
- оригинальная дата сообщения для пересылаемых сообщений;
- уменьшен размер заголовка в боковой панели;
- опция отключения камеры в приложении;
- опция сохранения непрочитанных чатов без звука сразу после прикрепленных диалогов;
- отображение корректного полного числа подписчиков в группах/каналах;
- опция перехода к первому сообщению в чате;
- добавлены дополнительные опции длительности отключения звука (3 часа, 1 день);
- кнопка быстрой публикации для каждого медиафайла в личных чатах;
- возможность начать запись видеосообщений с помощью задней камеры;
- неограниченное количество неархивированных прикрепленных чатов (их синхронизация отключена);
- опция отключения больших эмодзи;
- пересылка сообщений без цитирования отправителя;
- добавлено множество опций таймера самоуничтожения в секретных чатах;
- при нажатии на облачный GIF с заранее написанным текстом будет отправлен GIF с этим текстом в качестве подписи;
- при нажатии на стикер с заранее написанным текстом отправляются оба стикера;
- добавлена дата загрузки фотографий профиля;
- добавлена возможность просмотра информации о профиле из списка диалогов через контекстное меню;
- добавлена возможность видеть счетчик непрочитанных сообщений, когда вы хотите отметить как прочитанные несколько диалогов;
- опция прямого открытия архива в выпадающем списке;
- режим PiP для встроенного плеера YouTube;
- и многое другое...

Ссылка для скачивания: [https://f-droid.org/ru/packages/org.forkgram.messenger/](https://f-droid.org/ru/packages/org.forkgram.messenger/)

![QR-код Forkgram в F-Droid](/assets/img/posts/digital-anarchist-android/forkgram_qr.webp)

## Заключение

В общем, я рассказал про открытые приложения, которыми я пользуюсь чаще всего, на самом деле их больше. Я спешу вам заявить, что полностью избавиться от проприетарного софта пока не представляется возможным, как минимум из-за банковских приложений, да и Linux ядро, которое используется в Android, не является полностью открытым, в нем присутствуют так называемые «блобы», некоторые из которых, являются важными компонентами. Но запомните, чем меньше у вас процент «проприетарщины» в системе, тем вы независимее от корпораций. Большинство людей приняли, что Linux не является полностью свободным, но помните, что есть Linux-libre.

Пожалуйста напишите в комментариях о своих FOSS-приложениях, которыми вы пользуетесь, будет интересно посмотреть и изучить!

[^1]: [CyanogenMod — Wikipedia (RU)](https://ru.wikipedia.org/wiki/CyanogenMod)
[^2]: [List of custom Android distributions — Wikipedia (EN)](https://en.wikipedia.org/wiki/List_of_custom_Android_distributions)
[^3]: [With 3rd party ROMs from places like xda-developers, how do you REALLY know those ROMs are safe? How can you trust they haven't had malware/spyware installed? — Тред на Reddit от пользователя capran (01.08.2018)](https://www.reddit.com/r/Android/comments/93hzvq/with_3rd_party_roms_from_places_like)
[^4]: [Страница «О F-Droid» — официальный сайт F-Droid](https://f-droid.org/ru/about/)
[^5]: [Антифичи — документация F-Droid](https://f-droid.org/ru/docs/Anti-Features/)
[^6]: [Про корпорации, FOSS и как сделать лучшую экосистему у себя дома. Библия цифроанархиста - Том 1 — NukDokPlex (03.11.2023)](/posts/digital-anarchist-ecosystem)
