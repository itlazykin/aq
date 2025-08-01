## FULambda

[1. Что такое лямбда-выражение в Java?](#1-что-такое-лямбда-выражение-в-java)

[2. Какие преимущества лямбда-выражений вы можете назвать?](#2-какие-преимущества-лямбда-выражений-вы-можете-назвать)

[3. Что такое функциональный интерфейс в Java?](#3-что-такое-функциональный-интерфейс-в-java)

[4. Сколько абстрактных методов может быть в функциональном интерфейсе?](#4-сколько-абстрактных-методов-может-быть-в-функциональном-интерфейсе)

[5. Может ли лямбда-выражение изменить значение локальной переменной?](#5-может-ли-лямбда-выражение-изменить-значение-локальной-переменной)

[6. Что такое ссылка на метод?](#6-что-такое-ссылка-на-метод)

[7. Каковы основные характеристики функционального интерфейса в Java?](#7-каковы-основные-характеристики-функционального-интерфейса-в-java)

[8. Какие преимущества и недостатки использования лямбда выражений по сравнению с анонимными классами?](#8-какие-преимущества-и-недостатки-использования-лямбда-выражений-по-сравнению-с-анонимными-классами)

[9. Как можно использовать лямбда выражения для реализации функциональных интерфейсов?](#9-как-можно-использовать-лямбда-выражения-для-реализации-функциональных-интерфейсов)

[10. Что происходит при захвате переменной из внешнего контекста внутри лямбда-выражения?](#10-что-происходит-при-захвате-переменной-из-внешнего-контекста-внутри-лямбда-выражения)

[11. Как использовать лямбда-выражение для сортировки списка строк в обратном порядке с помощью Comparator?](#11-как-использовать-лямбда-выражение-для-сортировки-списка-строк-в-обратном-порядке-с-помощью-comparator)

[12. Какие стратегии и подходы используются для оптимизации производительности при работе с лямбда выражениями и потоками?](#12-какие-стратегии-и-подходы-используются-для-оптимизации-производительности-при-работе-с-лямбда-выражениями-и-потоками)

[13. Как можно создать собственный функциональный интерфейс в Java?](#13-как-можно-создать-собственный-функциональный-интерфейс-в-java)

[14. Какие есть способы обработки исключений в лямбда-выражениях и Stream API? Приведите пример.](#14-какие-есть-способы-обработки-исключений-в-лямбда-выражениях-и-stream-api-приведите-пример)

[15. Объясните различия между методами andThen и compose в интерфейсе Function.](#15-объясните-различия-между-методами-andthen-и-compose-в-интерфейсе-function)

# 1. Что такое лямбда-выражение в Java?

Лямбда-выражение в Java — это краткая запись анонимной функции, которая позволяет передавать поведение в виде параметра. Оно имеет форму (parameters) -> expression. Лямбда-выражения помогают уменьшить объем кода, улучшить его читаемость и поддерживают функциональный стиль программирования.

[К оглавлению](#FULambda)

# 2. Какие преимущества лямбда-выражений вы можете назвать?

Лямбда-выражения в Java предоставляют несколько преимуществ: они уменьшают объем кода, улучшают читаемость, поддерживают функциональный стиль программирования, позволяют передавать поведение как параметры

[К оглавлению](#FULambda)

# 3. Что такое функциональный интерфейс в Java?

Функциональный интерфейс – интерфейс с одним абстрактным методом. Помимо одного абстрактного, может содержать любое количество статических и дефолтных методов.

[К оглавлению](#FULambda)

# 4. Сколько абстрактных методов может быть в функциональном интерфейсе?

1

[К оглавлению](#FULambda)

# 5. Может ли лямбда-выражение изменить значение локальной переменной?

Лямбда-выражения в Java не могут изменять значение локальных переменных, которые находятся в области видимости метода, если эти переменные не являются финальными или эффективно финальными.

Это связано с тем, как лямбда-выражения обрабатываются компилятором. Лямбда-выражения могут быть выполнены в другом потоке или в другом контексте, и если лямбда-выражение изменяет переменные, это может привести к непредсказуемому поведению. Чтобы избежать подобных проблем, Java запрещает изменять локальные переменные из лямбд.

[К оглавлению](#FULambda)

# 6. Что такое ссылка на метод?

Ссылка на метод в Java — это механизм, позволяющий передавать метод как объект, используя синтаксис ClassName::methodName. Это сокращение для лямбда-выражений, которое улучшает читаемость и компактность кода. Ссылки на методы могут быть использованы для статических методов, методов экземпляров, а также для конструкторов.
[К оглавлению](#FULambda)

# 7. Каковы основные характеристики функционального интерфейса в Java?

Функциональный интерфейс в Java — это интерфейс, который имеет только один абстрактный метод. Он может содержать несколько методов по умолчанию или статических методов, но только один абстрактный метод. Аннотация @FunctionalInterface используется для явного указания, что интерфейс является функциональным, но не является обязательной. Функциональные интерфейсы идеально подходят для работы с лямбда-выражениями и часто используются в Java, например, в Stream API.

[К оглавлению](#FULambda)

# 8. Какие преимущества и недостатки использования лямбда выражений по сравнению с анонимными классами?

Лямбда-выражения позволяют сократить код, повысить его читаемость и упростить использование функционального стиля программирования, особенно с Stream API. Однако они не подходят для сложных случаев, где требуется больше гибкости, а также могут усложнить отладку из-за отсутствия имен. В таких случаях анонимные классы могут быть более подходящим выбором, так как они дают возможность использовать дополнительные методы и сохранять состояние.

[К оглавлению](#FULambda)

# 9. Как можно использовать лямбда выражения для реализации функциональных интерфейсов?

Лямбда-выражения используются для реализации функциональных интерфейсов, которые содержат только один абстрактный метод. Лямбда-выражение позволяет передать поведение в виде короткого, компактного выражения. Для функциональных интерфейсов можно использовать стандартные интерфейсы из пакета java.util.function, такие как Predicate, Function, Consumer, Supplier и другие.

[К оглавлению](#FULambda)

# 10. Что происходит при захвате переменной из внешнего контекста внутри лямбда-выражения?

При захвате переменной из внешнего контекста лямбда-выражение сохраняет ссылку на эту переменную. Локальные переменные, захваченные лямбдой, должны быть эффективно финальными, то есть их значения не могут изменяться после их инициализации. Это необходимо для обеспечения корректной работы лямбда-выражений, особенно в многозадачных приложениях, где изменяемые переменные могут привести к ошибкам или неожиданному поведению.

[К оглавлению](#FULambda)

# 11. Как использовать лямбда-выражение для сортировки списка строк в обратном порядке с помощью Comparator?

Для сортировки списка строк в обратном порядке с использованием лямбда-выражения и Comparator, можно использовать метод sort() списка и передать компаратор, который выполняет сравнение строк в обратном порядке. Это можно сделать с помощью Comparator.reverseOrder() или явного лямбда-выражения, например: (str1, str2) -> str2.compareTo(str1).

[К оглавлению](#FULambda)

# 12. Какие стратегии и подходы используются для оптимизации производительности при работе с лямбда выражениями и потоками?

Для оптимизации производительности при работе с лямбда-выражениями и потоками можно использовать следующие подходы: использовать параллельные потоки с осторожностью, избегать излишнего создания объектов, минимизировать количество промежуточных операций, использовать специализированные потоки для примитивных типов, а также выбирать правильные терминальные операции для минимизации затрат. Важно помнить о ленивой инициализации потоков и учитывать контекст, чтобы избежать лишних затрат в многозадачных приложениях.

[К оглавлению](#FULambda)

# 13. Как можно создать собственный функциональный интерфейс в Java?

Для создания собственного функционального интерфейса в Java нужно объявить интерфейс с одним абстрактным методом, который будет реализовываться лямбда-выражением. Для этого можно использовать аннотацию @FunctionalInterface, хотя она не обязательна, но помогает гарантировать, что интерфейс содержит только один абстрактный метод. Интерфейс может также содержать дефолтные и статические методы, но это не влияет на его функциональность.

```java
функциональный интерфейс, который будет представлять операцию над двумя числами.

@FunctionalInterface
public interface Operation {
    // Абстрактный метод
    int apply(int a, int b);
    
    // Опциональный дефолтный метод
    default int add(int a, int b) {
        return a + b;
    }

    // Опциональный статический метод
    static int multiply(int a, int b) {
        return a * b;
    }
}
```

[К оглавлению](#FULambda)

# 14. Какие есть способы обработки исключений в лямбда-выражениях и Stream API? Приведите пример.

Для обработки исключений в лямбда-выражениях и Stream API можно использовать несколько подходов. Один из них — обернуть проверяемые исключения в непроверяемые (RuntimeException). Также можно создать вспомогательные методы для ловли исключений или использовать try-catch внутри лямбды. Для более сложных случаев можно использовать библиотеки, такие как Vavr, которые предоставляют удобные инструменты для работы с исключениями.

[К оглавлению](#FULambda)

# 15. Объясните различия между методами andThen и compose в интерфейсе Function.

Методы andThen() и compose() в интерфейсе Function позволяют комбинировать функции, но делают это в разном порядке. andThen() применяет переданную функцию после текущей, а compose() — до текущей функции. Это влияет на порядок применения функций и, следовательно, на результат.

[К оглавлению](#FULambda)