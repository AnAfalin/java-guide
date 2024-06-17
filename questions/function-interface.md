#### [Оглавление](../README.md)

# Функциональные интерфейсы
+ [Что такое «функциональные интерфейсы»?](#что-такое-функциональные-интерфейсы)
+ [Для чего нужны функциональные интерфейсы `Function<T,R>`, `DoubleFunction<R>`, `IntFunction<R>` и `LongFunction<R>`?](#для-чего-нужны-функциональные-интерфейсы-functiontr--doublefunctionr--intfunctionr-и-longfunctionr-)
+ [Для чего нужны функциональные интерфейсы `UnaryOperator<T>`, `DoubleUnaryOperator`, `IntUnaryOperator` и `LongUnaryOperator`?](#для-чего-нужны-функциональные-интерфейсы-unaryoperatort--doubleunaryoperator--intunaryoperator-и-longunaryoperator-)
+ [Для чего нужны функциональные интерфейсы `BinaryOperator<T>`, `DoubleBinaryOperator`, `IntBinaryOperator` и `LongBinaryOperator`?](#для-чего-нужны-функциональные-интерфейсы-binaryoperatort--doublebinaryoperator--intbinaryoperator-и-longbinaryoperator-)
+ [Для чего нужны функциональные интерфейсы `Predicate<T>`, `DoublePredicate`, `IntPredicate` и `LongPredicate`?](#для-чего-нужны-функциональные-интерфейсы-predicatet--doublepredicate--intpredicate-и-longpredicate-)
+ [Для чего нужны функциональные интерфейсы `Consumer<T>`, `DoubleConsumer`, `IntConsumer` и `LongConsumer`?](#для-чего-нужны-функциональные-интерфейсы-consumert--doubleconsumer--intconsumer-и-longconsumer-)
+ [Для чего нужны функциональные интерфейсы `Supplier<T>`,  `BooleanSupplier`, `DoubleSupplier`, `IntSupplier` и `LongSupplier`?](#для-чего-нужны-функциональные-интерфейсы-suppliert--booleansupplier--doublesupplier--intsupplier-и-longsupplier-)
+ [Для чего нужен функциональный интерфейс `BiConsumer<T,U>`?](#для-чего-нужен-функциональный-интерфейс-biconsumertu-)
+ [Для чего нужен функциональный интерфейс `BiFunction<T,U,R>`?](#для-чего-нужен-функциональный-интерфейс-bifunctiontur-)
+ [Для чего нужен функциональный интерфейс `BiPredicate<T,U>`?](#для-чего-нужен-функциональный-интерфейс-bipredicatetu-)
+ [Для чего нужны функциональные интерфейсы вида `_To_Function`?](#для-чего-нужны-функциональные-интерфейсы-вида-tofunction-)
+ [Для чего нужны функциональные интерфейсы `ToDoubleBiFunction<T,U>`, `ToIntBiFunction<T,U>` и `ToLongBiFunction<T,U>`?](#для-чего-нужны-функциональные-интерфейсы-todoublebifunctiontu--tointbifunctiontu-и-tolongbifunctiontu-)
+ [Для чего нужны функциональные интерфейсы `ToDoubleFunction<T>`, `ToIntFunction<T>` и `ToLongFunction<T>`?](#для-чего-нужны-функциональные-интерфейсы-todoublefunctiont--tointfunctiont-и-tolongfunctiont-)
+ [Для чего нужны функциональные интерфейсы `ObjDoubleConsumer<T>`, `ObjIntConsumer<T>` и `ObjLongConsumer<T>`?](#для-чего-нужны-функциональные-интерфейсы-objdoubleconsumert--objintconsumert-и-objlongconsumert-)

_______________________________________________________________________________________________________________________
<span style="display: inline-block; float: right">[содержание](#функциональные-интерфейсы)</span>

## Что такое «функциональные интерфейсы»?
__Функциональный интерфейс__ - это интерфейс, который определяет только один абстрактный метод.

Чтобы точно определить интерфейс как функциональный, добавлена аннотация `@FunctionalInterface`, работающая по принципу `@Override`. Она обозначит замысел и не даст определить второй абстрактный метод в интерфейсе.

Интерфейс может включать сколько угодно `default` методов и при этом оставаться функциональным, потому что `default` методы - не абстрактные.
_______________________________________________________________________________________________________________________
<span style="display: inline-block; float: right">[содержание](#функциональные-интерфейсы)</span>

## Для чего нужны функциональные интерфейсы `Function<T,R>`, `DoubleFunction<R>`, `IntFunction<R>` и `LongFunction<R>`?

__`Function<T, R>`__ - интерфейс, с помощью которого реализуется функция, получающая на вход экземпляр класса `T` и возвращающая на выходе экземпляр класса `R`.

Методы по умолчанию могут использоваться для построения цепочек вызовов (`compose`, `andThen`).

```java
Function<String, Integer> toInteger = Integer::valueOf;
Function<String, String> backToString = toInteger.andThen(String::valueOf);
backToString.apply("123");     // "123"
```

+ `DoubleFunction<R>` - функция, получающая на вход `Double` и возвращающая на выходе экземпляр класса `R`;
+ `IntFunction<R>` - функция, получающая на вход `Integer` и возвращающая на выходе экземпляр класса `R`;
+ `LongFunction<R>` - функция, получающая на вход `Long` и возвращающая на выходе экземпляр класса `R`.
_______________________________________________________________________________________________________________________
<span style="display: inline-block; float: right">[содержание](#функциональные-интерфейсы)</span>

## Для чего нужны функциональные интерфейсы `UnaryOperator<T>`, `DoubleUnaryOperator`, `IntUnaryOperator` и `LongUnaryOperator`?

__`UnaryOperator<T>` (унарный оператор)__ принимает в качестве параметра объект типа `T`, выполняет над ними операции и возвращает результат операций в виде объекта типа `T`:

```java
UnaryOperator<Integer> operator = x -> x * x;
System.out.println(operator.apply(5)); // 25
```

+ `DoubleUnaryOperator` - унарный оператор, получающий на вход `Double`;
+ `IntUnaryOperator` - унарный оператор, получающий на вход `Integer`;
+ `LongUnaryOperator` - унарный оператор, получающий на вход `Long`.
_______________________________________________________________________________________________________________________
<span style="display: inline-block; float: right">[содержание](#функциональные-интерфейсы)</span>

## Для чего нужны функциональные интерфейсы `BinaryOperator<T>`, `DoubleBinaryOperator`, `IntBinaryOperator` и `LongBinaryOperator`?

__`BinaryOperator<T>` (бинарный оператор)__ - интерфейс, с помощью которого реализуется функция, получающая на вход два экземпляра класса `T` и возвращающая на выходе экземпляр класса `T`.
```java
BinaryOperator<Integer> operator = (a, b) -> a + b;
System.out.println(operator.apply(1, 2)); // 3
```

+ `DoubleBinaryOperator` - бинарный оператор, получающий на вход `Double`;
+ `IntBinaryOperator` - бинарный оператор, получающий на вход `Integer`;
+ `LongBinaryOperator` - бинарный оператор, получающий на вход `Long`.
_______________________________________________________________________________________________________________________
<span style="display: inline-block; float: right">[содержание](#функциональные-интерфейсы)</span>

## Для чего нужны функциональные интерфейсы `Predicate<T>`, `DoublePredicate`, `IntPredicate` и `LongPredicate`?

__`Predicate<T>` (предикат)__ - интерфейс, с помощью которого реализуется функция, получающая на вход экземпляр класса `T` и возвращающая на выходе значение типа `boolean`.

Интерфейс содержит различные методы по умолчанию, позволяющие строить сложные условия (`and`, `or`, `negate`).

```java
Predicate<String> predicate = (s) -> s.length() > 0;
predicate.test("foo"); // true
predicate.negate().test("foo"); // false
```

+ `DoublePredicate` - предикат, получающий на вход `Double`;
+ `IntPredicate` - предикат, получающий на вход `Integer`;
+ `LongPredicate` - предикат, получающий на вход `Long`.
_______________________________________________________________________________________________________________________
<span style="display: inline-block; float: right">[содержание](#функциональные-интерфейсы)</span>

## Для чего нужны функциональные интерфейсы `Consumer<T>`, `DoubleConsumer`, `IntConsumer` и `LongConsumer`?

__`Consumer<T>` (потребитель)__ - интерфейс, с помощью которого реализуется функция, которая получает на вход экземпляр 
класса `T`, производит с ним некоторое действие и ничего не возвращает.

```java
Consumer<String> hello = (name) -> System.out.println("Hello, " + name);
hello.accept("world");
```

+ `DoubleConsumer` - потребитель, получающий на вход `Double`;
+ `IntConsumer` - потребитель, получающий на вход `Integer`;
+ `LongConsumer` - потребитель, получающий на вход `Long`.
_______________________________________________________________________________________________________________________
<span style="display: inline-block; float: right">[содержание](#функциональные-интерфейсы)</span>

## Для чего нужны функциональные интерфейсы `Supplier<T>`,  `BooleanSupplier`, `DoubleSupplier`, `IntSupplier` и `LongSupplier`?

__`Supplier<T>` (поставщик)__ - интерфейс, с помощью которого реализуется функция, ничего не принимающая на вход, но 
возвращающая на выход результат класса `T`;

```java
Supplier<LocalDateTime> now = LocalDateTime::now;
now.get();
```

+ `DoubleSupplier` - поставщик, возвращающий `Double`;
+ `IntSupplier` - поставщик, возвращающий `Integer`;
+ `LongSupplier` - поставщик, возвращающий `Long`.
_______________________________________________________________________________________________________________________
<span style="display: inline-block; float: right">[содержание](#функциональные-интерфейсы)</span>

## Для чего нужен функциональный интерфейс `BiConsumer<T,U>`?

__`BiConsumer<T,U>`__ представляет собой операцию, которая принимает два аргумента классов `T` и `U` производит с ними
некоторое действие и ничего не возвращает.
_______________________________________________________________________________________________________________________
<span style="display: inline-block; float: right">[содержание](#функциональные-интерфейсы)</span>

## Для чего нужен функциональный интерфейс `BiFunction<T,U,R>`?

__`BiFunction<T,U,R>`__ представляет собой операцию, которая принимает два аргумента классов `T` и `U` и возвращающая 
результат класса `R`.
_______________________________________________________________________________________________________________________
<span style="display: inline-block; float: right">[содержание](#функциональные-интерфейсы)</span>

## Для чего нужен функциональный интерфейс `BiPredicate<T,U>`?

__`BiPredicate<T,U>`__ представляет собой операцию, которая принимает два аргумента классов `T` и `U` и возвращающая 
результат типа `boolean`.
_______________________________________________________________________________________________________________________
<span style="display: inline-block; float: right">[содержание](#функциональные-интерфейсы)</span>

## Для чего нужны функциональные интерфейсы вида `_To_Function`?

+ `DoubleToIntFunction` - операция, принимающая аргумент класса `Double` и возвращающая результат типа `Integer`;
+ `DoubleToLongFunction` - операция, принимающая аргумент класса `Double` и возвращающая результат типа `Long`;
+ `IntToDoubleFunction` - операция, принимающая аргумент класса `Integer` и возвращающая результат типа `Double`;
+ `IntToLongFunction` - операция, принимающая аргумент класса `Integer` и возвращающая результат типа `Long`;
+ `LongToDoubleFunction` - операция, принимающая аргумент класса `Long` и возвращающая результат типа `Double`;
+ `LongToIntFunction` - операция, принимающая аргумент класса `Long` и возвращающая результат типа `Integer`.
_______________________________________________________________________________________________________________________
<span style="display: inline-block; float: right">[содержание](#функциональные-интерфейсы)</span>

## Для чего нужны функциональные интерфейсы `ToDoubleBiFunction<T,U>`, `ToIntBiFunction<T,U>` и `ToLongBiFunction<T,U>`?

+ `ToDoubleBiFunction<T,U>` - операция принимающая два аргумента классов `T` и `U` и возвращающая результат типа `Double`;
+ `ToLongBiFunction<T,U>` - операция принимающая два аргумента классов `T` и `U` и возвращающая результат типа `Long`;
+ `ToIntBiFunction<T,U>`  - операция принимающая два аргумента классов `T` и `U` и возвращающая результат типа `Integer`.
_______________________________________________________________________________________________________________________
<span style="display: inline-block; float: right">[содержание](#функциональные-интерфейсы)</span>

## Для чего нужны функциональные интерфейсы `ToDoubleFunction<T>`, `ToIntFunction<T>` и `ToLongFunction<T>`?

+ `ToDoubleFunction<T>` - операция, принимающая аргумент класса `T` и возвращающая результат типа `Double`;
+ `ToLongFunction<T>` - операция, принимающая аргумент класса `T` и возвращающая результат типа `Long`;
+ `ToIntFunction<T>` - операция, принимающая аргумент класса `T` и возвращающая результат типа `Integer`.
_______________________________________________________________________________________________________________________
<span style="display: inline-block; float: right">[содержание](#функциональные-интерфейсы)</span>

## Для чего нужны функциональные интерфейсы `ObjDoubleConsumer<T>`, `ObjIntConsumer<T>` и `ObjLongConsumer<T>`?

+ `ObjDoubleConsumer<T>` - операция, которая принимает два аргумента классов `T` и `Double`, производит с ними некоторое 
действие и ничего не возвращает;
+ `ObjLongConsumer<T>` - операция, которая принимает два аргумента классов `T` и `Long`, производит с ними некоторое 
действие и ничего не возвращает;
+ `ObjIntConsumer<T>` - операция, которая принимает два аргумента классов `T` и `Integer`, производит с ними некоторое
действие и ничего не возвращает.
