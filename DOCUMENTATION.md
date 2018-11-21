# Документация

[A](#a), [B](#b), [C](#c), [D](#d), [J](#j), [I](#i), [M](#m), [N](#n), [O](#o), [P](#p), [R](#r), [S](#s), [T](#t), [U](#u), [X](#x), [Z](#z)

## A
- [__](#__) `Function`
- [add](#add) `Math`
- [addIndex](#addindex) `Function`
- [adjust](#adjust) `List`
- [all](#all) `List`
- [allPass](#allpass) `Logic`
- [always](#always) `Function`
- [and](#and) `Logic`
- [any](#any) `List`
- [anyPass](#anypass) `List`
- [ap](#ap) `Function`
- [aperture](#aperture) `List`
- [append](#append) `List`
- [apply](#apply) `Function`
- [applySpec](#applyspec) `Function`
- [ascend](#ascend) `Function`
- [assoc](#assoc) `Object`
- [assocPath](#assocpath) `Object`

**[⬆ вверх](#Документация)**

## B
- [binary](#binary) `Function`
- [bind](#bind) `Function`
- [both](#both) `Logic`

**[⬆ вверх](#Документация)**

## C
- [call](#call) `Function`
- [chain](#chain) `List`
- [clamp](#clamp) `Relation`
- [clone](#clone) `Object`
- [comparator](#comparator) `Function`
- [compose](#compose) `Function`
- [composeK](#composeK) `Function`
- [composeP](#composeP) `Function`
- [concat](#concat) `List`
- [cond](#cond) `Logic`
- [construct](#construct) `Function`
- [constructN](#constructN) `Function`
- [contains](#contains) `List`
- [converge](#converge) `Function`
- [countBy](#countBy) `Relation`
- [curry](#curry) `Function`
- [curryN](#curryN) `Function`

**[⬆ вверх](#Документация)**

## D
- [dec](#dec) `Math`
- [defaultTo](#defaultto) `Logic`
- [descend](#descend) `Function`
- [difference](#difference) `Relation`
- [differenceWith](#differencewith) `Relation`
- [dissoc](#dissoc) `Object`
- [dissocPath](#dissocpath) `Object`
- [divide](#divide) `Math`
- [drop](#drop) `List`
- [dropLast](#droplast) `List`
- [dropLastWhile](#droplastwhile) `List`
- [dropRepeats](#droprepeats) `List`
- [dropRepeatsWith](#droprepeatswith) `List`
- [dropWhile](#dropwhile) `List`

**[⬆ вверх](#Документация)**

## E
- [either](#either) `Logic`
- [empty](#empty) `Function`
- [endsWith](#endsWith) `List`
- [eqBy](#eqBy) `Relation`
- [eqProps](#eqProps) `Object`
- [equals](#equals) `Relation`
- [evolve](#evolve) `Object`

## F.
- [F](#F) `Function`
- [filter](#filter) `List`
- [find](#find) `List`
- [findIndex](#findIndex) `List`
- [findLast](#findLast) `List`
- [findLastIndex](#findLastIndex) `List`
- [flatten](#flatten) `List`
- [flip](#flip) `Function`
- [forEach](#forEach) `List`
- [forEachObjIndexed](#forEachObjIndexed) `Object`
- [fromPairs](#fromPairs) `List`

## G
- [groupBy](#groupBy) `List`
- [groupWith](#groupWith) `List`
- [gt](#gt) `Relation`
- [gte](#gte) `Relation`

## J
- [juxt](#) ``

**[⬆ вверх](#Документация)**

## I
- [identity](#identity) `Function`
- [into](#into) `List`

**[⬆ вверх](#Документация)**

## M
- [map](#map) `List`

________

## __
### `[Function]`

_Добавлено в версии v0.6.0
 
Специальное значение для определения "пробелов" в каррированных функциях, которое позволяет частичное применение любой комбинации аргументов, в независимости от их позиций.

Если `g` - это каррированная тернарная функцмя и `_` является `R.__`, то следующее эквивалентное:

- `g(1, 2, 3)`
- `g(_, 2, 3)(1)`
- `g(_, _, 3)(1)(2)`
- `g(_, _, 3)(1, 2)`
- `g(_, 2, _)(1, 3)`
- `g(_, 2)(1)(3)`
- `g(_, 2)(1, 3)`
- `g(_, 2)(_, 3)(1)`

```javascript
var greet = R.replace('{name}', R.__, 'Hello, {name}!');
greet('Alice'); //=> 'Hello, Alice!'
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#?var%20greet%20%3D%20R.replace%28%27%7Bname%7D%27%2C%20R.__%2C%20%27Hello%2C%20%7Bname%7D%21%27%29%3B%0Agreet%28%27Alice%27%29%3B%20%2F%2F%3D%3E%20%27Hello%2C%20Alice%21%27)



## add
### `[Math]`

`Number → Number → Number`

#### Параметры:
||
:---|
| a |
| b |
| вернет __Number__ |

_Добавлено в версии v0.1.0_

Добавляет два значения

Смотрите также [subtract](#subtract).

```javascript
R.add(2, 3);       //=>  5
R.add(7)(10);      //=> 17
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#;R.add%282%2C%203%29%3B%20%20%20%20%20%20%20%2F%2F%3D%3E%20%205%0AR.add%287%29%2810%29%3B%20%20%20%20%20%20%2F%2F%3D%3E%2017)

**[⬆ вверх](#Документация)**



## addIndex
### `[Function]`

`((a … → b) … → [a] → *) → (a …, Int, [a] → b) … → [a] → *)`

#### Параметры:
|||
:---|:---|
| fn | Функция итерации списка, которая не передает индекс или список в функцию обратного вызова(callback) |
| вернет __function__ | Изменена функция итерации списка, которая не передает (элемент, индекс, список) в его функцию обратного вызова(callback) |

_Добавлено в версии v0.15.0_

Создает новую функцию итерации списка с уже существующей, с помощью добавления двух новых аргументов к функции обратного вызова: текущий индекс и весь список.

Это, в свою очередь, преобразует, например функцию `R.map` в функцию, которая больше напоминает `Array.prototype.map`. Обратите внимание на то, что это сработает только для функций, в которых итерирующая функция обратного вызова является первым аргументом, а список - последним. (Последнее может быть не важно, если аргумент списка не используется.)
```javascript
var mapIndexed = R.addIndex(R.map);
mapIndexed((val, idx) => idx + '-' + val, ['f', 'o', 'o', 'b', 'a', 'r']);
//=> ['0-f', '1-o', '2-o', '3-b', '4-a', '5-r']
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#;var%20mapIndexed%20%3D%20R.addIndex%28R.map%29%3B%0AmapIndexed%28%28val%2C%20idx%29%20%3D%3E%20idx%20%2B%20%27-%27%20%2B%20val%2C%20%5B%27f%27%2C%20%27o%27%2C%20%27o%27%2C%20%27b%27%2C%20%27a%27%2C%20%27r%27%5D%29%3B%0A%2F%2F%3D%3E%20%5B%270-f%27%2C%20%271-o%27%2C%20%272-o%27%2C%20%273-b%27%2C%20%274-a%27%2C%20%275-r%27%5D)

**[⬆ вверх](#Документация)**



## adjust
### `[List]`

`(a → a) → Number → [a] → [a]`

#### Параметры:
|||
:---|:---|
| fn | Функция которая будет применена |
| idx | Индекс |
| list | Массиво-подобный объект, чье значение будет заменено в указанном индексом месте. |
| вернет __Array__ | Копию передаваемого массиво-подобного объекта, с элементом (на месте согласно индексу `idx`) замененным значением которое вернулось после применения функции ' fn ' к существующему элементу. |

_Добавлено в версии v0.14.0_

Применяет функцию к указанному индексом элемента в массиве, возвращая новую копию массива с элементом, на указанном индксом месте, замененным результатом примененной функции.

Смотрите также [update](#update).

```javascript
R.adjust(R.add(10), 1, [1, 2, 3]);     //=> [1, 12, 3]
R.adjust(R.add(10))(1)([1, 2, 3]);     //=> [1, 12, 3]
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#?R.adjust%28R.add%2810%29%2C%201%2C%20%5B1%2C%202%2C%203%5D%29%3B%20%20%20%20%20%2F%2F%3D%3E%20%5B1%2C%2012%2C%203%5D%0AR.adjust%28R.add%2810%29%29%281%29%28%5B1%2C%202%2C%203%5D%29%3B%20%20%20%20%20%2F%2F%3D%3E%20%5B1%2C%2012%2C%203%5D)

**[⬆ вверх](#Документация)**



## all
### `[List]`

`(a → Boolean) → [a] → Boolean`

#### Параметры:
|||
:---|:---|
| fn | Функция предикат |
| list | Массив, который должен быть оценен. |
| вернет __Boolean__ | `true`, если предикат удовлетворен каждым из элементов, в противном случае вернется `false`. |

_Добавлено в версии v0.1.0_

Вернет `true`, если все элементы списка соответствуют предикату, `false`, если в списке нет ни одного который бы отвечал.

Применяет ко всем метод второго аргумента, если он присутствует.

Действует как преобразователь (трансдюсер), если трансформер указан на месте списка.

Смотрите также [any](#any), [none](#none), [transduce](#transduce).

```javascript
var equals3 = R.equals(3);
R.all(equals3)([3, 3, 3, 3]); //=> true
R.all(equals3)([3, 3, 1, 3]); //=> false
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#?var%20equals3%20%3D%20R.equals%283%29%3B%0AR.all%28equals3%29%28%5B3%2C%203%2C%203%2C%203%5D%29%3B%20%2F%2F%3D%3E%20true%0AR.all%28equals3%29%28%5B3%2C%203%2C%201%2C%203%5D%29%3B%20%2F%2F%3D%3E%20false)

**[⬆ вверх](#Документация)**



## allPass
### `[Logic]`

`[(*… → Boolean)] → (*… → Boolean)`

#### Параметры:
|||
:---|:---|
| predicates | массив предикатов, которые необходимо проверить |
| вернет: __function__ | объединенный предикат |

_Добавлено в версии v0.9.0_

Принимает список предикатов и вернет предикат, который вернет `true` для заданного списка аргументов, если каждый из переданных предикатов удовлетворен теми аргументами.

Возвращенная функция является каррированной, чья арность совпадает с арностью предиката с высочайшей арностью.

Смотрите также [anyPass](#anypass)

```javascript
var isQueen = R.propEq('rank', 'Q');
var isSpade = R.propEq('suit', '♠︎');
var isQueenOfSpades = R.allPass([isQueen, isSpade]);

isQueenOfSpades({rank: 'Q', suit: '♣︎'}); //=> false
isQueenOfSpades({rank: 'Q', suit: '♠︎'}); //=> true
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#;var%20isQueen%20%3D%20R.propEq%28%27rank%27%2C%20%27Q%27%29%3B%0Avar%20isSpade%20%3D%20R.propEq%28%27suit%27%2C%20%27%E2%99%A0%EF%B8%8E%27%29%3B%0Avar%20isQueenOfSpades%20%3D%20R.allPass%28%5BisQueen%2C%20isSpade%5D%29%3B%0A%0AisQueenOfSpades%28%7Brank%3A%20%27Q%27%2C%20suit%3A%20%27%E2%99%A3%EF%B8%8E%27%7D%29%3B%20%2F%2F%3D%3E%20false%0AisQueenOfSpades%28%7Brank%3A%20%27Q%27%2C%20suit%3A%20%27%E2%99%A0%EF%B8%8E%27%7D%29%3B%20%2F%2F%3D%3E%20true)

**[⬆ вверх](#Документация)**



## always
### `[Function]`

`a → (* → a)`

#### Параметры:
|||
:---|:---|
| val | Значение, которое необходимо обернуть в функцию |
| вернет __function__ | функция :: * -> val. |

_Добавлено в версии v0.1.0_

Возвращает функцию, которая всегда возвращает заданное значение. Обратите внимание, что для непримитивов возвращаемое значение является ссылкой на исходное значение.

Эта функция известна как `const`, `constant` или `K` (для K combinator) в других языках и библиотеках.

```javascript
var t = R.always('Tee');
t(); //=> 'Tee'
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#?var%20t%20%3D%20R.always%28%27Tee%27%29%3B%0At%28%29%3B%20%2F%2F%3D%3E%20%27Tee%27)

**[⬆ вверх](#Документация)**



## and
### `[Logic]`

`a → b → a | b`

#### Параметры:
| | |
:---|:---|
| a |
| b |
| вернет __Any__ | первый аргумент, если он имеет значение `false`, в противном случае второй аргумент. |

_Добавлено в версии v0.1.0_

Возвращает `true`, если оба аргумента истинны, в противном случае - `false`.

Смотрите также [both](#both).

```javascript
R.and(true, true); //=> true
R.and(true, false); //=> false
R.and(false, true); //=> false
R.and(false, false); //=> false
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#;R.and%28true%2C%20true%29%3B%20%2F%2F%3D%3E%20true%0AR.and%28true%2C%20false%29%3B%20%2F%2F%3D%3E%20false%0AR.and%28false%2C%20true%29%3B%20%2F%2F%3D%3E%20false%0AR.and%28false%2C%20false%29%3B%20%2F%2F%3D%3E%20false)

**[⬆ вверх](#Документация)**



## any
### `[List]`

`(a → Boolean) → [a] → Boolean`

#### Параметры:
|||
:---|:---|
| fn | Функция предикат |
| list | Массив который должен быть оценен. |
| вернет __Boolean__ | `true` , если предикат удовлетворен хотя бы одним элементом, `false` в противном случае. |

_Добавлено в версии v0.1.0_

Возвращает `true`, если хотя бы один из элементов списка соответствует предикату, иначе `false`.

Применяется к любому методу второго аргумента, если он присутствует.

Действует как преобразователь (трансдюсер), если трансформер указан на месте списка.

Смотрите также [all](#all), [none](#none), [transduce](#transduce).

```javascript
var lessThan0 = R.flip(R.lt)(0);
var lessThan2 = R.flip(R.lt)(2);
R.any(lessThan0)([1, 2]); //=> false
R.any(lessThan2)([1, 2]); //=> true
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#;var%20lessThan0%20%3D%20R.flip%28R.lt%29%280%29%3B%0Avar%20lessThan2%20%3D%20R.flip%28R.lt%29%282%29%3B%0AR.any%28lessThan0%29%28%5B1%2C%202%5D%29%3B%20%2F%2F%3D%3E%20false%0AR.any%28lessThan2%29%28%5B1%2C%202%5D%29%3B%20%2F%2F%3D%3E%20true)

**[⬆ вверх](#Документация)**



## anyPass
### `[Logic]`

`[(*… → Boolean)] → (*… → Boolean)`

#### Параметры:
|||
:---|:---|
| predicates | массив предикатов, которые необходимо проверить |
| вернет __function__ | объединенный предикат |

_Добавлено в версии v0.9.0_

Принимает список предикатов и вернет предикат, который вернет `true` для заданного списка аргументов, если хотя бы один из переданных предикатов удовлетворен теми аргументами.

Возвращенная Функция является каррированной, чья арность совпадает с арностью предиката с высочайшей арностью.

Смотрите также [allPass](#allpass)

```javascript
var isClub = R.propEq('suit', '♣');
var isSpade = R.propEq('suit', '♠');
var isBlackCard = R.anyPass([isClub, isSpade]);

isBlackCard({rank: '10', suit: '♣'}); //=> true
isBlackCard({rank: 'Q', suit: '♠'}); //=> true
isBlackCard({rank: 'Q', suit: '♦'}); //=> false
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#?var%20isClub%20%3D%20R.propEq%28%27suit%27%2C%20%27%E2%99%A3%27%29%3B%0Avar%20isSpade%20%3D%20R.propEq%28%27suit%27%2C%20%27%E2%99%A0%27%29%3B%0Avar%20isBlackCard%20%3D%20R.anyPass%28%5BisClub%2C%20isSpade%5D%29%3B%0A%0AisBlackCard%28%7Brank%3A%20%2710%27%2C%20suit%3A%20%27%E2%99%A3%27%7D%29%3B%20%2F%2F%3D%3E%20true%0AisBlackCard%28%7Brank%3A%20%27Q%27%2C%20suit%3A%20%27%E2%99%A0%27%7D%29%3B%20%2F%2F%3D%3E%20true%0AisBlackCard%28%7Brank%3A%20%27Q%27%2C%20suit%3A%20%27%E2%99%A6%27%7D%29%3B%20%2F%2F%3D%3E%20false)

**[⬆ вверх](#Документация)**



## ap
### `[Function]`

`[a → b] → [a] → [b]`

`Apply f => f (a → b) → f a → f b`

#### Параметры:
||
:---|
| applyF |
| applyX |
| вернет __*__ |

_Добавлено в версии v0.3.0_

`ap` применяет список функций к списку значений.

Передает метод `ap` второго аргумента, если тот присутствует. Также воспринимает каррированные функции как аппликативы.

```javascript
R.ap([R.multiply(2), R.add(3)], [1,2,3]); //=> [2, 4, 6, 4, 5, 6]
R.ap([R.concat('tasty '), R.toUpper], ['pizza', 'salad']); //=> ["tasty pizza", "tasty salad", "PIZZA", "SALAD"]
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#;R.ap%28%5BR.multiply%282%29%2C%20R.add%283%29%5D%2C%20%5B1%2C2%2C3%5D%29%3B%20%2F%2F%3D%3E%20%5B2%2C%204%2C%206%2C%204%2C%205%2C%206%5D%0AR.ap%28%5BR.concat%28%27tasty%20%27%29%2C%20R.toUpper%5D%2C%20%5B%27pizza%27%2C%20%27salad%27%5D%29%3B%20%2F%2F%3D%3E%20%5B%22tasty%20pizza%22%2C%20%22tasty%20salad%22%2C%20%22PIZZA%22%2C%20%22SALAD%22%5D)

**[⬆ вверх](#Документация)**



## aperture
### `[List]`

`Number → [a] → [[a]]`

#### Параметры:
|||
:---|:---|
| n | Какого размера должны быть созданы массивы. |
| list | Список, который нужно разбить на массивы с `n`-длиной. |
| вернет __Array__ | Финальный список массивов, каждый с длиной `n`. |

_Добавлено в версии v0.12.0_

вернет новый список, составленный из массивов, каждый с длиной `n` последовательных элементов. Если `n` больше чем длина списка-вернется пустой список.

Действует как преобразователь(transducer), если трансформер(transformer) передан на месте списка.

Смотрите также [transduce](#transduce).

```javascript
R.aperture(2, [1, 2, 3, 4, 5]); //=> [[1, 2], [2, 3], [3, 4], [4, 5]]
R.aperture(3, [1, 2, 3, 4, 5]); //=> [[1, 2, 3], [2, 3, 4], [3, 4, 5]]
R.aperture(7, [1, 2, 3, 4, 5]); //=> []
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#;R.aperture%282%2C%20%5B1%2C%202%2C%203%2C%204%2C%205%5D%29%3B%20%2F%2F%3D%3E%20%5B%5B1%2C%202%5D%2C%20%5B2%2C%203%5D%2C%20%5B3%2C%204%5D%2C%20%5B4%2C%205%5D%5D%0AR.aperture%283%2C%20%5B1%2C%202%2C%203%2C%204%2C%205%5D%29%3B%20%2F%2F%3D%3E%20%5B%5B1%2C%202%2C%203%5D%2C%20%5B2%2C%203%2C%204%5D%2C%20%5B3%2C%204%2C%205%5D%5D%0AR.aperture%287%2C%20%5B1%2C%202%2C%203%2C%204%2C%205%5D%29%3B%20%2F%2F%3D%3E%20%5B%5D)

**[⬆ вверх](#Документация)**



## append
### `[List]`

`a → [a] → [a]`

#### Параметры:
|||
:---|:---|
| el | Элемент, который нужно добавить в конц списка. |
| list | Список элементов к которому следует добавить элемент. |
| вернет __Array__ | Новый массив, включающий в себя элементы старого списка и в конце добавлен элемент `el`. |

_Добавлено в версии v0.1.0_

вернет новый список, в котором находятся элементы переданные в качестве параметра `list`, и в конце элемент переданный в качестве аргумента `el`.

Смотрите также [prepend](#prepend).

```javascript
R.append('tests', ['write', 'more']); //=> ['write', 'more', 'tests']
R.append('tests', []); //=> ['tests']
R.append(['tests'], ['write', 'more']); //=> ['write', 'more', ['tests']]
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#;R.append%28%27tests%27%2C%20%5B%27write%27%2C%20%27more%27%5D%29%3B%20%2F%2F%3D%3E%20%5B%27write%27%2C%20%27more%27%2C%20%27tests%27%5D%0AR.append%28%27tests%27%2C%20%5B%5D%29%3B%20%2F%2F%3D%3E%20%5B%27tests%27%5D%0AR.append%28%5B%27tests%27%5D%2C%20%5B%27write%27%2C%20%27more%27%5D%29%3B%20%2F%2F%3D%3E%20%5B%27write%27%2C%20%27more%27%2C%20%5B%27tests%27%5D%5D)

**[⬆ вверх](#Документация)**



## apply
### `[Function]`

`(*… → a) → [*] → a`

#### Параметры:
|||
:---|:---|
| fn | Функция, которая будет вызвана с аргументами `args` |
| args | Аргументы, с которыми должна быть вызвана Функция `fn`. |
| вернет __*__ результат | Результат, равный `fn(...args)` |

_Добавлено в версии v0.7.0_

Применяет функцию `fn` к списку аргументов `args`. Это полезно для создания функций фиксированной арности из функции с переменным числом аргументов. `fn` должна быть привязанной (bind) функцией, в случае если контекст важен.

Смотрите также [call](#call), [unapply](#unapply).

```javascript
var nums = [1, 2, 3, -99, 42, 6, 7];
R.apply(Math.max, nums); //=> 42
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#;var%20nums%20%3D%20%5B1%2C%202%2C%203%2C%20-99%2C%2042%2C%206%2C%207%5D%3B%0AR.apply%28Math.max%2C%20nums%29%3B%20%2F%2F%3D%3E%2042)

**[⬆ вверх](#Документация)**



## applySpec
### `[Function]`

`{k: ((a, b, …, m) → v)} → ((a, b, …, m) → {k: v})`

#### Параметры:
|||
:---|:---|
| spec | Объект рекурсивно сопоставляет свойства с аргументами функции для получения значений этих свойств.|
| вернет __function__ | Функция, которая вернет объект с такой же структурой как и объект `spec`, с каждым свойством установленным в значение, которое было возвращено вызовом связанной функции с передаваемыми аргументами. |
_Добавлено в версии v0.20.0_

Учитывая, что объект `spec` рекурсивно сопоставляет свойства функции, создается Функция, которая создает объект с такой же структурой, путем сопоставления каждого свойства с результатом вызова связанной с ним функции с передаваемыми аргументами.

Смотрите также [converge](#converge), [juxt](#juxt).

```javascript
var getMetrics = R.applySpec({
                                sum: R.add,
                                nested: { mul: R.multiply }
                             });
getMetrics(2, 4); // => { sum: 6, nested: { mul: 8 } }
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#?var%20getMetrics%20%3D%20R.applySpec%28%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20sum%3A%20R.add%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20nested%3A%20%7B%20mul%3A%20R.multiply%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%29%3B%0AgetMetrics%282%2C%204%29%3B%20%2F%2F%20%3D%3E%20%7B%20sum%3A%206%2C%20nested%3A%20%7B%20mul%3A%208%20%7D%20%7D)

**[⬆ вверх](#Документация)**



## ascend
### `[Function]`

`Ord b => (a → b) → a → a → Number`

#### Параметры:
|||
:---|:---|
| fn | Функция арностью один, которая вернет значение, которое можно сравнить. |
| a | Первый элемент для сравнения. |
| b | Второй элемент для сравнения. |
| вернет __Number__ | `-1` если `fn(a) < fn(b)`, `1` - если `fn(b) < fn(a)`, иначе `0` |

_Добавлено в версии v0.23.0_

Создает восходящую функцию сравнения, которая вернет значение которое может быть сравнимо с помощью `<` и `>`.

Смотрите также [descend](#descend).

```javascript
var byAge = R.ascend(R.prop('age'));
var people = [
  // ...
];
var peopleByYoungestFirst = R.sort(byAge, people);
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#?var%20byAge%20%3D%20R.ascend%28R.prop%28%27age%27%29%29%3B%0Avar%20people%20%3D%20%5B%0A%20%20%2F%2F%20...%0A%5D%3B%0Avar%20peopleByYoungestFirst%20%3D%20R.sort%28byAge%2C%20people%29%3B)

**[⬆ вверх](#Документация)**



## assoc
### `[Object]`

`String → a → {k: v} → {k: v}`

#### Параметры:
|||
:---|:---|
| prop | Имя свойства, которое должно быть задано. |
| val | Новое значение |
| obj | Объект который должен быть скопирован. |
| вернет __Object__ | новый объект, эквивалентный исходному, за исключением измененного свойства. |

_Добавлено в версии v0.8.0_

Создает поверхностную копию объекта, устанавливая или переопределяя указанное свойство заданным значением. Обратите внимание, что это создаст новый объект. Все свойства, не являющиеся примитивами, копируются по ссылке.
Смотрите также [dissoc](#dissoc).

```javascript
R.assoc('c', 3, {a: 1, b: 2}); //=> {a: 1, b: 2, c: 3}
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#;R.assoc%28%27c%27%2C%203%2C%20%7Ba%3A%201%2C%20b%3A%202%7D%29%3B%20%2F%2F%3D%3E%20%7Ba%3A%201%2C%20b%3A%202%2C%20c%3A%203%7D)

**[⬆ вверх](#Документация)**



## assocPath
### `[Object]`

`[Idx] → a → {a} → {a}`
`Idx = String | Int`

#### Параметры:
|||
:---|:---|
| path | путь который надо задать. |
| val | Новое значение |
| obj | Объект который должен быть скопирован. |
| вернет __Object__ | Новый объект, эквивалентный оригинальному, за исключением указанного пути. |

_Добавлено в версии v0.8.0_

Создает поверхностную копию объекта, устанавливая или перезаписывая узлы, которые необходимы для создания указанного пути и вставляя указанное значение в конце того пути. __Обратите внимание__, что он так же копирует и приравнивает значения прототипов к новому объекту. Все значения не являющиеся примитивами копируются по ссылке.
Смотрите также [dissocPath](#dissocPath).

```javascript
R.assocPath(['a', 'b', 'c'], 42, {a: {b: {c: 0}}}); //=> {a: {b: {c: 42}}}

// Любые отсутствующие или не объектные ключи в path будут переопределены
R.assocPath(['a', 'b', 'c'], 42, {a: 5}); //=> {a: {b: {c: 42}}}
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#;R.assocPath%28%5B%27a%27%2C%20%27b%27%2C%20%27c%27%5D%2C%2042%2C%20%7Ba%3A%20%7Bb%3A%20%7Bc%3A%200%7D%7D%7D%29%3B%20%2F%2F%3D%3E%20%7Ba%3A%20%7Bb%3A%20%7Bc%3A%2042%7D%7D%7D%0A%0A%2F%2F%20Any%20missing%20or%20non-object%20keys%20in%20path%20will%20be%20overridden%0AR.assocPath%28%5B%27a%27%2C%20%27b%27%2C%20%27c%27%5D%2C%2042%2C%20%7Ba%3A%205%7D%29%3B%20%2F%2F%3D%3E%20%7Ba%3A%20%7Bb%3A%20%7Bc%3A%2042%7D%7D%7D)

**[⬆ вверх](#Документация)**



## binary
### `[Function]`

`(* → c) → (a, b → c)`

#### Параметры:
|||
:---|:---|
| fn | Функция, которую необходимо обернуть. |
| вернет __function__ | Новая Функция, которая оборачивает функцию `fn`. Новая Функция гарантированно имеет арность 2. |

_Добавлено в версии v0.2.0_

Оборачивает функцию любой арности (включая нулевую) в функцию, которая принимает в себя 2 аргумента. Ни один из избыточных аргументов не будет передан в обернутую функцию.

Смотрите также [nAry](#nary), [unary](#unary).

```javascript
var takesThreeArgs = function(a, b, c) {
  return [a, b, c];
};
takesThreeArgs.length; //=> 3
takesThreeArgs(1, 2, 3); //=> [1, 2, 3]

var takesTwoArgs = R.binary(takesThreeArgs);
takesTwoArgs.length; //=> 2
// В обернутую функцию передается только 2 аргумента
takesTwoArgs(1, 2, 3); //=> [1, 2, undefined]
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#;var takesThreeArgs %3D function(a%2C b%2C c) {%0A return [a%2C b%2C c]%3B%0A}%3B%0AtakesThreeArgs.length%3B %2F%2F%3D> 3%0AtakesThreeArgs(1%2C 2%2C 3)%3B %2F%2F%3D> [1%2C 2%2C 3]%0A%0Avar takesTwoArgs %3D R.binary(takesThreeArgs)%3B%0AtakesTwoArgs.length%3B %2F%2F%3D> 2%0A%2F%2F Only 2 arguments are passed to the wrapped function%0AtakesTwoArgs(1%2C 2%2C 3)%3B %2F%2F%3D> [1%2C 2%2C undefined])

**[⬆ вверх](#Документация)**



## bind
### `[Function]`

`(* → *) → {*} → (* → *)`

#### Параметры:
|||
:---|:---|
| fn | Функция, которую необходимо привязать к контексту. |
| thisObj | Контекст, к которому привязывается Функция `fn` |
| вернет __function__ | Функция, которая будет выполнена в контексте `thisObj`. |

_Добавлено в версии v0.6.0_

Создает функцию привязанную к контесту. __Примечание:__ `R.bind` не предоставляет дополнительные возможности привязки аргументов `Function.prototype.bind`.

Смотрите также [partial](#partial).

```javascript
var log = R.bind(console.log, console);
R.pipe(R.assoc('a', 2), R.tap(log), R.assoc('a', 3))({a: 1}); //=> {a: 3}
// logs {a: 2}
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#?var%20log%20%3D%20R.bind%28console.log%2C%20console%29%3B%0AR.pipe%28R.assoc%28%27a%27%2C%202%29%2C%20R.tap%28log%29%2C%20R.assoc%28%27a%27%2C%203%29%29%28%7Ba%3A%201%7D%29%3B%20%2F%2F%3D%3E%20%7Ba%3A%203%7D%0A%2F%2F%20logs%20%7Ba%3A%202%7D)

**[⬆ вверх](#Документация)**



## both
### `[Logic]`

`(*… → Boolean) → (*… → Boolean) → (*… → Boolean)`

#### Параметры:
|||
:---|:---|
| f | Предикат |
| g | Другой предикат |
| вернет __function__ | Функция, вызывает `f` и `g` и возвращает `&&` их результатов. |

_Добавлено в версии v0.12.0_

Функция, которая вызывает две передаваемых в нее функции и возвращает `&&` результата. Это вернет результат первой функции, если она `false`, а иначе вернет вторую функцию. __Примечание__, вторая Функция не будет вызвана, если первая вернет значение `false`.

В дополнение к функциям, `R.both` также принимает любые совместимые с `fantasy-land` аппликативные функторы.

Смотрите также [and](#and).

```javascript
var gt10 = R.gt(R.__, 10)
var lt20 = R.lt(R.__, 20)
var f = R.both(gt10, lt20);
f(15); //=> true
f(30); //=> false
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#;var%20gt10%20%3D%20R.gt%28R.__%2C%2010%29%0Avar%20lt20%20%3D%20R.lt%28R.__%2C%2020%29%0Avar%20f%20%3D%20R.both%28gt10%2C%20lt20%29%3B%0Af%2815%29%3B%20%2F%2F%3D%3E%20true%0Af%2830%29%3B%20%2F%2F%3D%3E%20false)

**[⬆ вверх](#Документация)**



## call
### `[Function]`

`(*… → a),*… → a`

#### Параметры:
|||
:---|:---|
| fn | Функция, которую нужно применить к оставшимся аргументам. |
| args | Любое количество позиционных аргументов. |
| вернет __*__ |   |

_Добавлено в версии v0.9.0_

вернет результат вызова первого аргумента и оставшиеся аргументы. Иногда это полезно в качестве конверсионной функции для `R.converge`: первая ветка может образовать функцию, в то время как остальные ветви образуют значения, которые будут переданы в ту образованную функцию в качестве аргументов.
Смотрите также [apply](#apply).

```javascript
R.call(R.add, 1, 2); //=> 3

var indentN = R.pipe(R.times(R.always(' ')),
                     R.join(''),
                     R.replace(/^(?!$)/gm));

var format = R.converge(R.call, [
                            R.pipe(R.prop('indent'), indentN),
                            R.prop('value')
                        ]);

format({indent: 2, value: 'foo\nbar\nbaz\n'}); //=> '  foo\n  bar\n  baz\n'
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#?R.call%28R.add%2C%201%2C%202%29%3B%20%2F%2F%3D%3E%203%0A%0Avar%20indentN%20%3D%20R.pipe%28R.times%28R.always%28%27%20%27%29%29%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20R.join%28%27%27%29%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20R.replace%28%2F%5E%28%3F%21%24%29%2Fgm%29%29%3B%0A%0Avar%20format%20%3D%20R.converge%28R.call%2C%20%5B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20R.pipe%28R.prop%28%27indent%27%29%2C%20indentN%29%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20R.prop%28%27value%27%29%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%5D%29%3B%0A%0Aformat%28%7Bindent%3A%202%2C%20value%3A%20%27foo%5Cnbar%5Cnbaz%5Cn%27%7D%29%3B%20%2F%2F%3D%3E%20%27%20%20foo%5Cn%20%20bar%5Cn%20%20baz%5Cn%27)

**[⬆ вверх](#Документация)**



## chain
### `[List]`

`Chain m => (a → m b) → m a → m b`

#### Параметры:
|||
:---|:---|
| fn | Функция, с которой надо совместить. |
| list | Список для отображения. |
| вернет __Array__ | Результат плоского отображения списка `list` с функцией `fn`. |

_Добавлено в версии v0.3.0_

`chain` применяет функцию к списку и объединяет результаты. `chain` также известен в некоторых библиотеках как `flatMap`.

Выполняется метод `chain` второго аргумента(если он имеется), согласно [FantasyLand Chain спецификации](https://github.com/fantasyland/fantasy-land#chain).

Смотрите также [apply](#apply).

```javascript
var duplicate = n => [n, n];
R.chain(duplicate, [1, 2, 3]); //=> [1, 1, 2, 2, 3, 3]

R.chain(R.append, R.head)([1, 2, 3]); //=> [1, 2, 3, 1]
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#;var%20duplicate%20%3D%20n%20%3D%3E%20%5Bn%2C%20n%5D%3B%0AR.chain%28duplicate%2C%20%5B1%2C%202%2C%203%5D%29%3B%20%2F%2F%3D%3E%20%5B1%2C%201%2C%202%2C%202%2C%203%2C%203%5D%0A%0AR.chain%28R.append%2C%20R.head%29%28%5B1%2C%202%2C%203%5D%29%3B%20%2F%2F%3D%3E%20%5B1%2C%202%2C%203%2C%201%5D)

**[⬆ вверх](#Документация)**



## clamp
### `[Relation]`

`Ord a => a → a → a → a`

#### Параметры:
|||
:---|:---|
| minimum | Нижний предел диапазона (включительно) |
| maximum | Верхний предел диапазона (включительно) |
| value | Значение для закрепления в диапазоне |
| вернет __Number__ | вернет `minimum`, когда значение меньше минимума(`value < minimum`), `maximum`, когда значение больше максимум(`value > maximum`), во всех других случаях вернет именно значение(`value`) |

Добавлено в версии __v0.20.0__

Ограничивает число вне диапазона.

Также работает для других упорядоченных типов, таких как сроки (_Strings_) и даты (_Dates_)

```javascript
R.clamp(1, 10, -5) // => 1
R.clamp(1, 10, 15) // => 10
R.clamp(1, 10, 4)  // => 4
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#?R.clamp%281%2C%2010%2C%20-5%29%20%2F%2F%20%3D%3E%201%0AR.clamp%281%2C%2010%2C%2015%29%20%2F%2F%20%3D%3E%2010%0AR.clamp%281%2C%2010%2C%204%29%20%20%2F%2F%20%3D%3E%204)

**[⬆ вверх](#Документация)**



## clone
### `[Object]`

`{*} → {*}`

#### Параметры:
|||
:---|:---|
| value | Объект или массив, который нужно клонировать |
| вернет __*__ | Глубокую копию передаваемого объекта / массива (`val`) |

Добавлено в версии __v0.1.0__

Создает глубокую копию `value`, которое может содержать (вложенный) массивы (`Array`), объекты (`Object`), числа (`Number`), строки (`String`), булевые значения (`Boolean`) и даты (`Date`). Функции назначаются по ссылке, а не копируются.

Передает в метод `clone`, если тот присутствует.

```javascript
var objects = [{}, {}, {}];
var objectsClone = R.clone(objects);
objects === objectsClone; //=> false
objects[0] === objectsClone[0]; //=> false
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#?var%20objects%20%3D%20%5B%7B%7D%2C%20%7B%7D%2C%20%7B%7D%5D%3B%0Avar%20objectsClone%20%3D%20R.clone%28objects%29%3B%0Aobjects%20%3D%3D%3D%20objectsClone%3B%20%2F%2F%3D%3E%20false%0Aobjects%5B0%5D%20%3D%3D%3D%20objectsClone%5B0%5D%3B%20%2F%2F%3D%3E%20false)

**[⬆ вверх](#Документация)**


## comparator
### `[Function]`

`((a, b) → Boolean) → ((a, b) → Number)`

#### Параметры:
|||
:---|:---|
| pred | Функция предикат второго уровня, которая возвращает true, если первый аргумент меньше второго, иначе false |
| вернет __Function__ | Функция:: `a - > b - > Int`, которая возвращает `-1` Если `a < b`, `1` Если `b < a`, в противном случае `0` |

Добавлено в версии __v0.1.0__

Создает функцию сравнения, которая сообщает, является ли первый элемент меньше второго.

```javascript
var byAge = R.comparator((a, b) => a.age < b.age);
var people = [
  // ...
];
var peopleByIncreasingAge = R.sort(byAge, people);
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;var%20byAge%20%3D%20R.comparator%28%28a%2C%20b%29%20%3D%3E%20a.age%20%3C%20b.age%29%3B%0Avar%20people%20%3D%20%5B%0A%20%20%2F%2F%20...%0A%5D%3B%0Avar%20peopleByIncreasingAge%20%3D%20R.sort%28byAge%2C%20people%29%3B)

**[⬆ вверх](#Документация)**



## complement
### `[Logic]`

`(*… → *) → (*… → Boolean)`

#### Параметры:
||
:---|
| f | 
| вернет __Function__ |

Добавлено в версии __v0.12.0__

Принимает функцию `f` и возвращает функцию `g` такую, что если она вызывается с теми же аргументами что и `f`, когда `f` возвращает `true`, `g` возвращает `false`, а когда `f` возвращает значение `false`, `g` возвращает `true`.

R.complement может быть применено к любому функтору.

Смотрите также [not](#not).

```javascript
var isNotNil = R.complement(R.isNil);
isNil(null); //=> true
isNotNil(null); //=> false
isNil(7); //=> false
isNotNil(7); //=> true
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;var%20isNotNil%20%3D%20R.complement%28R.isNil%29%3B%0AisNil%28null%29%3B%20%2F%2F%3D%3E%20true%0AisNotNil%28null%29%3B%20%2F%2F%3D%3E%20false%0AisNil%287%29%3B%20%2F%2F%3D%3E%20false%0AisNotNil%287%29%3B%20%2F%2F%3D%3E%20true)

**[⬆ вверх](#Документация)**


## compose
### `[Function]`

`((y → z), (x → y), …, (o → p), ((a, b, …, n) → o)) → ((a, b, …, n) → z)`

#### Параметры:
|||
:---|:---|
| ...functions | Функции, которые должны быть скомпозированны. |
| вернет __function__ | Скомпозированную функцию |

_Добавлено в версии v0.1.0_

Выполняет композирование функции справа налево. Крайняя правая Функция может иметь любую арность, а другие функции должны быть унарными.

__Зауважте:__ Результат метода `compose` не каррируется автоматически.

Смотрите также [pipe](#pipe).

```javascript
var classyGreeting = (firstName, lastName) => "The name's " + lastName + ", " + firstName + " " + lastName
var yellGreeting = R.compose(R.toUpper, classyGreeting);
yellGreeting('James', 'Bond'); //=> "THE NAME'S BOND, JAMES BOND"

R.compose(Math.abs, R.add(1), R.multiply(2))(-4) //=> 7
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#?var%20classyGreeting%20%3D%20%28firstName%2C%20lastName%29%20%3D%3E%20%22The%20name%27s%20%22%20%2B%20lastName%20%2B%20%22%2C%20%22%20%2B%20firstName%20%2B%20%22%20%22%20%2B%20lastName%0Avar%20yellGreeting%20%3D%20R.compose%28R.toUpper%2C%20classyGreeting%29%3B%0AyellGreeting%28%27James%27%2C%20%27Bond%27%29%3B%20%2F%2F%3D%3E%20%22THE%20NAME%27S%20BOND%2C%20JAMES%20BOND%22%0A%0AR.compose%28Math.abs%2C%20R.add%281%29%2C%20R.multiply%282%29%29%28-4%29%20%2F%2F%3D%3E%207)

**[⬆ вверх](#Документация)**


## composeK
### `[Function]`

`Chain m => ((y → m z), (x → m y), …, (a → m b)) → (a → m z)`

#### Параметры:
|||
:---|:---|
| ...functions | Функции, которые должны быть скомпозированны. |
| вернет __function__ | |

_Добавлено в версии v0.16.0_

Возвращает композицию Kleisli справа налево предоставленных функций, каждая из которых должна возвращать значение типа, поддерживаемого `Chain`.

R.composeK(h, g, f) эквивалент R.compose(R.chain(h), R.chain(g), f).

Смотрите также [pipeK](#pipeK).

```javascript
//  get :: String -> Object -> Maybe *
 var get = R.curry((propName, obj) => Maybe(obj[propName]))

 //  getStateCode :: Maybe String -> Maybe String
 var getStateCode = R.composeK(
   R.compose(Maybe.of, R.toUpper),
   get('state'),
   get('address'),
   get('user'),
 );
 getStateCode({"user":{"address":{"state":"ny"}}}); //=> Maybe.Just("NY")
 getStateCode({}); //=> Maybe.Nothing()
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#?var%20classyGreeting%20%3D%20%28firstName%2C%20lastName%29%20%3D%3E%20%22The%20name%27s%20%22%20%2B%20lastName%20%2B%20%22%2C%20%22%20%2B%20firstName%20%2B%20%22%20%22%20%2B%20lastName%0Avar%20yellGreeting%20%3D%20R.compose%28R.toUpper%2C%20classyGreeting%29%3B%0AyellGreeting%28%27James%27%2C%20%27Bond%27%29%3B%20%2F%2F%3D%3E%20%22THE%20NAME%27S%20BOND%2C%20JAMES%20BOND%22%0A%0AR.compose%28Math.abs%2C%20R.add%281%29%2C%20R.multiply%282%29%29%28-4%29%20%2F%2F%3D%3E%207)

**[⬆ вверх](#Документация)**


## composeP
### `[Function]`

`((y → Promise z), (x → Promise y), …, (a → Promise b)) → (a → Promise z)`

#### Параметры:
|||
:---|:---|
| ...functions | Функции, которые должны быть скомпозированны. |
| вернет __function__ | |

_Добавлено в версии v0.10.0_

Выполняет композицию справа налево одной или нескольких функций, возвращающих `Promise`. Крайняя правая функция может иметь любую арность, остальные функции должны быть унарными.

Смотрите также [pipeP](#pipeP).

```javascript
var db = {
  users: {
    JOE: {
      name: 'Joe',
      followers: ['STEVE', 'SUZY']
    }
  }
}

// We'll pretend to do a db lookup which returns a promise
var lookupUser = (userId) => Promise.resolve(db.users[userId])
var lookupFollowers = (user) => Promise.resolve(user.followers)
lookupUser('JOE').then(lookupFollowers)

//  followersForUser :: String -> Promise [UserId]
var followersForUser = R.composeP(lookupFollowers, lookupUser);
followersForUser('JOE').then(followers => console.log('Followers:', followers))
// Followers: ["STEVE","SUZY"]
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;var%20db%20%3D%20%7B%0A%20%20users%3A%20%7B%0A%20%20%20%20JOE%3A%20%7B%0A%20%20%20%20%20%20name%3A%20%27Joe%27%2C%0A%20%20%20%20%20%20followers%3A%20%5B%27STEVE%27%2C%20%27SUZY%27%5D%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%0A%0A%2F%2F%20We%27ll%20pretend%20to%20do%20a%20db%20lookup%20which%20returns%20a%20promise%0Avar%20lookupUser%20%3D%20%28userId%29%20%3D%3E%20Promise.resolve%28db.users%5BuserId%5D%29%0Avar%20lookupFollowers%20%3D%20%28user%29%20%3D%3E%20Promise.resolve%28user.followers%29%0AlookupUser%28%27JOE%27%29.then%28lookupFollowers%29%0A%0A%2F%2F%20%20followersForUser%20%3A%3A%20String%20-%3E%20Promise%20%5BUserId%5D%0Avar%20followersForUser%20%3D%20R.composeP%28lookupFollowers%2C%20lookupUser%29%3B%0AfollowersForUser%28%27JOE%27%29.then%28followers%20%3D%3E%20console.log%28%27Followers%3A%27%2C%20followers%29%29%0A%2F%2F%20Followers%3A%20%5B%22STEVE%22%2C%22SUZY%22%5D)

**[⬆ вверх](#Документация)**



## concat
### `[List]`

`[a] → [a] → [a]`
`String → String → String`

#### Параметры:
|||
:---|:---|
| firstList | Первый список. |
| secondList | Второй список. |
| вернет __Array__ | Список, состоящий из элементов `firstList` и элементов `secondList`. |

_Добавлено в версии v0.1.0_

Возвращает результат конкатенации данных списков или строк.

__Примечание:__ R.concat ожидает, что оба аргумента будут одного типа, в отличие от метода Array.prototype.concat. Он выдаст ошибку, если вы конкатенируете массив с примитвом.

Отправляет метод `concat` первого аргумента, если он присутствует.  Может также объединять два члена полугруппы совместимой с [fantasy-land](https://github.com/fantasyland/fantasy-land#semigroup).

```javascript
R.concat('ABC', 'DEF'); // 'ABCDEF'
R.concat([4, 5, 6], [1, 2, 3]); //=> [4, 5, 6, 1, 2, 3]
R.concat([], []); //=> []
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;var%20db%20%3D%20%7B%0A%20%20users%3A%20%7B%0A%20%20%20%20JOE%3A%20%7B%0A%20%20%20%20%20%20name%3A%20%27Joe%27%2C%0A%20%20%20%20%20%20followers%3A%20%5B%27STEVE%27%2C%20%27SUZY%27%5D%0A%20%20%20%20%7D%0A%20%20%7D%0A%7D%0A%0A%2F%2F%20We%27ll%20pretend%20to%20do%20a%20db%20lookup%20which%20returns%20a%20promise%0Avar%20lookupUser%20%3D%20%28userId%29%20%3D%3E%20Promise.resolve%28db.users%5BuserId%5D%29%0Avar%20lookupFollowers%20%3D%20%28user%29%20%3D%3E%20Promise.resolve%28user.followers%29%0AlookupUser%28%27JOE%27%29.then%28lookupFollowers%29%0A%0A%2F%2F%20%20followersForUser%20%3A%3A%20String%20-%3E%20Promise%20%5BUserId%5D%0Avar%20followersForUser%20%3D%20R.composeP%28lookupFollowers%2C%20lookupUser%29%3B%0AfollowersForUser%28%27JOE%27%29.then%28followers%20%3D%3E%20console.log%28%27Followers%3A%27%2C%20followers%29%29%0A%2F%2F%20Followers%3A%20%5B%22STEVE%22%2C%22SUZY%22%5D)

**[⬆ вверх](#Документация)**


## cond
### `[Logoc]`

`[[(*… → Boolean),(*… → *)]] → (*… → *)`

#### Параметры:
|||
:---|:---|
| pairs | Список [предикат, трансформатор] |
| вернет __Function__ ||

_Добавлено в версии v0.6.0_

Возвращает функцию fn, которая инкапсулирует `if/else`, `if/else`, `... logic`. R.cond принимает список пар [предикат, трансформатор]. Все аргументы `fn` применяются к каждому из предикатов по очереди, пока не вернется «истинное» значение, после чего `fn` возвращает результат применения своих аргументов к соответствующему трансформатору. Если ни один из предикатов не совпадает, `fn` возвращает `undefined`.

Отправляет метод `concat` первого аргумента, если он присутствует.  Может также объединять два члена полугруппы совместимой с [fantasy-land](https://github.com/fantasyland/fantasy-land#semigroup).

```javascript
var fn = R.cond([
  [R.equals(0),   R.always('water freezes at 0°C')],
  [R.equals(100), R.always('water boils at 100°C')],
  [R.T,           temp => 'nothing special happens at ' + temp + '°C']
]);
fn(0); //=> 'water freezes at 0°C'
fn(50); //=> 'nothing special happens at 50°C'
fn(100); //=> 'water boils at 100°C'
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;var%20fn%20%3D%20R.cond%28%5B%0A%20%20%5BR.equals%280%29%2C%20%20%20R.always%28%27water%20freezes%20at%200%C2%B0C%27%29%5D%2C%0A%20%20%5BR.equals%28100%29%2C%20R.always%28%27water%20boils%20at%20100%C2%B0C%27%29%5D%2C%0A%20%20%5BR.T%2C%20%20%20%20%20%20%20%20%20%20%20temp%20%3D%3E%20%27nothing%20special%20happens%20at%20%27%20%2B%20temp%20%2B%20%27%C2%B0C%27%5D%0A%5D%29%3B%0Afn%280%29%3B%20%2F%2F%3D%3E%20%27water%20freezes%20at%200%C2%B0C%27%0Afn%2850%29%3B%20%2F%2F%3D%3E%20%27nothing%20special%20happens%20at%2050%C2%B0C%27%0Afn%28100%29%3B%20%2F%2F%3D%3E%20%27water%20boils%20at%20100%C2%B0C%27)

**[⬆ вверх](#Документация)**


## construct
### `[Fnction]`

`(* → {*}) → (* → {*})`

#### Параметры:
|||
:---|:---|
| fn | Функция конструктор для обертывания. |
| вернет __Function__ | Каррированная функция конструктор.|

_Добавлено в версии v0.1.0_

Оборачивает функцию-конструктор внутри каррированной функции, которая может быть вызвана с теми же аргументами и возвращает один и тот же тип.

Смотрите также [invoker](#invoker).

```javascript
// Constructor function
function Animal(kind) {
  this.kind = kind;
};
Animal.prototype.sighting = function() {
  return "It's a " + this.kind + "!";
}

var AnimalConstructor = R.construct(Animal)

// Notice we no longer need the 'new' keyword:
AnimalConstructor('Pig'); //=> {"kind": "Pig", "sighting": function (){...}};

var animalTypes = ["Lion", "Tiger", "Bear"];
var animalSighting = R.invoker(0, 'sighting');
var sightNewAnimal = R.compose(animalSighting, AnimalConstructor);
R.map(sightNewAnimal, animalTypes); //=> ["It's a Lion!", "It's a Tiger!", "It's a Bear!"]
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;%2F%2F%20Constructor%20function%0Afunction%20Animal%28kind%29%20%7B%0A%20%20this.kind%20%3D%20kind%3B%0A%7D%3B%0AAnimal.prototype.sighting%20%3D%20function%28%29%20%7B%0A%20%20return%20%22It%27s%20a%20%22%20%2B%20this.kind%20%2B%20%22%21%22%3B%0A%7D%0A%0Avar%20AnimalConstructor%20%3D%20R.construct%28Animal%29%0A%0A%2F%2F%20Notice%20we%20no%20longer%20need%20the%20%27new%27%20keyword%3A%0AAnimalConstructor%28%27Pig%27%29%3B%20%2F%2F%3D%3E%20%7B%22kind%22%3A%20%22Pig%22%2C%20%22sighting%22%3A%20function%20%28%29%7B...%7D%7D%3B%0A%0Avar%20animalTypes%20%3D%20%5B%22Lion%22%2C%20%22Tiger%22%2C%20%22Bear%22%5D%3B%0Avar%20animalSighting%20%3D%20R.invoker%280%2C%20%27sighting%27%29%3B%0Avar%20sightNewAnimal%20%3D%20R.compose%28animalSighting%2C%20AnimalConstructor%29%3B%0AR.map%28sightNewAnimal%2C%20animalTypes%29%3B%20%2F%2F%3D%3E%20%5B%22It%27s%20a%20Lion%21%22%2C%20%22It%27s%20a%20Tiger%21%22%2C%20%22It%27s%20a%20Bear%21%22%5D)

**[⬆ вверх](#Документация)**


## constructN
### `[Fnction]`

`Number → (* → {*}) → (* → {*})`

#### Параметры:
|||
:---|:---|
| n | Арность функции-конструктора. |
| fn | Функция конструктор для обертывания. |
| вернет __Function__ | Каррированная функция конструктор.|

_Добавлено в версии v0.4.0_

Оборачивает функцию-конструктор внутри каррированной функции, которая может быть вызвана с теми же аргументами и возвращает один и тот же тип. Арность функции возвращается, чтобы разрешить использование функций с переменным числом аргументов конструктора.

Смотрите также [invoker](#invoker).

```javascript
// Функция конструктор с переменным числом аргументов
function Salad() {
  this.ingredients = arguments;
}

Salad.prototype.recipe = function() {
  var instructions = R.map(ingredient => 'Add a dollop of ' + ingredient, this.ingredients);
  return R.join('\n', instructions);
};

var ThreeLayerSalad = R.constructN(3, Salad);

// Обратите внимание, что нам больше не нужно ключевое слово "new", и конструктор каррирован для 3 аргументов.
var salad = ThreeLayerSalad('Mayonnaise')('Potato Chips')('Ketchup');

console.log(salad.recipe());
// Add a dollop of Mayonnaise
// Add a dollop of Potato Chips
// Add a dollop of Ketchup
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;%2F%2F%20Variadic%20Constructor%20function%0Afunction%20Salad%28%29%20%7B%0A%20%20this.ingredients%20%3D%20arguments%3B%0A%7D%0A%0ASalad.prototype.recipe%20%3D%20function%28%29%20%7B%0A%20%20var%20instructions%20%3D%20R.map%28ingredient%20%3D%3E%20%27Add%20a%20dollop%20of%20%27%20%2B%20ingredient%2C%20this.ingredients%29%3B%0A%20%20return%20R.join%28%27%5Cn%27%2C%20instructions%29%3B%0A%7D%3B%0A%0Avar%20ThreeLayerSalad%20%3D%20R.constructN%283%2C%20Salad%29%3B%0A%0A%2F%2F%20Notice%20we%20no%20longer%20need%20the%20%27new%27%20keyword%2C%20and%20the%20constructor%20is%20curried%20for%203%20arguments.%0Avar%20salad%20%3D%20ThreeLayerSalad%28%27Mayonnaise%27%29%28%27Potato%20Chips%27%29%28%27Ketchup%27%29%3B%0A%0Aconsole.log%28salad.recipe%28%29%29%3B%0A%2F%2F%20Add%20a%20dollop%20of%20Mayonnaise%0A%2F%2F%20Add%20a%20dollop%20of%20Potato%20Chips%0A%2F%2F%20Add%20a%20dollop%20of%20Ketchup)

**[⬆ вверх](#Документация)**


## contains
### `[List]`

`a → [a] → Boolean`

#### Параметры:
|||
:---|:---|
| a | Элемент для сравнения. |
| list | Массив для рассмотрения. |
| вернет __Boolean__ | `true`, если эквивалентный элемент находится в списке, в противном случае - `false`. |

_Добавлено в версии v0.1.0_

Возвращает `true`, если указанное значение равно, с точки зрения R.equals, по меньшей мере одному элементу данного списка, `false` в противном случае.

Смотрите также [any](#any).

```javascript
R.contains(3, [1, 2, 3]); //=> true
R.contains(4, [1, 2, 3]); //=> false
R.contains({ name: 'Fred' }, [{ name: 'Fred' }]); //=> true
R.contains([42], [[42]]); //=> true
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;R.contains%283%2C%20%5B1%2C%202%2C%203%5D%29%3B%20%2F%2F%3D%3E%20true%0AR.contains%284%2C%20%5B1%2C%202%2C%203%5D%29%3B%20%2F%2F%3D%3E%20false%0AR.contains%28%7B%20name%3A%20%27Fred%27%20%7D%2C%20%5B%7B%20name%3A%20%27Fred%27%20%7D%5D%29%3B%20%2F%2F%3D%3E%20true%0AR.contains%28%5B42%5D%2C%20%5B%5B42%5D%5D%29%3B%20%2F%2F%3D%3E%20true)

**[⬆ вверх](#Документация)**


## converge
### `[Function]`

`(x1 → x2 → … → z) → [(a → b → … → x1), (a → b → … → x2), …] → (a → b → … → z)`

#### Параметры:
|||
:---|:---|
| after | Функция `after` будет вызвона с возвращаемыми значениями `fn1` и `fn2` в качестве аргументов. |
| functions | Список функций. |
| вернет __function__ | Новая функция. |

_Добавлено в версии v0.4.2_

Принимает функцию преобразователь и список функций и вернет новую функцию. При вызове эта новая Функция применяется к некоторым аргументам, каждая переданная Функция применяется к соответствующим аргументам. Результат каждой примененной функции передается как аргумент функции преобразователя для создания возвращаемого значение.

Смотрите также [useWith](#usewith).

```javascript
var average = R.converge(R.divide, [R.sum, R.length])
average([1, 2, 3, 4, 5, 6, 7]) //=> 4

var strangeConcat = R.converge(R.concat, [R.toUpper, R.toLower])
strangeConcat("Yodel") //=> "YODELyodel"
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#;var%20average%20%3D%20R.converge%28R.divide%2C%20%5BR.sum%2C%20R.length%5D%29%0Aaverage%28%5B1%2C%202%2C%203%2C%204%2C%205%2C%206%2C%207%5D%29%20%2F%2F%3D%3E%204%0A%0Avar%20strangeConcat%20%3D%20R.converge%28R.concat%2C%20%5BR.toUpper%2C%20R.toLower%5D%29%0AstrangeConcat%28%22Yodel%22%29%20%2F%2F%3D%3E%20%22YODELyodel%22)

**[⬆ вверх](#Документация)**


## countBy
### `[Relation]`

`(a → String) → [a] → {*}`

#### Параметры:
|||
:---|:---|
| fn | Функция, используемая для сопоставления ключ - значение. |
| list | Список для подсчета элементов. |
| вернет __Object__ | Сопоставление ключей объекта с числом, вхождений в список. (An object mapping keys to number, of occurrences in the list.) |

_Добавлено в версии v0.1.0_

Подсчитывает элементы списка в зависимости от того, сколько из них соответствует каждому значению ключа, сгенерированного предоставленной функцией. Возвращает объект, сопоставляющий ключи, созданные `fn`, с количеством вхождений в списке. Обратите внимание, что все ключи принудительно приведены к строкам из-за того, как работают объекты JavaScript.

Действует как преобразователь, если трансформатор задан в позиции списка.

```javascript
var numbers = [1.0, 1.1, 1.2, 2.0, 3.0, 2.2];
R.countBy(Math.floor)(numbers);    //=> {'1': 3, '2': 2, '3': 1}

var letters = ['a', 'b', 'A', 'a', 'B', 'c'];
R.countBy(R.toLower)(letters);   //=> {'a': 3, 'b': 2, 'c': 1}
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;var%20numbers%20%3D%20%5B1.0%2C%201.1%2C%201.2%2C%202.0%2C%203.0%2C%202.2%5D%3B%0AR.countBy%28Math.floor%29%28numbers%29%3B%20%20%20%20%2F%2F%3D%3E%20%7B%271%27%3A%203%2C%20%272%27%3A%202%2C%20%273%27%3A%201%7D%0A%0Avar%20letters%20%3D%20%5B%27a%27%2C%20%27b%27%2C%20%27A%27%2C%20%27a%27%2C%20%27B%27%2C%20%27c%27%5D%3B%0AR.countBy%28R.toLower%29%28letters%29%3B%20%20%20%2F%2F%3D%3E%20%7B%27a%27%3A%203%2C%20%27b%27%3A%202%2C%20%27c%27%3A%201%7D)

**[⬆ вверх](#Документация)**


## curry
### `[Function]`

`(* → a) → (* → a)`

#### Параметры:
|||
:---|:---|
| fn | Функция, которую ужно закаррировать. |
| вернет __Function__ | Новая каррированная функция|

_Добавлено в версии v0.1.0_

Возвращает эквивалент предоставленной функции. Функция карри имеет две необычные возможности. 

Во-первых, его аргументы не обязательно должны предоставляться по одному. Если `f` - тернарная функция, а `g` - `R.curry(f)`, то следующие функции эквивалентны:

  * g(1)(2)(3)
  * g(1)(2, 3)
  * g(1, 2)(3)
  * g(1, 2, 3)
  
  Во-вторых, специальное значение placeholder `R.__` может использоваться для указания «пробелов», допускающих частичное применение любой комбинации аргументов независимо от их позиций. Если `g` является таким, как указано выше, а `_` является `R.__`, то следующие функции эквивалентны:
  
  * g(1, 2, 3)
  * g(_ , 2, 3)(1)
  * g(_ , _ , 3)(1)(2)
  * g(_ , _ , 3)(1, 2)
  * g(_ , 2)(1)(3)
  * g(_ , 2)(1, 3)
  * g(_ , 2)(_ , 3)(1)

Смотрите также [curryN](#curryN).

```javascript
var addFourNumbers = (a, b, c, d) => a + b + c + d;

var curriedAddFourNumbers = R.curry(addFourNumbers);
var f = curriedAddFourNumbers(1, 2);
var g = f(3);
g(4); //=> 10
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;var%20addFourNumbers%20%3D%20%28a%2C%20b%2C%20c%2C%20d%29%20%3D%3E%20a%20%2B%20b%20%2B%20c%20%2B%20d%3B%0A%0Avar%20curriedAddFourNumbers%20%3D%20R.curry%28addFourNumbers%29%3B%0Avar%20f%20%3D%20curriedAddFourNumbers%281%2C%202%29%3B%0Avar%20g%20%3D%20f%283%29%3B%0Ag%284%29%3B%20%2F%2F%3D%3E%2010)

**[⬆ вверх](#Документация)**


## curryN
### `[Function]`

`Number → (* → a) → (* → a)`

#### Параметры:
|||
:---|:---|
| length | Арность возвращаемой функции |
| fn | Функция, которую ужно закаррировать. |
| вернет __Function__ | Новая каррированная функция|

_Добавлено в версии v0.5.0_

Возвращает эквивалент предоставленной функции, с заданной арностью. Функция карри имеет две необычные возможности. 

Во-первых, его аргументы не обязательно должны предоставляться по одному. Если `g` является `R.curryN(3, f)`, то следующие эквиваленты:

  * g(1)(2)(3)
  * g(1)(2, 3)
  * g(1, 2)(3)
  * g(1, 2, 3)
  
  Во-вторых, специальное значение placeholder `R.__` может использоваться для указания «пробелов», допускающих частичное применение любой комбинации аргументов независимо от их позиций. Если `g` является таким, как указано выше, а `_` является `R.__`, то следующие функции эквивалентны:
  
  * g(1, 2, 3)
  * g(_ , 2, 3)(1)
  * g(_ , _ , 3)(1)(2)
  * g(_ , _ , 3)(1, 2)
  * g(_ , 2)(1)(3)
  * g(_ , 2)(1, 3)
  * g(_ , 2)(_ , 3)(1)

Смотрите также [curry](#curry).

```javascript
var sumArgs = (...args) => R.sum(args);

var curriedAddFourNumbers = R.curryN(4, sumArgs);
var f = curriedAddFourNumbers(1, 2);
var g = f(3);
g(4); //=> 10
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;var%20sumArgs%20%3D%20%28...args%29%20%3D%3E%20R.sum%28args%29%3B%0A%0Avar%20curriedAddFourNumbers%20%3D%20R.curryN%284%2C%20sumArgs%29%3B%0Avar%20f%20%3D%20curriedAddFourNumbers%281%2C%202%29%3B%0Avar%20g%20%3D%20f%283%29%3B%0Ag%284%29%3B%20%2F%2F%3D%3E%2010)

**[⬆ вверх](#Документация)**


## dec
### `[Math]`

`Number → Number`

#### Параметры:
||
:---|
| n |
| вернет __Number__ n - 1 |

_Добавлено в версии v0.9.0_

Уменьшит свой аргумент.

Смотрите также [inc](#inc).

```javascript
R.dec(42); //=> 41
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.25.0#;R.dec%2842%29%3B%20%2F%2F%3D%3E%2041)

**[⬆ вверх](#Документация)**



## defaultTo
### `[Logic]`

`a → b → a | b`

#### Параметры:
|||
:---|:---|
| default | Значение по умолчанию |
| val | `val` будет возвращен вместо значения по умолчанию, пока `val` не является `null`, `undefined` или` NaN` |
| _вернет_ * | Второе значение, если оно не является `null`, `undefined` или `NaN`, иначе вернет значение по умолчанию |

_Добавлено в версии v0.10.0_

вернет второй аргумент если он не  `null`, `undefined` или `NaN`, иначе вернет `default`.

```javascript
var defaultTo42 = R.defaultTo(42);

defaultTo42(null);  //=> 42
defaultTo42(undefined);  //=> 42
defaultTo42('Ramda');  //=> 'Ramda'
// parseInt('string') results in NaN
defaultTo42(parseInt('string')); //=> 42
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.25.0#;var%20defaultTo42%20%3D%20R.defaultTo%2842%29%3B%0A%0AdefaultTo42%28null%29%3B%20%20%2F%2F%3D%3E%2042%0AdefaultTo42%28undefined%29%3B%20%20%2F%2F%3D%3E%2042%0AdefaultTo42%28%27Ramda%27%29%3B%20%20%2F%2F%3D%3E%20%27Ramda%27%0A%2F%2F%20parseInt%28%27string%27%29%20results%20in%20NaN%0AdefaultTo42%28parseInt%28%27string%27%29%29%3B%20%2F%2F%3D%3E%2042)

**[⬆ вверх](#Документация)**



## descend
### `[Function]`

`Ord b => (a → b) → a → a → Number`

#### Параметры:
|||
:---|:---|
| fn | Унарная функция, возвращающая значение, которое можно сравнить |
| a | Первый элемент для сравнения. |
| b | Второй элемент для сравнения. |
| вернет __Number__ | `-1` в случае, если `fn(a) > fn(b)`, или `1`, если `fn(b) > fn(a)`, иначе вернет `0`|

_Добавлено в версии v0.23.0_

Создает нисходящий компаратор из функции, которая возвращает значение, которое можно сравнить с `<` и `>`.

Смотрите также [ascend](#ascend).

```javascript
var byAge = R.descend(R.prop('age'));
var people = [
  // ...
];
var peopleByOldestFirst = R.sort(byAge, people);
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#?var%20byAge%20%3D%20R.descend%28R.prop%28%27age%27%29%29%3B%0Avar%20people%20%3D%20%5B%0A%20%20%2F%2F%20...%0A%5D%3B%0Avar%20peopleByOldestFirst%20%3D%20R.sort%28byAge%2C%20people%29%3B)

**[⬆ вверх](#Документация)**



## difference
### `[Relation]`

`[*] → [*] → [*]`

#### Параметры:
|||
:---|:---|
| list1 | Первый список. |
| list2 | Второй список. |
| вернет __Array__ | вернет массив элементов из списка `list1`, которых нет в списке` list2`. |

_Добавлено в версии v0.1.0_

Находит набор (неповторяющихся) элементов из первого списка, которых нет во втором списке. Объекты и массивы сравниваются с точки зрения равенства значений, а не равенства ссылок.

Смотрите также [differenceWith](#differencewidth), [symmetricDifference](#symmetricdifference), [symmetricDifferenceWith](#symmetricdifferencewith), [without](#without).

```javascript
R.difference([1,2,3,4], [7,6,5,4,3]); //=> [1,2]
R.difference([7,6,5,4,3], [1,2,3,4]); //=> [7,6,5]
R.difference([{a: 1}, {b: 2}], [{a: 1}, {c: 3}]) //=> [{b: 2}]
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#?R.difference%28%5B1%2C2%2C3%2C4%5D%2C%20%5B7%2C6%2C5%2C4%2C3%5D%29%3B%20%2F%2F%3D%3E%20%5B1%2C2%5D%0AR.difference%28%5B7%2C6%2C5%2C4%2C3%5D%2C%20%5B1%2C2%2C3%2C4%5D%29%3B%20%2F%2F%3D%3E%20%5B7%2C6%2C5%5D%0AR.difference%28%5B%7Ba%3A%201%7D%2C%20%7Bb%3A%202%7D%5D%2C%20%5B%7Ba%3A%201%7D%2C%20%7Bc%3A%203%7D%5D%29%20%2F%2F%3D%3E%20%5B%7Bb%3A%202%7D%5D)

**[⬆ вверх](#Документация)**



## differenceWith
### `[Relation]`

`((a, a) → Boolean) → [a] → [a] → [a]`

#### Параметры:
|||
:---|:---|
| pred | Предикат, который используется для выяснения равны ли елементы между собой. |
| list1 | Первый список. |
| list2 | Второй список. |
| вернет __Array__ | вернет массив элементов из списка `list1`, которых нет в списке` list2`. |

_Добавлено в версии v0.1.0_

Находит набор (неповторяющихся) элементов первого списка, которых нет во втором списке. Повторяемость элементов оказывается согласно значению, которое вернетться после применения предоставленного предиката по обоим спискам.

Смотрите также [difference](#difference), [symmetricDifference](#symmetricdifference), [symmetricDifferenceWith](#symmetricdifferencewith).

```javascript
var cmp = (x, y) => x.a === y.a;
var l1 = [{a: 1}, {a: 2}, {a: 3}];
var l2 = [{a: 3}, {a: 4}];
R.differenceWith(cmp, l1, l2); //=> [{a: 1}, {a: 2}]
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#?var%20cmp%20%3D%20%28x%2C%20y%29%20%3D%3E%20x.a%20%3D%3D%3D%20y.a%3B%0Avar%20l1%20%3D%20%5B%7Ba%3A%201%7D%2C%20%7Ba%3A%202%7D%2C%20%7Ba%3A%203%7D%5D%3B%0Avar%20l2%20%3D%20%5B%7Ba%3A%203%7D%2C%20%7Ba%3A%204%7D%5D%3B%0AR.differenceWith%28cmp%2C%20l1%2C%20l2%29%3B%20%2F%2F%3D%3E%20%5B%7Ba%3A%201%7D%2C%20%7Ba%3A%202%7D%5D)

**[⬆ вверх](#Документация)**



## dissoc
### `[Object]`

`String → {k: v} → {k: v}`

#### Параметры:
|||
:---|:---|
| prop | Имя свойства, которое нужно диссоциировать (отделить) |
| obj | Объект, который нужно клонировать |
| вернет __Object__ | Новый объект, эквивалентный `obj`, но без указанного свойства `prop`. |

_Добавлено в версии v0.10.0_

вернет объект, не содержащий указанного свойства `prop`.

Смотрите также [assoc](#assoc).

```javascript
R.dissoc('b', {a: 1, b: 2, c: 3}); //=> {a: 1, c: 3}
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.25.0#?R.dissoc%28%27b%27%2C%20%7Ba%3A%201%2C%20b%3A%202%2C%20c%3A%203%7D%29%3B%20%2F%2F%3D%3E%20%7Ba%3A%201%2C%20c%3A%203%7D)

**[⬆ вверх](#Документация)**



## dissocPath
### `[Object]`

`[Idx] → {k: v} → {k: v}`
`Idx = String | Int`

#### Параметры:
|||
:---|:---|
| path | Путь до значения, которое надо пропустить |
| obj | Объект, который нужно копировать |
| вернет __Object__ | Новый объект без свойства, которое находится по указанному пути. |

_Добавлено в версии v0.11.0_

Создает поверхностную копию объекта, пропуская свойство по указанному пути. __Примечание__: это также копирует и приравнивает свойства прототипа к новому объекту. Все непримитивы копируются по ссылке.

Смотрите также [assocPath](#assocpath).

```javascript
R.dissocPath(['a', 'b', 'c'], {a: {b: {c: 42}}}); //=> {a: {b: {}}}
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.25.0#;R.dissocPath%28%5B%27a%27%2C%20%27b%27%2C%20%27c%27%5D%2C%20%7Ba%3A%20%7Bb%3A%20%7Bc%3A%2042%7D%7D%7D%29%3B%20%2F%2F%3D%3E%20%7Ba%3A%20%7Bb%3A%20%7B%7D%7D%7D)

*[⬆ вверх](#Документация)**



## divide
### `[Math]`

`Number → Number → Number`

#### Параметры:
|||
:---|:---|
| a | Первое значение. |
| b | Первое значение. |
| вернет __Number__ | Результат `a / b`. |

_Добавлено в версии v0.1.0_

Делит два числа, эквивалент `a / b`.

Смотрите также [multiply](#multiply).

```javascript
R.divide(71, 100); //=> 0.71

var half = R.divide(R.__, 2);
half(42); //=> 21

var reciprocal = R.divide(1);
reciprocal(4);   //=> 0.25
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.25.0#?R.divide%2871%2C%20100%29%3B%20%2F%2F%3D%3E%200.71%0A%0Avar%20half%20%3D%20R.divide%28R.__%2C%202%29%3B%0Ahalf%2842%29%3B%20%2F%2F%3D%3E%2021%0A%0Avar%20reciprocal%20%3D%20R.divide%281%29%3B%0Areciprocal%284%29%3B%20%20%20%2F%2F%3D%3E%200.25)

**[⬆ вверх](#Документация)**



## drop

### `[List]`

`Number → [a] → [a]`
`Number → String → String`

#### Параметры:
|||
:---|:---|
| n ||
| list ||
| вернет __*__ | Копию списка без первых `n` 'ktvtynjd. |

_Добавлено в версии v0.1.0_

вернет все, кроме первых `n` элементов передаваемого списка, сроки или трансдюсера/трансформера (или объекта с `drop` методом)

Выполняется со вторым аргументом, если тот присутствует.

Смотрите также [take](#take), [transduce](#transduce), [dropLast](#droplast), [dropWhile](#dropwhile)

```javascript
R.drop(1, ['foo', 'bar', 'baz']); //=> ['bar', 'baz']
R.drop(2, ['foo', 'bar', 'baz']); //=> ['baz']
R.drop(3, ['foo', 'bar', 'baz']); //=> []
R.drop(4, ['foo', 'bar', 'baz']); //=> []
R.drop(3, 'ramda');               //=> 'da'
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.25.0#?R.drop%281%2C%20%5B%27foo%27%2C%20%27bar%27%2C%20%27baz%27%5D%29%3B%20%2F%2F%3D%3E%20%5B%27bar%27%2C%20%27baz%27%5D%0AR.drop%282%2C%20%5B%27foo%27%2C%20%27bar%27%2C%20%27baz%27%5D%29%3B%20%2F%2F%3D%3E%20%5B%27baz%27%5D%0AR.drop%283%2C%20%5B%27foo%27%2C%20%27bar%27%2C%20%27baz%27%5D%29%3B%20%2F%2F%3D%3E%20%5B%5D%0AR.drop%284%2C%20%5B%27foo%27%2C%20%27bar%27%2C%20%27baz%27%5D%29%3B%20%2F%2F%3D%3E%20%5B%5D%0AR.drop%283%2C%20%27ramda%27%29%3B%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%2F%2F%3D%3E%20%27da%27)

**[⬆ вверх](#Документация)**



## dropLast

### `[List]`

`Number → [a] → [a]`
`Number → String → String`

#### Параметры:
|||
:---|:---|
| n | Количество элементов списка, которое нужно пропустить. |
| list | Список элементов. |
| вернет __Array__ | Копия списка только c первыми `list.length - n` элементами. |

_Добавлено в версии v0.16.0_

вернет список, который содержит все кроме последних `n` элементов передаваемого списка.

Смотрите также [takeLast](#takelast), [drop](#drop), [dropWhile](#dropwhile), [dropLastWhile](#droplastwhile).

```javascript
R.dropLast(1, ['foo', 'bar', 'baz']); //=> ['foo', 'bar']
R.dropLast(2, ['foo', 'bar', 'baz']); //=> ['foo']
R.dropLast(3, ['foo', 'bar', 'baz']); //=> []
R.dropLast(4, ['foo', 'bar', 'baz']); //=> []
R.dropLast(3, 'ramda');               //=> 'ra'
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.25.0#?R.dropLast%281%2C%20%5B%27foo%27%2C%20%27bar%27%2C%20%27baz%27%5D%29%3B%20%2F%2F%3D%3E%20%5B%27foo%27%2C%20%27bar%27%5D%0AR.dropLast%282%2C%20%5B%27foo%27%2C%20%27bar%27%2C%20%27baz%27%5D%29%3B%20%2F%2F%3D%3E%20%5B%27foo%27%5D%0AR.dropLast%283%2C%20%5B%27foo%27%2C%20%27bar%27%2C%20%27baz%27%5D%29%3B%20%2F%2F%3D%3E%20%5B%5D%0AR.dropLast%284%2C%20%5B%27foo%27%2C%20%27bar%27%2C%20%27baz%27%5D%29%3B%20%2F%2F%3D%3E%20%5B%5D%0AR.dropLast%283%2C%20%27ramda%27%29%3B%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%2F%2F%3D%3E%20%27ra%27)

**[⬆ вверх](#Документация)**



## dropLastWhile

### `[List]`

`(a → Boolean) → [a] → [a]`
`(a → Boolean) → String → String`

#### Параметры:
|||
:---|:---|
| predicate | Функция, которая должна быть вызвана для каждого элемента. |
| xs | Коллекция, которую надо итерировать. |
| вернет __Array__ | Новый массив без элементов, которые начиная с конца возвращают `falsy` значение из функции-предиката(`predicate`). |

_Добавлено в версии v0.16.0_

Вернет новый список, без последних элементов переданного списка, которые удовлетворяют условию переданной функции-предиката. Она передает каждое значение справа к переданному предикату, отсеивая элементы пока Функция-предикат возвращает `false`. Функция-предикат применяется к одному аргементу: (value).

Смотрите также [takeLastWhile](#takelastwhile), [addIndex](#addindex), [drop](#drop), [dropWhile](#dropwhile).

```javascript
var lteThree = x => x <= 3;

R.dropLastWhile(lteThree, [1, 2, 3, 4, 3, 2, 1]); //=> [1, 2, 3, 4]

R.dropLastWhile(x => x !== 'd' , 'Ramda'); //=> 'Ramd'
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.25.0#?var%20lteThree%20%3D%20x%20%3D%3E%20x%20%3C%3D%203%3B%0A%0AR.dropLastWhile%28lteThree%2C%20%5B1%2C%202%2C%203%2C%204%2C%203%2C%202%2C%201%5D%29%3B%20%2F%2F%3D%3E%20%5B1%2C%202%2C%203%2C%204%5D%0A%0AR.dropLastWhile%28x%20%3D%3E%20x%20%21%3D%3D%20%27d%27%20%2C%20%27Ramda%27%29%3B%20%2F%2F%3D%3E%20%27Ramd%27)

**[⬆ вверх](#Документация)**



## dropRepeats
### `[List]`

`[a] → [a]`

#### Параметры:
|||
:---|:---|
| list | Рассматриваемый массив. |
| вернет __Array__ | `list` без повторяющихся элементов. |

_Добавлено в версии v0.14.0_

вернет новый список без последовательно повторяющихся элементов. Для определения равенства используется `R.equals`.

Ведет себя как трансдюсер, если передан трансформер вместо списка.

Смотрите также [transduce](#transduce).

```javascript
R.dropRepeats([1, 1, 1, 2, 3, 4, 4, 2, 2]); //=> [1, 2, 3, 4, 2]
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.25.0#?R.dropRepeats%28%5B1%2C%201%2C%201%2C%202%2C%203%2C%204%2C%204%2C%202%2C%202%5D%29%3B%20%2F%2F%3D%3E%20%5B1%2C%202%2C%203%2C%204%2C%202%5D)

**[⬆ вверх](#Документация)**




## dropRepeatsWith
### `[List]`

`((a, a) → Boolean) → [a] → [a]`

#### Параметры:
|||
:---|:---|
| pred | Предикат, с помощью которого проверяется, есть ли два элемента равные между собой |
| list | Рассматриваемый массив. |
| вернет __Array__ | `list` без повторяющихся элементов. |

_Добавлено в версии v0.14.0

вернет новый список без последовательно повторяющихся элементов. Равенство определяется применением переданного предиката к каждой паре последовательных элементов. Первый элемент в серии равных элементов будет сохранен.

Ведет себя как трансдюсер, в случае, если вместо списка передан трансформер.

Смотрите также [transduce](#transduce).

```javascript
var l = [1, -1, 1, 3, 4, -4, -4, -5, 5, 3, 3];
R.dropRepeatsWith(R.eqBy(Math.abs), l); //=> [1, 3, 4, -5, 3]
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.25.0#;var%20l%20%3D%20%5B1%2C%20-1%2C%201%2C%203%2C%204%2C%20-4%2C%20-4%2C%20-5%2C%205%2C%203%2C%203%5D%3B%0AR.dropRepeatsWith%28R.eqBy%28Math.abs%29%2C%20l%29%3B%20%2F%2F%3D%3E%20%5B1%2C%203%2C%204%2C%20-5%2C%203%5D)

**[⬆ вверх](#Документация)**



## dropWhile
### `[List]`

`(a → Boolean) → [a] → [a]`
`(a → Boolean) → String → String`

#### Параметры:
|||
:---|:---|
| fn | Фунция, которая будет вызываться на каждой итерации. |
| xs | Итерируемая коллекция. |
| вернет __Array__ | Новый массивю |

_Добавлено в версии v0.9.0_

Вернет новый список, исключая начальные элементы переданного списка, которые удовлетворяют условию переданного предиката. Эта Функция передает каждое значение из списка в предоставленный предикат, пропуская элементы, пока предикат возвращает `true`. Предикат применяется к одному элементу: `(value)`.

Передает в `dropWhile` метод второго аргумента, если тот присутствует.

Ведет себя как трансдюсер, если вместо списка передан трансформер.

Смотрите также [takeWhile](#takewhile), [transduce](#transduce), [addIndex](#addindex).

```javascript
var lteTwo = x => x <= 2;

R.dropWhile(lteTwo, [1, 2, 3, 4, 3, 2, 1]); //=> [3, 4, 3, 2, 1]

R.dropWhile(x => x !== 'd' , 'Ramda'); //=> 'da'
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.25.0#;var%20lteTwo%20%3D%20x%20%3D%3E%20x%20%3C%3D%202%3B%0A%0AR.dropWhile%28lteTwo%2C%20%5B1%2C%202%2C%203%2C%204%2C%203%2C%202%2C%201%5D%29%3B%20%2F%2F%3D%3E%20%5B3%2C%204%2C%203%2C%202%2C%201%5D%0A%0AR.dropWhile%28x%20%3D%3E%20x%20%21%3D%3D%20%27d%27%20%2C%20%27Ramda%27%29%3B%20%2F%2F%3D%3E%20%27da%27)

**[⬆ вверх](#Документация)**

## either
### `[Logic]`

`(*… → Boolean) → (*… → Boolean) → (*… → Boolean)`

#### Параметры:
|||
:---|:---|
| f | предикат |
| d | второй предикат |
| вернет __Function__ | Функция которая применит логическое `или` к передаваемым аргументам |

_Добавлено в версии v0.24.0_

Фунция обертка, вызывает функции и применяет к ним логическое `или`, возвращая результат первой если это истинна `true` или результат второй в противном случае. __Примечание__: вторая функция не будет вызвана если первая вернет `true`.

Помимо функций, `R.either` также принимает апликативные функторы совместимые с `fantasy-land`.
  
Смотрите также [or](#or)

```javascript
var gt10 = x => x > 10;
var even = x => x % 2 === 0;
var f = R.either(gt10, even);
f(101); //=> true
f(8); //=> true
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;var%20gt10%20%3D%20x%20%3D%3E%20x%20%3E%2010%3B%0Avar%20even%20%3D%20x%20%3D%3E%20x%20%25%202%20%3D%3D%3D%200%3B%0Avar%20f%20%3D%20R.either%28gt10%2C%20even%29%3B%0Af%28101%29%3B%20%2F%2F%3D%3E%20true%0Af%288%29%3B%20%2F%2F%3D%3E%20true)

**[⬆ вверх](#Документация)**

## empty
### `[Function]`

`a → a`

#### Параметры:
||
:---|
| x |
| вернет __*__ |

_Добавлено в версии v0.3.0_

Вернет пустое значение типа аргумента. Ramda определяет пустое значение `Array ([])`, `Object ({})`, `String ("")` и `Arguments`. Другие типы поддерживаются, если они определяют `<Type>.empty`, `<Type>.prototype.empty` или реализуют [FantasyLand Monoid](https://github.com/fantasyland/fantasy-land#monoid) спецификацию.
  
Отправляет в `empty` метод первого аргумента, если он есть.

```javascript
R.empty(Just(42));      //=> Nothing()
R.empty([1, 2, 3]);     //=> []
R.empty('unicorns');    //=> ''
R.empty({x: 1, y: 2});  //=> {}
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;R.empty%28Just%2842%29%29%3B%20%20%20%20%20%20%2F%2F%3D%3E%20Nothing%28%29%0AR.empty%28%5B1%2C%202%2C%203%5D%29%3B%20%20%20%20%20%2F%2F%3D%3E%20%5B%5D%0AR.empty%28%27unicorns%27%29%3B%20%20%20%20%2F%2F%3D%3E%20%27%27%0AR.empty%28%7Bx%3A%201%2C%20y%3A%202%7D%29%3B%20%20%2F%2F%3D%3E%20%7B%7D)

**[⬆ вверх](#Документация)**

## endsWith
### `[List]`

`[a] → Boolean`
`String → Boolean`

#### Параметры:
||
:---|
| suffix |
| list | 
| вернет __Boolean__ |

_Добавлено в версии v0.24.0_

Проверит заканчивается ли список `list`, предоставленными значениями.

```javascript
R.endsWith('c', 'abc')                //=> true
R.endsWith('b', 'abc')                //=> false
R.endsWith(['c'], ['a', 'b', 'c'])    //=> true
R.endsWith(['b'], ['a', 'b', 'c'])    //=> false
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;R.endsWith%28%27c%27%2C%20%27abc%27%29%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%2F%2F%3D%3E%20true%0AR.endsWith%28%27b%27%2C%20%27abc%27%29%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%2F%2F%3D%3E%20false%0AR.endsWith%28%5B%27c%27%5D%2C%20%5B%27a%27%2C%20%27b%27%2C%20%27c%27%5D%29%20%20%20%20%2F%2F%3D%3E%20true%0AR.endsWith%28%5B%27b%27%5D%2C%20%5B%27a%27%2C%20%27b%27%2C%20%27c%27%5D%29%20%20%20%20%2F%2F%3D%3E%20false)

**[⬆ вверх](#Документация)**

## eqBy
### `[Relation]`

`(a → b) → a → a → Boolean`

#### Параметры:
||
:---|
| f |
| x | 
| y | 
| вернет __Boolean__ |

_Добавлено в версии v0.18.0_

Принимает функцию и два значения и возвращает `true`, если фукция вернет одно и то же для каждого значения в противном случае `false`.

```javascript
R.eqBy(Math.abs, 5, -5); //=> true
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;R.eqBy%28Math.abs%2C%205%2C%20-5%29%3B%20%2F%2F%3D%3E%20true)

**[⬆ вверх](#Документация)**

## eqProps
### `[Object]`

`k → {k: v} → {k: v} → Boolean`

#### Параметры:
|||
:---|:---|
| props | Имя свойства для сравнения |
| obj1 | |
| obj2 | |
| вернет __Boolean__ ||

_Добавлено в версии v0.1.0_

Проверяет, имеют объекты одинаковое значение, по логике `R.equals` для указанного свойства. Полезен как каррированный предикат.

```javascript
var o1 = { a: 1, b: 2, c: 3, d: 4 };
var o2 = { a: 10, b: 20, c: 3, d: 40 };
R.eqProps('a', o1, o2); //=> false
R.eqProps('c', o1, o2); //=> true
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;var%20o1%20%3D%20%7B%20a%3A%201%2C%20b%3A%202%2C%20c%3A%203%2C%20d%3A%204%20%7D%3B%0Avar%20o2%20%3D%20%7B%20a%3A%2010%2C%20b%3A%2020%2C%20c%3A%203%2C%20d%3A%2040%20%7D%3B%0AR.eqProps%28%27a%27%2C%20o1%2C%20o2%29%3B%20%2F%2F%3D%3E%20false%0AR.eqProps%28%27c%27%2C%20o1%2C%20o2%29%3B%20%2F%2F%3D%3E%20true)

**[⬆ вверх](#Документация)**

## equals
### `[Relation]`

`a → b → Boolean`

#### Параметры:
||
:---|
| a |
| b |
| вернет __Boolean__ |

_Добавлено в версии v0.15.0_

Вернет `true`, если аргументы эквивалентны, иначе `false`. Обрабатывает циклические структуры данных.

Применяется к одинаковым методам обоих аргументов, если они есть.

```javascript
R.equals(1, 1); //=> true
R.equals(1, '1'); //=> false
R.equals([1, 2, 3], [1, 2, 3]); //=> true

var a = {}; a.v = a;
var b = {}; b.v = b;
R.equals(a, b); //=> true
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;R.equals%281%2C%201%29%3B%20%2F%2F%3D%3E%20true%0AR.equals%281%2C%20%271%27%29%3B%20%2F%2F%3D%3E%20false%0AR.equals%28%5B1%2C%202%2C%203%5D%2C%20%5B1%2C%202%2C%203%5D%29%3B%20%2F%2F%3D%3E%20true%0A%0Avar%20a%20%3D%20%7B%7D%3B%20a.v%20%3D%20a%3B%0Avar%20b%20%3D%20%7B%7D%3B%20b.v%20%3D%20b%3B%0AR.equals%28a%2C%20b%29%3B%20%2F%2F%3D%3E%20true)

**[⬆ вверх](#Документация)**

## evolve
### `[Object]`

`{k: (v → v)} → {k: v} → {k: v}`

#### Параметры:
|||
:---|:---|
| transformations ||
| object | |
| вернет __Object__ ||

_Добавлено в версии v0.9.0_

Объект, определяющий функции преобразования, применяемые к объекту.

Функция не будет вызывана, если соответствующий ей ключ не существует в изменяемом объекте.

```javascript
var tomato  = {firstName: '  Tomato ', data: {elapsed: 100, remaining: 1400}, id:123};
var transformations = {
  firstName: R.trim,
  lastName: R.trim, // Не будет вызвано.
  data: {elapsed: R.add(1), remaining: R.add(-1)}
};
R.evolve(transformations, tomato); //=> {firstName: 'Tomato', data: {elapsed: 101, remaining: 1399}, id:123}
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;var%20tomato%20%20%3D%20%7BfirstName%3A%20%27%20%20Tomato%20%27%2C%20data%3A%20%7Belapsed%3A%20100%2C%20remaining%3A%201400%7D%2C%20id%3A123%7D%3B%0Avar%20transformations%20%3D%20%7B%0A%20%20firstName%3A%20R.trim%2C%0A%20%20lastName%3A%20R.trim%2C%20%2F%2F%20Will%20not%20get%20invoked.%0A%20%20data%3A%20%7Belapsed%3A%20R.add%281%29%2C%20remaining%3A%20R.add%28-1%29%7D%0A%7D%3B%0AR.evolve%28transformations%2C%20tomato%29%3B%20%2F%2F%3D%3E%20%7BfirstName%3A%20%27Tomato%27%2C%20data%3A%20%7Belapsed%3A%20101%2C%20remaining%3A%201399%7D%2C%20id%3A123%7D)

**[⬆ вверх](#Документация)**

## F
### `[Function]`

`* → Boolean`

#### Параметры:
||
:---|
| вернет __Boolean__ |

_Добавлено в версии v0.9.0_

Функция, которая всегда возвращает `false`. Любые переданные параметры игнорируются.

Смотрите также [always](#always), [T](#t).

```javascript
R.F(); //=> false
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;R.F%28%29%3B%20%2F%2F%3D%3E%20false)

**[⬆ вверх](#Документация)**

## filter
### `[List]`

`Filterable f => (a → Boolean) → f a → f a`

#### Параметры:
|||
:---|:---|
|pred||
|filterable||
| вернет __Array__ | отфильтрованный |

_Добавлено в версии v0.1.0_

Фильтрует коллекцию и возвращает новую, того же типа, содержащую елементы удовлетворяющие условию заданного предиката. Это может быть объект или любой элемент, имеющий метод `filter`, например `Array`.

Отправляет в метод `filter` второй аргумент, если он есть.

Действует как `transducer`, если `transformer` задан в позиции списка.

Смотрите также [reject](#reject), [transduce](#transduce), [addIndex](#addIndex).

```javascript
var isEven = n => n % 2 === 0;

R.filter(isEven, [1, 2, 3, 4]); //=> [2, 4]

R.filter(isEven, {a: 1, b: 2, c: 3, d: 4}); //=> {b: 2, d: 4}

R.filter(isEven, '689'); //=> ["6", "8"]
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#?var%20isEven%20%3D%20n%20%3D%3E%20n%20%25%202%20%3D%3D%3D%200%3B%0A%0AR.filter%28isEven%2C%20%5B1%2C%202%2C%203%2C%204%5D%29%3B%20%2F%2F%3D%3E%20%5B2%2C%204%5D%0A%0AR.filter%28isEven%2C%20%7Ba%3A%201%2C%20b%3A%202%2C%20c%3A%203%2C%20d%3A%204%7D%29%3B%20%2F%2F%3D%3E%20%7Bb%3A%202%2C%20d%3A%204%7D%0A%0AR.filter%28isEven%2C%20%27689%27%29%3B%20%2F%2F%3D%3E%20%5B%226%22%2C%20%228%22%5D)

**[⬆ вверх](#Документация)**

## find
### `[List]`

`(a → Boolean) → [a] → a | undefined`

#### Параметры:
|||
:---|:---|
|fn|Функция предикат, используемая для определения подходящего элемента.|
|list|Массив для рассмотрения|
| вернет __Object__ | Элемент найден, или `undefined`. |

_Добавлено в версии v0.1.0_

Возвращает первый элемент списка, который соответствует предикату, или `undefined`, если элемент не найден.

Отправляет в метод `find` второй аргумент, если он присутствует.

Действует как `transducer`, если `transformer` задан в позиции списка.

Смотрите также [transduce](#transduce).

```javascript
var xs = [{a: 1}, {a: 2}, {a: 3}];
R.find(R.propEq('a', 2))(xs); //=> {a: 2}
R.find(R.propEq('a', 4))(xs); //=> undefined
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;var%20xs%20%3D%20%5B%7Ba%3A%201%7D%2C%20%7Ba%3A%202%7D%2C%20%7Ba%3A%203%7D%5D%3B%0AR.find%28R.propEq%28%27a%27%2C%202%29%29%28xs%29%3B%20%2F%2F%3D%3E%20%7Ba%3A%202%7D%0AR.find%28R.propEq%28%27a%27%2C%204%29%29%28xs%29%3B%20%2F%2F%3D%3E%20undefined)

**[⬆ вверх](#Документация)**

## findIndex
### `[List]`

`(a → Boolean) → [a] → Number`

#### Параметры:
|||
:---|:---|
|fn|Функция предикат, используемая для определения подходящего элемента.|
|list|Массив для рассмотрения|
| вернет __Number__ | Вернет индекс элемента, если он найден, иначе `-1`. |

_Добавлено в версии v0.1.1_

Возвращает первый элемент списка, который соответствует предикату, или `-1`, если элемент не найден.

Действует как `transducer`, если `transformer` задан в позиции списка.

Смотрите также [transduce](#transduce).

```javascript
var xs = [{a: 1}, {a: 2}, {a: 3}];
R.findIndex(R.propEq('a', 2))(xs); //=> 1
R.findIndex(R.propEq('a', 4))(xs); //=> -1
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;var%20xs%20%3D%20%5B%7Ba%3A%201%7D%2C%20%7Ba%3A%202%7D%2C%20%7Ba%3A%203%7D%5D%3B%0AR.findIndex%28R.propEq%28%27a%27%2C%202%29%29%28xs%29%3B%20%2F%2F%3D%3E%201%0AR.findIndex%28R.propEq%28%27a%27%2C%204%29%29%28xs%29%3B%20%2F%2F%3D%3E%20-1)

**[⬆ вверх](#Документация)**

## findLast
### `[List]`

`(a → Boolean) → [a] → a | undefined`

#### Параметры:
|||
:---|:---|
|fn|Функция предикат, используемая для определения подходящего элемента.|
|list|Массив для рассмотрения|
| вернет __Object__ | Вернет `Object`, если он найден, иначе `undefined`. |

_Добавлено в версии v0.1.1_

Возвращает последний элемент списка, в котором найдет соответствие предикату, или `undefined`, если соответствий не найдено.

Действует как `transducer`, если `transformer` задан в позиции списка.

Смотрите также [transduce](#transduce).

```javascript
var xs = [{a: 1, b: 0}, {a:1, b: 1}];
R.findLast(R.propEq('a', 1))(xs); //=> {a: 1, b: 1}
R.findLast(R.propEq('a', 4))(xs); //=> undefined
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;var%20xs%20%3D%20%5B%7Ba%3A%201%2C%20b%3A%200%7D%2C%20%7Ba%3A1%2C%20b%3A%201%7D%5D%3B%0AR.findLast%28R.propEq%28%27a%27%2C%201%29%29%28xs%29%3B%20%2F%2F%3D%3E%20%7Ba%3A%201%2C%20b%3A%201%7D%0AR.findLast%28R.propEq%28%27a%27%2C%204%29%29%28xs%29%3B%20%2F%2F%3D%3E%20undefined)

## findLastIndex
### `[List]`

`(a → Boolean) → [a] → Number`

#### Параметры:
|||
:---|:---|
|fn|Функция предикат, используемая для определения подходящего элемента.|
|list|Массив для рассмотрения|
| вернет __Number__ | Вернет индекс элемента, если он найден, иначе `-1`. |

_Добавлено в версии v0.1.1_

Возвращает индекс последнего, соответсвующего предикату элемента, или `-1`, если соответствий не найдено.

Действует как `transducer`, если `transformer` задан в позиции списка.

Смотрите также [transduce](#transduce).

```javascript
var xs = [{a: 1, b: 0}, {a:1, b: 1}];
R.findLastIndex(R.propEq('a', 1))(xs); //=> 1
R.findLastIndex(R.propEq('a', 4))(xs); //=> -1
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;var%20xs%20%3D%20%5B%7Ba%3A%201%2C%20b%3A%200%7D%2C%20%7Ba%3A1%2C%20b%3A%201%7D%5D%3B%0AR.findLastIndex%28R.propEq%28%27a%27%2C%201%29%29%28xs%29%3B%20%2F%2F%3D%3E%201%0AR.findLastIndex%28R.propEq%28%27a%27%2C%204%29%29%28xs%29%3B%20%2F%2F%3D%3E%20-1)

**[⬆ вверх](#Документация)**

## flatten
### `[List]`

`[a] → [b]`

#### Параметры:
|||
:---|:---|
|list|Массив для рассмотрения|
| вернет __Array__ | Вернет одномерный массив. |

_Добавлено в версии v0.1.0_

Вернет новый одномерный массив, со всеми элементами старого (включая элементы вложенных в него массивов).

Смотрите также [unnest](#unnest).

```javascript
R.flatten([1, 2, [3, 4], 5, [6, [7, 8, [9, [10, 11], 12]]]]);
//=> [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12]
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;R.flatten%28%5B1%2C%202%2C%20%5B3%2C%204%5D%2C%205%2C%20%5B6%2C%20%5B7%2C%208%2C%20%5B9%2C%20%5B10%2C%2011%5D%2C%2012%5D%5D%5D%5D%29%3B%0A%2F%2F%3D%3E%20%5B1%2C%202%2C%203%2C%204%2C%205%2C%206%2C%207%2C%208%2C%209%2C%2010%2C%2011%2C%2012%5D)

**[⬆ вверх](#Документация)**

## flip
### `[Function]`

`((a, b, c, …) → z) → (b → a → c → … → z)`

#### Параметры:
|||
:---|:---|
|fn|Функция вызываемая с измененным порядком первых двух аргументов|
| вернет __*__ | Вернет результат вычислений `fh`. |

_Добавлено в версии v0.1.0_

Вернет такую же функцию с измененным порядком первых двух аргументов.

```javascript
var mergeThree = (a, b, c) => [].concat(a, b, c);

mergeThree(1, 2, 3); //=> [1, 2, 3]

R.flip(mergeThree)(1, 2, 3); //=> [2, 1, 3]
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;var%20mergeThree%20%3D%20%28a%2C%20b%2C%20c%29%20%3D%3E%20%5B%5D.concat%28a%2C%20b%2C%20c%29%3B%0A%0AmergeThree%281%2C%202%2C%203%29%3B%20%2F%2F%3D%3E%20%5B1%2C%202%2C%203%5D%0A%0AR.flip%28mergeThree%29%281%2C%202%2C%203%29%3B%20%2F%2F%3D%3E%20%5B2%2C%201%2C%203%5D)

**[⬆ вверх](#Документация)**

## forEach
### `[List]`

`(a → *) → [a] → [a]`

#### Параметры:
|||
:---|:---|
|fn|Вызываемая функция, с одним аргументом `value` |
|list|Итерируемый массив|
| вернет __Array__ | Вернет оригинальный массив. |

_Добавлено в версии v0.1.1_

Итерируется по входящему массиву `list`, применяя функцию `fn` для каждого элемента.

`fn` принимает один аргумент: (`value`)

Примечание: `R.forEach` не пропускает удаленные или неназначенные индексы (разреженные массивы), в отличие от `Array.prototype.forEach`. Больше о поведении встроеного метода можно почитать тут: [https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach#Description](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/forEach#Description)

Так же в отличии от `Array.prototype.forEach`, `R.forEach` возвращает оригинальный массив. В некоторых библиотеках этот метод называется `each`.

Отправляет в метод `forEach` второй аргумент, если он присутствует.

Смотрите также [addIndex](#addIndex).

```javascript
var printXPlusFive = x => console.log(x + 5);
R.forEach(printXPlusFive, [1, 2, 3]); //=> [1, 2, 3]
// logs 6
// logs 7
// logs 8
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;var%20printXPlusFive%20%3D%20x%20%3D%3E%20console.log%28x%20%2B%205%29%3B%0AR.forEach%28printXPlusFive%2C%20%5B1%2C%202%2C%203%5D%29%3B%20%2F%2F%3D%3E%20%5B1%2C%202%2C%203%5D%0A%2F%2F%20logs%206%0A%2F%2F%20logs%207%0A%2F%2F%20logs%208)

**[⬆ вверх](#Документация)**

## forEachObjIndexed
### `[Object]`

`((a, String, StrMap a) → Any) → StrMap a → StrMap a`

#### Параметры:
|||
:---|:---|
|fn|Вызываемая функция, принимающая три аргумента `value`, `key`, `object` |
|obj|Итерируемый объект|
| вернет __Object__ | Вернет оригинальный объект. |

_Добавлено в версии v0.23.0_

Итерируется по входящему объекту `obj`, применяя функцию `fn` для каждого `key` и `value` в `object`.

`fn` принимает три аргумента: (`key`, `value`, `object`)

Смотрите также [addIndex](#addIndex).

```javascript
var printKeyConcatValue = (value, key) => console.log(key + ':' + value);
R.forEachObjIndexed(printKeyConcatValue, {x: 1, y: 2}); //=> {x: 1, y: 2}
// logs x:1
// logs y:2
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;var%20printKeyConcatValue%20%3D%20%28value%2C%20key%29%20%3D%3E%20console.log%28key%20%2B%20%27%3A%27%20%2B%20value%29%3B%0AR.forEachObjIndexed%28printKeyConcatValue%2C%20%7Bx%3A%201%2C%20y%3A%202%7D%29%3B%20%2F%2F%3D%3E%20%7Bx%3A%201%2C%20y%3A%202%7D%0A%2F%2F%20logs%20x%3A1%0A%2F%2F%20logs%20y%3A2)

**[⬆ вверх](#Документация)**

## fromPairs
### `[List]`

`[[k,v]] → {k: v}`

#### Параметры:
|||
:---|:---|
|pairs|Массив массивов из двух элементов которые будут `key` и `value` результирующего объекта |
| вернет __Object__ | Вернет объект с `key` и `value` равными значениям парных массивов. |

_Добавлено в версии v0.3.0_

Создаст новый объект из элементов массива `pairs`. Если в нескольких парах одинаковый `key` то в объект будет добалена последняя.

Смотрите также [toPairs](#toPairs), [pair](#pair).

```javascript
R.fromPairs([['a', 1], ['b', 2], ['c', 3]]); //=> {a: 1, b: 2, c: 3}
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.25.0#;R.fromPairs%28%5B%5B%27a%27%2C%201%5D%2C%20%5B%27b%27%2C%202%5D%2C%20%5B%27c%27%2C%203%5D%5D%29%3B%20%2F%2F%3D%3E%20%7Ba%3A%201%2C%20b%3A%202%2C%20c%3A%203%7D)

**[⬆ вверх](#Документация)**


## groupBy
### `[List]`

`(a → String) → [a] → {String: [a]}`

#### Параметры:
|||
:---|:---|
|fn|Функция :: a -> String |
|list|Массив |
| вернет __Object__ | Объект c ключами, сопоставленный с массивом элементов, которые произвели этот ключ при передаче в `fn`. |

_Добавлено в версии v0.1.0_

Разделяет список на вложенные списки, хранящиеся в объекте, на основе результата вызова функции возвращающей строку для каждого элемента и группы результатов в соответствии с возвращаемыми значениями.

Отправляет методу `groupBy` второй аргумента, если он есть.

Действует как `transducer`, если `transformer` задан в позиции списка.

Смотрите также [reduceBy](#reduceBy), [transduce](#transduce).

```javascript
const byGrade = R.groupBy(function(student) {
  const score = student.score;
  return score < 65 ? 'F' :
         score < 70 ? 'D' :
         score < 80 ? 'C' :
         score < 90 ? 'B' : 'A';
});
const students = [{name: 'Abby', score: 84},
                {name: 'Eddy', score: 58},
                // ...
                {name: 'Jack', score: 69}];
byGrade(students);
// {
//   'A': [{name: 'Dianne', score: 99}],
//   'B': [{name: 'Abby', score: 84}]
//   // ...,
//   'F': [{name: 'Eddy', score: 58}]
// }
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.26.0#;const%20byGrade%20%3D%20R.groupBy%28function%28student%29%20%7B%0A%20%20const%20score%20%3D%20student.score%3B%0A%20%20return%20score%20%3C%2065%20%3F%20%27F%27%20%3A%0A%20%20%20%20%20%20%20%20%20score%20%3C%2070%20%3F%20%27D%27%20%3A%0A%20%20%20%20%20%20%20%20%20score%20%3C%2080%20%3F%20%27C%27%20%3A%0A%20%20%20%20%20%20%20%20%20score%20%3C%2090%20%3F%20%27B%27%20%3A%20%27A%27%3B%0A%7D%29%3B%0Aconst%20students%20%3D%20%5B%7Bname%3A%20%27Abby%27%2C%20score%3A%2084%7D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7Bname%3A%20%27Eddy%27%2C%20score%3A%2058%7D%2C%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%2F%2F%20...%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7Bname%3A%20%27Jack%27%2C%20score%3A%2069%7D%5D%3B%0AbyGrade%28students%29%3B%0A%2F%2F%20%7B%0A%2F%2F%20%20%20%27A%27%3A%20%5B%7Bname%3A%20%27Dianne%27%2C%20score%3A%2099%7D%5D%2C%0A%2F%2F%20%20%20%27B%27%3A%20%5B%7Bname%3A%20%27Abby%27%2C%20score%3A%2084%7D%5D%0A%2F%2F%20%20%20%2F%2F%20...%2C%0A%2F%2F%20%20%20%27F%27%3A%20%5B%7Bname%3A%20%27Eddy%27%2C%20score%3A%2058%7D%5D%0A%2F%2F%20%7D)

**[⬆ вверх](#Документация)**

## groupWith
### `[List]`

`((a, a) → Boolean) → [a] → [[a]]`

#### Параметры:
|||
:---|:---|
|fn|Функция для определения того, должны ли два заданных (смежных) элемента быть в одной группе |
|list|Массив для группировки. Также принимает строку, которая будет рассматриваться как список символов. |
| вернет __List__ | Список, содержащий подсписки элементов, конкатенация которых равна исходному списку. |

_Добавлено в версии v0.21.0_

Принимает список и возвращает список списков, в которых все элементы подсписка удовлетворяются по взаимному сравнению в соответствии с предоставленной функцией. Только соседние элементы передаются в функцию сравнения.

```javascript
R.groupWith(R.equals, [0, 1, 1, 2, 3, 5, 8, 13, 21])
//=> [[0], [1, 1], [2], [3], [5], [8], [13], [21]]

R.groupWith((a, b) => a + 1 === b, [0, 1, 1, 2, 3, 5, 8, 13, 21])
//=> [[0, 1], [1, 2, 3], [5], [8], [13], [21]]

R.groupWith((a, b) => a % 2 === b % 2, [0, 1, 1, 2, 3, 5, 8, 13, 21])
//=> [[0], [1, 1], [2], [3, 5], [8], [13, 21]]

R.groupWith(R.eqBy(isVowel), 'aestiou')
//=> ['ae', 'st', 'iou']
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.26.0#;R.groupWith%28R.equals%2C%20%5B0%2C%201%2C%201%2C%202%2C%203%2C%205%2C%208%2C%2013%2C%2021%5D%29%0A%2F%2F%3D%3E%20%5B%5B0%5D%2C%20%5B1%2C%201%5D%2C%20%5B2%5D%2C%20%5B3%5D%2C%20%5B5%5D%2C%20%5B8%5D%2C%20%5B13%5D%2C%20%5B21%5D%5D%0A%0AR.groupWith%28%28a%2C%20b%29%20%3D%3E%20a%20%2B%201%20%3D%3D%3D%20b%2C%20%5B0%2C%201%2C%201%2C%202%2C%203%2C%205%2C%208%2C%2013%2C%2021%5D%29%0A%2F%2F%3D%3E%20%5B%5B0%2C%201%5D%2C%20%5B1%2C%202%2C%203%5D%2C%20%5B5%5D%2C%20%5B8%5D%2C%20%5B13%5D%2C%20%5B21%5D%5D%0A%0AR.groupWith%28%28a%2C%20b%29%20%3D%3E%20a%20%25%202%20%3D%3D%3D%20b%20%25%202%2C%20%5B0%2C%201%2C%201%2C%202%2C%203%2C%205%2C%208%2C%2013%2C%2021%5D%29%0A%2F%2F%3D%3E%20%5B%5B0%5D%2C%20%5B1%2C%201%5D%2C%20%5B2%5D%2C%20%5B3%2C%205%5D%2C%20%5B8%5D%2C%20%5B13%2C%2021%5D%5D%0A%0AR.groupWith%28R.eqBy%28isVowel%29%2C%20%27aestiou%27%29%0A%2F%2F%3D%3E%20%5B%27ae%27%2C%20%27st%27%2C%20%27iou%27%5D)

**[⬆ вверх](#Документация)**

## gt
### `[Relation]`

`Ord a => a → a → Boolean`

#### Параметры:
||
:---|
|a| 
|list|
| вернет __Boolean__ |

_Добавлено в версии v0.1.0_

Возвращает `true`, если первый аргумент больше второго, иначе `false`.

Смотрите также [it](#it).

```javascript
R.gt(2, 1); //=> true
R.gt(2, 2); //=> false
R.gt(2, 3); //=> false
R.gt('a', 'z'); //=> false
R.gt('z', 'a'); //=> true
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.26.0#;R.gt%282%2C%201%29%3B%20%2F%2F%3D%3E%20true%0AR.gt%282%2C%202%29%3B%20%2F%2F%3D%3E%20false%0AR.gt%282%2C%203%29%3B%20%2F%2F%3D%3E%20false%0AR.gt%28%27a%27%2C%20%27z%27%29%3B%20%2F%2F%3D%3E%20false%0AR.gt%28%27z%27%2C%20%27a%27%29%3B%20%2F%2F%3D%3E%20true)

**[⬆ вверх](#Документация)**

## gte
### `[Relation]`

`Ord a => a → a → Boolean`

#### Параметры:
||
:---|
|a| 
|list|
| вернет __Boolean__ |

_Добавлено в версии v0.1.0_

Возвращает `true`, если первый аргумент больше или равен второму, иначе `false`.

Смотрите также [ite](#ite).

```javascript
R.gte(2, 1); //=> true
R.gte(2, 2); //=> true
R.gte(2, 3); //=> false
R.gte('a', 'z'); //=> false
R.gte('z', 'a'); //=> true
```
Попробуйте в [REPL](https://ramdajs.com/repl/?v=0.26.0#;R.gte%282%2C%201%29%3B%20%2F%2F%3D%3E%20true%0AR.gte%282%2C%202%29%3B%20%2F%2F%3D%3E%20true%0AR.gte%282%2C%203%29%3B%20%2F%2F%3D%3E%20false%0AR.gte%28%27a%27%2C%20%27z%27%29%3B%20%2F%2F%3D%3E%20false%0AR.gte%28%27z%27%2C%20%27a%27%29%3B%20%2F%2F%3D%3E%20true)

**[⬆ вверх](#Документация)**







## identity
### `[Function]`

`a → a`

#### Параметры:
|||
:---|:---|
| x | Возвращаемое значение |
| вернет __*__ | Введенное значение `x` |

_Добавлено в версии v0.1.0_

Функция, которая ничего не делает, но вернет переданный в нее аргумент. Хорошо подходит, чтобы быть функцией по умолчанию или функцией-заполнителем.

```javascript
R.identity(1); //=> 1

var obj = {};
R.identity(obj) obj; //=> true
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#?R.identity%281%29%3B%20%2F%2F%3D%3E%201%0A%0Avar%20obj%20%3D%20%7B%7D%3B%0AR.identity%28obj%29%20%3D%3D%3D%20obj%3B%20%2F%2F%3D%3E%20true)

**[⬆ вверх](#Документация)**



## into
### `[List]`

`a → (b → b) → [c] → a`

#### Параметры:
|||
:---|:---|
| acc | Аккумулятор. Начальное значеие. |
| xf | Функция-преобразователь. Получает и возвращает трансформер. |
| list | Список. |
| вернет __*__ | Окончательное накопленное значение |

_Добавлено в версии v0.12.0_

Изменяет элементы списка с помощью преобразователя и добавляет преобразованные элементы в аккумулятор, используя соответствующую функцию итератор, основанную на типе аккумулятора.

Аккумулятор может быть массивом, строкой, объектом или трансформатором. Итерированные элементы будут добавлены в массивы и объединены со строками. Объекты будут смержены, массивы из 2 элементов будут смержены как пары ключ - значение.

Аккумулятор может также быть объектом-трансформером, который обеспечит бинарность (2-арность) сокращение функции-итератора, шаг (step), нулярнисть (0-арность) начального значения функций, Инит (init) и унарнисть (1 - арность) результата извлечениыя функции `result`. Функция `step` используется в качестве итератора в `reduce`. Функция `result` используется для преобразования аккумулятора в возвращаемый тип и в большинстве случаев является `R.identity`. Функция `init` используется для составления начального аккумулятора.

Итерации выполняются с помощью `R.reduce` после инициализации преобразователя (transducer).

```javascript
var numbers = [1, 2, 3, 4];
var transducer = R.compose(R.map(R.add(1)), R.take(2));

R.into([], transducer, numbers); //=> [2, 3]

var intoArray = R.into([]);
intoArray(transducer, numbers); //=> [2, 3]
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.24.1#?var%20numbers%20%3D%20%5B1%2C%202%2C%203%2C%204%5D%3B%0Avar%20transducer%20%3D%20R.compose%28R.map%28R.add%281%29%29%2C%20R.take%282%29%29%3B%0A%0AR.into%28%5B%5D%2C%20transducer%2C%20numbers%29%3B%20%2F%2F%3D%3E%20%5B2%2C%203%5D%0A%0Avar%20intoArray%20%3D%20R.into%28%5B%5D%29%3B%0AintoArray%28transducer%2C%20numbers%29%3B%20%2F%2F%3D%3E%20%5B2%2C%203%5D)

**[⬆ вверх](#Документация)**



## map
### `[List]`

`Functor f => (a → b) → f a → f b`

#### Параметры:
|||
:---|:---|
| fn | Фунция, которая должна быть вызвана по отношению к каждому элементу из списка (`list`). |
| list | Итерируемый список. |
| вернет __Array__ | Новый список. |

_Добавлено в версии v0.1.0_

Принимает функцию и функтор, применяет функцию к каждому значению в функторе и вернет функтор такой же формы.

Ramda предоставляет удобную реализацию `map` для` Array` и `Object`, поэтому эта Функция может быть применена как к `[1, 2, 3] `, так и к `{x 1, y 2, z 3 }`.

Отправляет в метод `map` второй аргумент, если он есть.

Ведет себя как трансдьюсер (`transducer`), если` transformer` передан вместо списка.

Также воспринимает функции как функторы и сделает из них композицию.

Смотрите также [transduce](#transduce), [addIndex](#addindex).

```javascript
var double = x => x * 2;

R.map(double, [1, 2, 3]); //=> [2, 4, 6]

R.map(double, {x: 1, y: 2, z: 3}); //=> {x: 2, y: 4, z: 6}
```
Попробуйте в [REPL](http://ramdajs.com/repl/?v=0.25.0#?var%20double%20%3D%20x%20%3D%3E%20x%20%2A%202%3B%0A%0AR.map%28double%2C%20%5B1%2C%202%2C%203%5D%29%3B%20%2F%2F%3D%3E%20%5B2%2C%204%2C%206%5D%0A%0AR.map%28double%2C%20%7Bx%3A%201%2C%20y%3A%202%2C%20z%3A%203%7D%29%3B%20%2F%2F%3D%3E%20%7Bx%3A%202%2C%20y%3A%204%2C%20z%3A%206%7D)

**[⬆ вверх](#Документация)**
