# Тестовое. Фронт-енд разработчик. HTML/CSS/Webpack/Git #
## Описание для ревьюера ##

**Студенту была дана задача сверстать адаптивную страницу поисковика новостей,
используя HTML/CSS и сборщик - Webpack. Проект ведется под Git. Сверстанная страница:**
* Должна корректно отображаться в последних версиях следующих браузеров: GC, FireFo , Safari.
* Страница должна корректно отображаться на мобильных, планшетных и десктопных устройствах разных OC.
* Не должна иметь горизонтальный скролл на разрешениях от 320p .
* Проект должен билдиться, инициализироваться и деплоится GitHub скриптами

*Прокомментируйте верстку, структуру репозитория и инфраструктуру проекта.*

## Комментарии необходимо оставлять под соответствующим критерием, а также зачесть/не зачесть критерий, отметив чекбокс. ##
*Укажите не только места ошибок, но и ее объяснение, а также способ исправления. А также места, где студент хорошо справился с заданием.
Для выполненных критериев отметьте чекбокс*

*Вы можете включать ссылки на ресурсы, абстрактные примеры кода*

## Инфраструктура и Git
- [ ] Вебпак настроен:
    - [х] собирает проект.
    - [x] деплоит сайт на GitHub Pages.
    - [x] переменные окружения запрещены, проект собирается и запускается на любой OC после установки необходимых npm-зависимостей.
    - [x] Локальный сервер установлен и настроен.
    - [x] Хеши проставляются и настроено автоматическое обновление страницы (*hot reload*).
    - [ ] `webpack.config.js` не содержит ошибок и корректно оформлен.

    **OptimizeCssAssetsPlugin - данный плагин зарегестрирован, однако, не используется в конфигурации**

- [ ] Настроен Babel

**Не указаеы плагины, только пресеты. В package.json нет строки с babel. Настройка babel - https://babeljs.io/docs/en/configuration**

- [x] PostCSS установлен и настроен для минификации CSS-кода и простановки вендорных префиксов.
- [x] Плагины корректно устанавливаются.
- [ ] Устранена проблема с нижними подчеркиваниями при публикации на github.
- [х] Продакшн-бандл должен деплоиться на Github Pages скриптом вебпака. (Все необходимые данные должны быть указаны)

**Нет конфигурации скрипта**

- [ ] Работа с Git
  - [ ] `Package.json` содержит всю необходимую информацию

  **Не содержит информацию об авторе. Пустые поля с url**

  - [ ] `.gitignore` содержит все необходимые каталоги и файлы

  **Файл назван неверно, с подчеркиванием вместо точки в начале**

  - [х] Gh-pages

  **Нет дополнительной конфигурации скрипта**

- [x] Исходники проекта хранятся в каталоге `src/`, итоговый билд - в каталоге `dist/`.
- [ ] Бандлы хранятся в отдельной директории каталога `dist/`

**Все хранится в едином файле для js и css. JS хранится в корне директории.**

- [x] У каждого установленного плагина зафиксирована версия.

## HTML и CSS
- [ ] Именование классов и структура файлов сделаны по БЭМ. Отсутствуют ошибки в БЭМ-нейминге сущностей.

**В целом - нейминг правильный, однако, есть опечатки и ошибки. К примеру, auth-form__other-action_left - здесь будет верно использовать не булевое значение, а модификатор --left. Пропущено дополнительное подчеркивание в классах - card_image-wrapper, card_img и т.д. (верно - card__(element))Рекомендую дополнительно ознакомиться с БЭМ неймингом по ссылке - https://ru.bem.info/methodology/quick-start/**

- [ ] БЭМ файловая структура не содержит ошибок.

**Названия файлов должны соответствовать классам. В данном случае есть ошибки - файл about_title содержит только одно нижнее подчеркивание, в то время как хранит в себе верный класс about__title. Из-за прошлого пункта с ошибкой в неймингах - неверные названия файлов и классов card (card_title и т.д.). Более подробно про структуру файлов - https://ru.bem.info/methodology/filestructure/**

- [ ] Мета-элементы не содержат ошибок.

**Замечание - запрещен ресайз документа в мета-теге viewport, что выдаст предупреждение валидатором. Отсутствует контент в мета теге author**

- [ ] Проект адаптирован под различные разрешения экрана. Горизонтальный скролл не должен возникать на разрешениях от 320 пикселей и больше. Скрывать полосу прокрутки свойством `overflow: hidden` нельзя.

**Класс header-form имеет стиль min-width: 330px, из-за чего на экранах маленьких телефонов(320px) - возникает горизонтальный скролл. Рекомендуется написать дополнительный стиль для данного разрешения, либо использовать относительные величины (проценты, либо vw). Класс about содержит большие показатели padding, из-за чего текст так же выходит за границы экрана, а т.к. в правилах страницы не указан стиль box-sizing: border-box  -  секция выпадает из общего flow документа. Рекомендуется присвоить данный стиль, либо задать padding для вложенного контейнера, а так жеуменьшить шрифт текста в данном блоке. Подробнее про box-sizing можно прочитать тут - https://learn.javascript.ru/box-sizing. Для решения вышеперечисленных проблем используется класс scroll-lock для body со стилем overflow: hidden, что запрещено заданием.**

- [ ] Отзывчивая вёрстка, которая корректно тянется на всех промежуточных разрешениях.

**Блок с результатами поиска, а вернее карточки в нем - слишком сильно растянуты из-за текста по вертикали, я бы пересмотрел их раскладку в мобильном разрешении.**

- [ ] Корректно работают ссылки на внешние ресурсы: ни одна ссылка не ведёт в пустоту или на якорь, внешние ссылки открываются в новой вкладке.

**Ссылки на гитхаб и fb не работают**

- [ ] В коде используется семантическая разметка: применяются семантические теги, выбор элементов при вёрстке корректен (параграф должен быть параграфом, список — списком); структура DOM-дерева состоит не только из контейнеров div.

**Не используется тег nav для навигации в меню, не всегда используются списки с тегом ul, в хэдере используется div контейнер вместо формы, в результатах поиска картинки вставлены как div контейнеры, вместо тегов figure, picture и img. В футере использованы теги p вместо div или span.Отличная статься о семантической верстке - https://www.internetingishard.com/html-and-css/semantic-html/**

- [ ] Нету лишних DIV-оберток.

**Есть пустые контейнеры без классов.**

- [ ] Кнопки, инпуты и ссылки реализованы во всех состояниях

**Кнопка логина - не реализован фукнционал, нет тега button, нет состояний нажатия и наведения. Инпут поле запроса - нет состояния focus. Кнопка показать еще - нет эффекта наведения. Ссылки в футере и меню навигации - нет эффектов состояний**

- [ ] Элементы формы должны выделяться, когда на них установлен фокус.
- У формы должны быть:
    - [х] заданы плейсхолдеры;
    - [ ] валидированы обязательные поля.

**Форма поиска не является формой(обернута в div). Валидации нет.**

- [х] Шрифты подключены через @font-face.

- [ ] Для каждого шрифта указаны альтернативные варианты из системных шрифтов.

**Не указаны.Примеры с font-face - https://developer.mozilla.org/ru/docs/Web/CSS/@font-face**

- [ ] Для позиционирования элементов выбран верный подход, описанный корректным синтаксисом.

**Не всегда используется flex или grid, вместо этого используются отступы(margin). К примеру, в хэдере можно использовать grid со стилем gap.Хорошая статься о grid - https://css-tricks.com/snippets/css/complete-guide-grid/. Выучить grid в игровой форме - https://cssgridgarden.com/#ru**

- [ ] Для изображений задан атрибут alt с подходящий значением.

**img class="preloader__icon" src="<%= require('./images/not-found.svg')%>" alt="no" - в данном случае непонятное значение no**

- [ ] Каркас макета реализован на Flex-layout или Grid-layout;

**Не реализован**

- [ ] Растровые и векторные изображения оптимизированы;

**Изображения не конвертируются в webp/jpeg200. Отличная статья по оптимизации изображения для фронтедеров - https://evilmartians.com/chronicles/images-done-right-web-graphics-good-to-the-last-byte-optimization-techniques**

- [ ] Контентные и декоративные изображения выделены корректно

**Вставлены в div контейнер через backgroound в результатах поиска вместо img тега**

- [ ] Графика оптимизирована для мобильных и планшетных устройств

**В img тегах нет аттрибута srcset для соответсвующих разрешений**

## Доп. Комментарии:
