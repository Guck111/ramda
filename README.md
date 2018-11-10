Ramda
=============

Практическая функциональная библиотека для JavaScript программистов.

[![Build Status](https://travis-ci.org/ramda/ramda.svg?branch=master)](https://travis-ci.org/ramda/ramda)
[![npm module](https://badge.fury.io/js/ramda.svg)](https://www.npmjs.org/package/ramda)
[![dependencies](https://david-dm.org/ramda/ramda.svg)](https://david-dm.org/ramda/ramda)
[![Gitter](https://badges.gitter.im/Join_Chat.svg)](https://gitter.im/ramda/ramda?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)


Почему Ramda?
----------

<img src="http://ramda.jcphillipps.com/logo/ramdaFilled_200x235.png" 
     width="170" height="190" align="right" hspace="12" />

Уже есть несколько отличных библиотек с функциональным оттенком. Как правило, они предназначены для того, чтобы быть инструментами общего назначения, подходят для работы в нескольких парадигмах. У Ramda, в свою очередь, более конкретная цель. Мы хотели библиотеку, разработанную специально для программирования в функциональном стиле, библиотеку, с которой легко создавать функциональные источники информации, которая не изменяет данные пользователя.


В чем разница?
-----------------

Основные отличительные особенности Ramda:

* Ramda делает упор на чистый функциональный стиль. Неизменность (Immutable) данных и отсутствие побочных эффектов функций лежат в основе философии дизайна. Это помогает выполнять работу с помощью простого и элегантного кода.

* Ramda функции имеют автоматический карринг. Это позволяет легко строить новые функции из старых просто не передавая конечный параметр.

* Параметры в Ramda функциях расположены таким образом, чтобы сделать карринг как можно более удобным. Данные, которые должны быть обработанны, как правило, подаются в последнюю очередь.

Последние два пункта вместе, делают очень легким создание функций в виде последовательности простых функций, каждая из которых преобразует данные и передает их следующей. Ramda спроектирована для поддержки такого стиля написания кода.

Введение
-------------

* [Введение в Ramda](http://buzzdecafe.github.io/code/2014/05/16/introducing-ramda) by Buzz de Cafe
* [Почему Ramda?](http://fr.umio.us/why-ramda/) by Scott Sauyet [на русском языке](https://habr.com/post/349468/) 
* [Содействие каррингу](http://fr.umio.us/favoring-curry/) by Scott Sauyet
* [Почему карринг помогает](https://hughfdjackson.com/javascript/why-curry-helps/) by Hugh Jackson
* [Эй, Underscore, ты делаешь это неправильно!](https://www.youtube.com/watch?v=m3svKOdZijA&app=desktop) by Brian Lonsdorf
* [Думать в Ramda](http://randycoulman.com/blog/categories/thinking-in-ramda) by Randy Coulman [на русском языке](https://habr.com/post/348868/)


Философия
----------
Используя Ramda у вас должно появиться чувство как будто вы просто используете JavaScript. Это практичный, функциональный JavaScript. Мы не представляем лямбда выражения в строках, мы не заимствуем consed списки, мы не импортируем все функции с Clojure.

Наши базовые структуры данных - это простые JavaScript объекты, а наши обычные коллекции - это JavaScript массивы. Мы также сохраняем другие встроенные в JavaScript функции, такие как функции-объекты со свойствами.

Функциональное программирование в значительной степени связано с неизменными (immutable) объектами и Функциями без побочных эффектов. Хотя Ramda не применяет это, она позволяет использовать такой стиль с как можно меньшим "трением".

Мы стремимся к реализации как чистоты, так и элегантности кода, но АРI остается более важным. Частично мы приносим в жертву элегантность реализации ради более чистого АРI.

И последнее, но не менее важное: Ramda стремится к производительности. Надежная и быстрая реализация побеждают любые понятия функциональной чистоты.

Установка
---------

Для использования с node:

```bash
$ npm install ramda
```

Затем в консоли:

```javascript
const R = require('ramda');
```

Для прямого использования в браузере:

```html
<script src="path/to/yourCopyOf/ramda.js"></script>
```

или минифицированная версия:

```html
<script src="path/to/yourCopyOf/ramda.min.js"></script>
```

или с CDN, или cdnjs:

```html
<script src="//cdnjs.cloudflare.com/ajax/libs/ramda/0.25.0/ramda.min.js"></script>
```

или с помощью одной из ссылок приведенных ниже [jsDelivr](http://jsdelivr.com):

```html
<script src="//cdn.jsdelivr.net/npm/ramda@0.25.0/dist/ramda.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/ramda@0.25/dist/ramda.min.js"></script>
<script src="//cdn.jsdelivr.net/npm/ramda@latest/dist/ramda.min.js"></script>
```

(заметьте, что использование `latest` привносит огромный риск того, что при изменении Ramda API ваш код может сломаться.)

Эти теги script добавляют переменную `R` в глобальной области видимости браузера.

Или вы можете вставить Ramda в любой ничего не подозревающий сайт с помощью [bookmarklet](https://github.com/Guck111/ramda/blob/master/BOOKMARKLET.md).

**Замечания к версиям > 0.25**
Версии Rambda > 0.25 не имеют экспрота по умолчанию.
Поэтому вместо `import R from 'ramda';` нужно использовать `import * as R from 'ramda';`
А еще лучше, импортировать только необходимые функции через `import { functionName } from 'ramda';`

### Сборка

* на Unix-подобных платформах, `npm run build` обновляет __dist/ramda.js__ и __dist/ramda.min.js__
* на Windows, запишите результат `scripts / build --complete` до временного файла, после чего переименуйте временный файл на __dist / ramda.js__.
#### Частичная сборка

Возможно собрать Ramda с подмножеством функциональных возможностей ради уменьшения размера файла. Система сборки Ramda предоставляет эту возможность с помощью флажков в командной строке. Например, если вы используете `R.compose`, `R.reduce` и `R.filter`, вы можете создать частичную сборку с помощью следующей строки:

    ./scripts/build -- src/compose.js src/reduce.js src/filter.js > dist/ramda.custom.js

Для этого нужно иметь установленный Node/io.js. 

Документация
-------------
- Перевод API-документации [русский язык](https://github.com/Guck111/ramda/blob/master/DOCUMENTATION.md).
- Переклад API-документації [украинский язык](https://github.com/ivanzusko/ramda/blob/master/DOCUMENTATION.md).
- API Документация [английский язык](http://ramdajs.com/docs/).

Имя
--------

Хорошо, Итак, мы любим овец: ram:. Это все. Это короткое имя, никем пока не занято. Это с легкостью могло бы быть `eweda`, но тогда мы бы были вынуждены говорить _eweda lamb!_ (lamb - ягненок, прим.переводчика), а токого никто не хотел. Для тех, кто не является носителем английского языка, _lambs_ - это детеныш овцы, _ewes_ - это овца, а _rams_ - бараны. Поэтому, возможно, _ramda_-это повзрослевшая lambda... Но, наверное, нет.


Запуск тестов
----------------------

**Консоль:**

Для запуска тестов с консоли, вам необходимо установить `mocha`:

    npm install -g mocha

Тогда из корня вашего проекта вы можете просто вызвать

    mocha

Или если вы установили зависимости через:

    npm install

тогда вы можете запустить тесты (и получить вывод деталей в терминале) запустив команду:

    npm test

**Браузер:**

Вы можете использовать [testem](https://github.com/airportyh/testem) для тестирования в разных браузерах (и даже в "безголовых" браузерах), с мгновенной перезагрузкой. Установите __testem__ (`npm install -g testem`) и выполните `testem`. Откройте ссылку которую предоставит вам ваш браузер и вы увидите результаты в вашем терминале.

Если у вас установлен _PhantomJS_ , вы можете выполнить `testem -l phantomjs` для запуска тестов полностью в "безголовом" режиме.


Переводы
-----------------

- [Англійською(English)](https://github.com/ramda/ramda)
- [Китайською(中文)](http://ramda.cn/)
- [Украинский(Українська)](https://github.com/ivanzusko/ramda/)


Благодарности
-----------------

Спасибо [J. C. Phillipps](http://www.jcphillipps.com) за Ramda logo.
Ramda logo artwork &copy; 2014 J. C. Phillipps. Creative Commons Licensed 
[CC BY-NC-SA 3.0](http://creativecommons.org/licenses/by-nc-sa/3.0/).
