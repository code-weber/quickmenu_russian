# Быстрое меню
Новый перспективный стандарт мобильной навигации в Интернете, обеспечивающий непревзойденный пользовательский опыт. Все в пределах досягаемости большого пальца. Не нужно тянуться или использовать вторую руку, чтобы открыть меню гамбургеров.

<p align="center">
    <img src="readme-demo.gif" alt="Demo illustrating the Quick Menu in action." width="300px" height="auto">
</p>

## Содержимое
- [Основные особенности]((#Ключевые-особенности))
- [Живое демо](#Живая-демонстрация)
- [Установка](#Установка)
    - [Быстрый старт через CDN](#Быстрый-старт-через-CDN)
    - [NPM](#npm)
- [Использование](#Использование)
    - [JavaScript](#javascript)
    - [Примеры HTML](#Примеры-HTML)
    - [Класс `qm-only`](#the-qm-only-class)
    - [Настройки CSS](#Настройки-CSS)
    - [Настройки Sass](#Настройки-Sass)
- [Содействие](#contributing)
- [Задачи/планы на будущее](#to-do--future-plans)
- [Кредиты/Ссылки](#credits--references)

## Ключевые особенности
* Themeable с поддержкой как светлого, так и темного режима в зависимости от предпочтений устройства пользователя.
* Мобильная альбомная ориентация поддерживается и протестирована на моделях до Apple iPhone 12 Pro Max и Samsung Galaxy S20 Ultra.
* Совместимость с мобильными устройствами с непрямоугольными экранами, т. е. с вырезами и областями жестов.
* Формулировка и содержание меню настраиваются в HTML.
* Адаптивно для мобильных устройств, планшетов и компьютеров. Desktop отобразит базовую встроенную навигацию.
* SEO-дружественный. Нет необходимости дублировать навигационные ссылки для каждого типа устройства и отображения контента, управляемого исключительно с помощью CSS.
* Никаких зависимостей разработки, библиотек или предварительных условий не требуется.

## Живая демонстрация
Демонстрационную версию можно найти на странице <a href="https://quickmenu.org">quickmenu.org</a>.

Убедитесь, что вы используете мобильное устройство или планшет, чтобы опробовать Быстрое меню, в противном случае будет отображаться режим рабочего стола, который представляет собой встроенную навигацию.

## Установка
### Быстрый старт через CDN
Чтобы быстро и просто внедрить Quick Menu в ваш проект, мы можем использовать бесплатную CDN jsDelivr с открытым исходным кодом.

Возможности настройки сокращаются при использовании CDN, однако вы все равно должны иметь возможность вносить изменения, перезаписывая свойства стиля быстрого меню в своем собственном пользовательском CSS.

```html
<!-- Последний скомпилированный CSS. Размещается в <head> над другими таблицами стилей. -->
<link href="https://cdn.jsdelivr.net/npm/quickmenu@1.4.3/dist/css/quickmenu.min.css" rel="stylesheet" integrity="sha384-7j3v8L4HaBsl4ybaVZEFtSNd6Lvr11rU+wF3pKEPcGa6Ype0tgSDZmHh8ihbSee4" crossorigin="anonymous">

<!-- Последний скомпилированный JS. Размещается перед закрывающим тегом <body> над другими скриптами. -->
<script src="https://cdn.jsdelivr.net/npm/quickmenu@1.4.3/dist/js/quickmenu.min.js" integrity="sha384-J+7UVhxvYUPTb1N2qLj0dvniUcy8M1Ssxsic1xFI31naqNI4KlXP+r4D5eLVxhgg" crossorigin="anonymous"></script>
```

Мы рекомендуем размещать таблицу стилей перед любыми вашими собственными таблицами стилей, чтобы ваши настройки имели приоритет там, где это возможно. Точно так же необходимо поместить сценарий перед любым из ваших собственных сценариев.

### NPM
Быстрое меню можно установить как модуль Node.js в ваш проект с помощью NPM с помощью следующей команды:

npm install quickmenu

Используя сборщик модулей, такой как Webpack, импортируйте JavaScript быстрого меню в свой JS-файл (например, обычно `main.js` или `app.js`):

```javascript
import QuickMenu from "quickmenu";
```

Затем для полной настройки импортируйте предварительно скомпилированный Sass Quick Menu в файл `.scss`: (В зависимости от файловой структуры вашего проекта вам может потребоваться добавить `../` перед правилом импорта.)

```scss
@import "node_modules/quickmenu/src/scss/quickmenu";
```

Или, в качестве альтернативы, вы можете импортировать готовый к использованию скомпилированный css (через упаковщик, например, Webpack):

```javascript
import "quickmenu/dist/css/quickmenu.min.css";
```

## Использование
### JavaScript
```javascript
new QuickMenu(); // To initialise the Quick Menu.
```

### Примеры HTML
В адаптивном режиме для мобильных устройств и планшетов меню фиксируется в нижней части экрана в пределах досягаемости большого пальца. Для настольных компьютеров отображается обычное встроенное меню, поэтому вы должны разместить HTML-код там, где вы хотите разместить навигацию для посетителей настольных компьютеров.

#### Предельно минимальный
```html
<!-- Utmost Minimal -->
<nav class="quick-menu navigation">
    <ul>
        <li><a href="/">Home</a></li>
        <li><a href="/about">About</a></li>
        <li><a href="/work">Work</a></li>
        <li><a href="/contact">Contact</a></li>
    </ul>
</nav>
```

#### Минимум: переименование кнопки быстрого меню```html

<!-- Minimal: Renaming Quick Menu Button -->
<div class="quick-menu navigation">
    <div class="button">My Menu</div>
    <nav>
        <ul>
            <li><a href="/">Home</a></li>
            <li><a href="/about">About</a></li>
            <li><a href="/work">Work</a></li>
            <li><a href="/contact">Contact</a></li>
        </ul>
    </nav>
</div>
```

#### Минимум: переименование кнопки закрытия
```html
<!-- Minimal: Renaming Close Button -->
<div class="quick-menu navigation">
    <div class="menu">
        <nav>
            <ul>
                <li><a href="/">Home</a></li>
                <li><a href="/about">About</a></li>
                <li><a href="/work">Work</a></li>
                <li><a href="/contact">Contact</a></li>
            </ul>
        </nav>
        <div class="menu-close">Dismiss</div>
    </div>
</div>
```

#### Полноценный
```html
<!-- Full Fledged: including SVGs as icons (not supplied), menu heading content, customised wording on open and close buttons. -->
<div class="quick-menu navigation">
    <div class="button"><img src="/icons/bars.svg">My Menu</div>
    <div class="menu">
        <div class="menu-heading">
            <div class="qm-icon"><img src="/icons/compass.svg"></div>
            <span>My Menu</span>
            <p>Explore the contents of this site by jumping around using the following handy menu.</p>
        </div>
        <hr>
        <nav>
            <ul>
                <li><a href="/"><div class="qm-icon qm-only"><img src="/icons/home.svg"></div>Home</a></li>
                <li><a href="/about"><div class="qm-icon qm-only"><img src="/icons/about.svg"></div>About</a></li>
                <li><a href="/work"><div class="qm-icon qm-only"><img src="/icons/work.svg"></div>Work</a></li>
                <li><a href="/contact"><div class="qm-icon qm-only"><img src="/icons/contact.svg"></div>Contact</a></li>
            </ul>
        </nav>
        <div class="menu-close">Dismiss</div>
    </div>
</div>
```

##### Класс `.qm-icon`
Быстрое меню было разработано для того, чтобы вы могли использовать любую иконографию, установленную в меню, включая изображения/SVG, шрифты и т. д. Любой стиль значков должен быть применен с помощью вашего собственного пользовательского CSS. Однако мы ввели класс `qm-icon`, чтобы обеспечить минимальные стили и уменьшить вашу рабочую нагрузку.

Если вы используете значки FontAwesome, например, через элемент `<i>`, вы можете применить класс `.qm-icon` непосредственно к элементу. В противном случае вы можете обернуть свои значки в элемент `div` с классом `.qm-icon`.

### Класс `.qm-only`
В рамках ваших требований вам может потребоваться представить дополнительный контент или функции (например, такие как поле поиска) внутри быстрого меню. Вы можете встроить дополнительный контент в div `.menu` (как показано в примерах HTML «Минимальный: переименование кнопки закрытия» и «Полноценный» выше).

Чтобы убедиться, что дополнительный контент, который вы вставляете, появляется только внутри быстрого меню для мобильных устройств и планшетов и не присутствует на настольных компьютерах, вы можете добавить класс `qm-only` к элементам HTML.

### Настройки CSS
Быстрое меню было разработано таким образом, чтобы сбалансировать минимальные стили и предложить готовое решение, поэтому, даже если вы используете этот пакет через CDN, вы все равно можете настроить свойства стиля. Настроив таргетинг на определенные элементы в собственном пользовательском CSS, вы можете перезаписать значения по умолчанию.

Чтобы убедиться, что ваш пользовательский CSS имеет приоритет, поместите CSS быстрого меню перед (т.е. над) вашей собственной таблицей стилей в вашем HTML-документе. Использование`!important` должно быть ненужным при соблюдении этих правил, так как ни одно из них не применялось в CSS быстрого меню.

#### Селекторы
```css
.quick-menu.navigation .button { /* The 'Quick Menu' floating button */ }
.quick-menu.navigation .menu { /* The entire menu container */ }
.quick-menu.navigation .menu .menu-heading { /* The heading content (i.e. top part) within the menu from the 'Full Fledged' example */ }
.quick-menu.navigation .menu .menu-close { /* The close button */ }
.quick-menu.navigation .menu nav ul li { /* The container for a single navigation link */
    min-width: 100px; /* The width of a link. You may adjust this to a fixed value or a % to ensure all items are of equal width. */
}
.quick-menu.navigation .menu nav ul li a { /* The actual hyperlink. */ }
```

### Настройки Sass
Импортировав предварительно скомпилированные исходные файлы Sass в свой проект, вы можете воспользоваться дополнительными преимуществами настройки быстрого меню в соответствии со своими предпочтениями/требованиями. Однако все пользовательские и дополнительные стили должны быть включены в ваши собственные файлы SCSS, чтобы сохранить независимость пакета быстрого меню и гарантировать, что он может продолжать обновляться без конфликтов.

#### Переменные по умолчанию
Все переменные Sass быстрого меню определяются с помощью свойства `!default`, которое гарантирует, что если переменная не была объявлена в вашем пользовательском SCSS, то будет присвоено значение по умолчанию. Это позволяет вашим переменным иметь приоритет без необходимости изменять пакет быстрого меню.

Ваши переменные должны быть установлены перед импортом SCSS быстрого меню. Например:
```scss
// Your customisations
$backdrop-bg: rgba(255, 255, 255, 0.5);
$nav-item-width: 120px;

// Import Quick Menu SCSS
@import "node_modules/quickmenu/src/scss/quickmenu";
```

#### Доступные переменные
Чтобы просмотреть все переменные, доступные для вашей настройки, изучите файл «[src/scss/_variables.scss](https://github.com/aullah/quickmenu/blob/main/src/scss/_variables.scss)». файле.

Вы должны скопировать и вставить переменные, которые необходимо изменить, в свой собственный файл SCSS, соответствующим образом изменить значения, а затем удалить свойство `!default`.

#### Изменение точек останова устройства
Естественно по умолчанию для мобильных устройств появится мобильная версия Быстрого меню, поэтому нужно только определить точки останова для планшета и десктопа.

Следуя приведенной выше документации по изменению переменных, мы также можем изменять карты Sass (и, в нашем случае, точки останова устройства) в аналогичном порядке. Например:

```scss
// Ваши настройки
$menu-breakpoints: (
    tablet: 768px,
    desktop: 1200px
);

// Импорт быстрого меню SCSS
@import "node_modules/quickmenu/src/scss/quickmenu";
```


# Участие
Мы ценим ваш вклад в то, чтобы сделать этот проект лучше для всех нас. Пожалуйста, ознакомьтесь с нашим [Contributing Guide] (https://github.com/aullah/quickmenu/blob/main/CONTRIBUTING.md) для получения более подробной информации.

Во время участия в проекте Quick Menu мы придерживаемся [Code of Conduct](https://github.com/aullah/quickmenu/blob/main/CODE_OF_CONDUCT.md), которого мы требуем от всех.

## Задачи/Планы на будущее
* Предоставьте возможность переключать темы вручную.
* Реализовать возможность иметь подменю как для настольных, так и для мобильных устройств.



## Кредиты / ссылки
* Вдохновлено «Концепцией веб-навигации iPhone X» [Даниэля Корпаи через Medium] (https://medium.muz.li/iphone-x-web-navigation-concept-c06efc0e0c50) и [Dribble] (https://dribbble). .com/shots/3851367-iPhone-X-Web-Navigation-Idea).
* Исследование «The Thumb Zone: Designing For Mobile Users» [Саманта Ингрэм через Smashing Magazine] (https://www.smashingmagazine.com/2016/09/the-thumb-zone-designing-for-mobile-users/ ).
* Стандарты разработки модулей и документации взяты от [Alex MacArthur через TypeIt] (https://github.com/alexmacarthur/typeit) и [Bootstrap] (https://github.com/twbs/bootstrap).
* Окна просмотра мобильных и планшетных устройств взяты из [Полного руководства по разрешениям iPhone] (https://www.paintcodeapp.com/news/ultimate-guide-to-iphone-resolutions), ["iPhone 12 vs Designers" Михала Малевича. через Medium] (https://uxdesign.cc/iphone-12-vs-designers-ca8bac776dad) и [инструмент Viewport Sizer Tool] (https://viewportsizer.com/devices/).
