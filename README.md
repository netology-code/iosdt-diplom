# Курсовой проект “Работа с сетью и хранение данных”

В качестве курсового проекта вы разработаете приложение «Погодное приложение". Вы примените полученные знания:

- Адаптивная верстка экранов;

- Различные навигационные паттерны в iOS;

- Использование и настройка визуальных компонентов;

- Использование UITableView, UICollectionView и кастомных ячеек;

- Работа с сетью, а именно:
  - Получение данных из сети;
  - Обработка этих данных;
  - Сохранение этих данных в базу данных.

## Требования к проекту

- Проект должен запускаться без ошибок;
- Верстка приложения реализована либо в коде, либо в Interface Builder;
- Верстка приложения адаптивная, интерфейс выглядит хорошо на различных устройствах, в том числе на iPad;
- Код проекта написан в одном стиле. Обратите внимание на названия классов, переменных и функций;
- Сетевые запросы запускаются не в основном потоке, UI не тормозится.

## Работа с дизайном

Для того, чтобы условия разработки были максимально приближенными к реальности, весь дизайн приложения отрисован в figma - https://www.figma.com/file/z7Z9JYnxoOI4g4nVCX8BYU/%D0%BF%D0%BE%D0%B3%D0%BE%D0%B4%D0%B0?node-id=0%3A1. Все картинки и цвета и расположения элементов находятся в проекте figma. Работа с figma максимально интуитивная, но если вам что-то будет непонятно, то вот 5-ти минутное видео с подробным рассказом - https://www.youtube.com/watch?v=c1sCRKOWTQw

## Работа с данными

Все данные должны кэшироваться в базе данных (можно использовать любой фреймворк, который будет вам удобен - CoreData или Realm и различного рода обертки).

## Работа с сетью

Можете использовать любой фреймворк для работы с сетью, предпочтительнее использовать Alamofire или Moja.

Для работы с JSON так же не возброняется использовать фреймворк, однако предпочтительнее использовать Decodable.

## Дизайн приложения

Прежде всего, необходимо спросить у пользователя о разрешении на использование геолокации, так как это необходимо, с точки зрения политики конфиденциальности - 

КАРТИНКА

После того, как пользователь дал или не дал согласие на использование геолокации, приложение должно показать экран настроек для выбора единиц измерения. Следует это делать лишь после первого запуска приложения

КАРТИНКА

После нажатия на кнопку Установить, пользователь должен провалиться на следующий экран - 

КАРТИНКА

Это и есть основной экран приложения, на котором будет отображаться погода, влажность, осадки, длина светового для время, дата и скорость ветра.

Сверху у вас есть слайдер. Если вы разрешили доступ к геолокации, то по умолчанию у вас будет экран с погодой для вашего гео.

Как видно из дизайна, сверху слева есть кнопка о выборе местоположения. Это кнопка добавления нового города. При нажатии на эту кнопку должен повиться UIAlertController с возможностью ввода города. 
После ввода и нажатия на кнопку ок, необходимо перевести название города в координаты - это необходимо, так как большинство погодных сервисов принимают на вход пару координат - долготу и широту. Это легче всего делать с помощью сервиса - https://yandex.ru/dev/maps/geocoder/. Подробнее про этот сервис можете прочитать в документации - https://yandex.ru/dev/maps/geocoder/doc/desc/concepts/about.html

После такого действия в слайдере(pageViewController) появится еще один вариант с новым добавленным городом.

Кнопка слева сверху открывает настройки, которые выглядят -

КАРТИНКА

По умолчанию список погоды содержит 7 ячеек, то есть на 7 ближайших дней. Но при нажатии на кнопку 25 дней, список с погодой у вас увеличивается до 25 ячеек (если вы сможете найти такое API) и текст на кнопки меняется на «7 дней». При нажатии еще раз - это возвращает вас в изначальный вариант погоды на 7 дней.

**«Подробнее на 24 часа»**

КАРТИНКА

При нажатии на подробнее на 24 часа должен открываться экран, показанный выше, в котором отображается подробная информация о погоде на сутки.

На этом горизонтальном списке (лучше всего делать с помощью UICollectionView) показывается погода на ближайшие сутки. При выборе элемента на ДОПИСАТЬ КОНЕЦ ФРАЗЫ

КАРТИНКА

Вы попадаете на экран «подробнее на 24 часа» для текущего дня.

При запуске приложения до того, как будет получен ответ о погоде, вам необходимо показывать закодированные значения погоды

## Подробнее про API

Для запроса погоды можно использовать:
* https://openweathermap.org/api
* https://rapidapi.com/stefan.skliarov/api/AccuWeather
* https://developer.yr.no
* https://yandex.ru/dev/weather/ (оно бесплатно месяц)
*  https://rapidapi.com/blog/access-global-weather-data-with-these-weather-apis/

Для геокодинга (перевода названий мест в координаты, можете использовать api яндекса) - https://yandex.ru/dev/maps/geocoder/doc/desc/concepts/about.html

## Отправка работы на проверку

Чтобы отправить работу на проверку, загрузите репозиторий на GitHub.

### Как правильно задавать вопросы дипломному руководителю?

**Что поможет решить большинство частых проблем:**
1. Попробовать найти ответ сначала самому в интернете. Скилл поиска ответов пригодится вам в профессиональной деятельности. И только после этого спрашивать дипломного руководителя.
2. Если вопросов больше одного, то присылайте их в виде нумерованного списка. Так дипломному руководителю будет проще отвечать на каждый из них. 
3. При необходимости прикрепите к вопросу скриншоты и стрелочкой покажите, где не получается. Программу для этого можно скачать [здесь](https://app.prntscr.com/ru).
4. По возможности задавайте вопросы в комментариях к коду. 
5. Начинать работу над проектом как можно раньше, чтобы было больше времени на правки.
6. Делайте проект частями, а не всё сразу. Если сделать всё сразу, то количество комментариев от дипломного руководителя может вас демотивировать. 

**Что может стать источником проблем:**
1. Вопросы вида "Ничего не работает/не запускается/всё сломалось". Дипломный руководитель не сможет ответить на такой вопрос без дополнительных уточнений. Цените своё время и время других.
2. Откладывание проекта на последний момент.
3. Ожидание моментального ответа на свой вопрос. Дипломные руководители — работающие разработчики, которые кроме преподавания занимаются своими проектами. Их время ограничено, поэтому постарайтесь задавать правильные вопросы, чтобы получать быстрые ответы :)
