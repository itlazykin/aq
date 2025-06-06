## ImmutableCollections

[1. Что такое immutable (неизменяемые) коллекции в Java?](#1-что-такое-immutable-неизменяемые-коллекции-в-java)

[2. Как можно создать immutable список в Java?](#2-как-можно-создать-immutable-список-в-java)

[3. Перечислите преимущества использования immutable коллекций.](#3-перечислите-преимущества-использования-immutable-коллекций)

[4. Какие основные отличия между Collections.unmodifiableCollection и Collections.immutableCollection в Java?](#4-какие-основные-отличия-между-collectionsunmodifiablecollection-и-collectionsimmutablecollection-в-java)

[5. Как использовать метод Collectors.toUnmodifiableList() при работе со Stream API?](#5-как-использовать-метод-collectorstounmodifiablelist-при-работе-со-stream-api)

[6. Каковы особенности работы с immutable коллекциями в многопоточной среде?](#6-каковы-особенности-работы-с-immutable-коллекциями-в-многопоточной-среде)

[7. Какие нововведения связанные с immutable коллекциями были введены в Java 9?](#7-какие-нововведения-связанные-с-immutable-коллекциями-были-введены-в-java-9)

[8. Как реализовать свою immutable коллекцию в Java?](#8-как-реализовать-свою-immutable-коллекцию-в-java)

[9. Какие есть ограничения и недостатки при использовании immutable коллекций в Java?](#9-какие-есть-ограничения-и-недостатки-при-использовании-immutable-коллекций-в-java)

# 1. Что такое immutable (неизменяемые) коллекции в Java?

Immutable коллекции — это коллекции, которые нельзя изменить после их создания.

[К оглавлению](#ImmutableCollections)

# 2. Как можно создать immutable список в Java?

- Фабричный метод `List.of()`
- Использование Collections.unmodifiableList()

[К оглавлению](#ImmutableCollections)

# 3. Перечислите преимущества использования immutable коллекций.

Преимущества immutable коллекций включают безопасность данных, потокобезопасность, упрощение тестирования,
предсказуемость поведения, возможность оптимизации и улучшение чистоты кода.

[К оглавлению](#ImmutableCollections)

# 4. Какие основные отличия между Collections.unmodifiableCollection и Collections.immutableCollection в Java?

Основное отличие между Collections.unmodifiableCollection и ImmutableCollection заключается в том, что
unmodifiableCollection — это обертка над коллекцией, которая не позволяет изменять её через публичный интерфейс, но
изменения в оригинальной коллекции могут повлиять на обертку. В то время как ImmutableCollection из библиотеки Guava —
это настоящая неизменяемая коллекция, которая не позволяет изменять данные после создания.

[К оглавлению](#ImmutableCollections)

# 5. Как использовать метод Collectors.toUnmodifiableList() при работе со Stream API?

Метод Collectors.toUnmodifiableList() используется для сбора элементов потока в неизменяемый список. Он гарантирует, что список не может быть изменен после его создания, и любая попытка модификации вызовет исключение UnsupportedOperationException.

```java
import java.util.List;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class Main {
    public static void main(String[] args) {
        List<String> unmodifiableList = Stream.of("apple", "banana", "cherry")
                .filter(fruit -> fruit.startsWith("a"))
                .collect(Collectors.toUnmodifiableList());

        System.out.println(unmodifiableList);  // Выведет: [apple]
        
        // Попытка изменения списка вызовет UnsupportedOperationException
        // unmodifiableList.add("orange"); // Ошибка! UnsupportedOperationException
    }
}

```

[К оглавлению](#ImmutableCollections)

# 6. Каковы особенности работы с immutable коллекциями в многопоточной среде?

Immutable коллекции являются потокобезопасными, потому что их состояние не может изменяться после создания, что исключает необходимость в синхронизации и блокировках. Они позволяют безопасно читать данные нескольким потокам одновременно и устраняют проблемы с состоянием гонки.

[К оглавлению](#ImmutableCollections)

# 7. Какие нововведения связанные с immutable коллекциями были введены в Java 9?

В Java 9 были добавлены новые методы для создания неизменяемых коллекций, такие как List.of(), Set.of(), Map.of(), Map.ofEntries(). Эти методы упрощают создание коллекций, которые нельзя изменять после их создания, и обеспечивают более высокую безопасность данных и улучшенную производительность.

[К оглавлению](#ImmutableCollections)

# 8. Как реализовать свою immutable коллекцию в Java?

Для создания собственной immutable коллекции в Java нужно использовать подходы, которые исключают возможность изменения её состояния после создания. Это можно достичь, используя такие механизмы, как Collections.unmodifiableList() или Arrays.asList(). Важно также гарантировать, чтобы все внутренние данные коллекции не могли быть изменены после её создания.

```java
import java.util.Arrays;
import java.util.Collections;
import java.util.List;

public class ImmutableList<T> {
    private final List<T> list;

    // Конструктор, принимающий коллекцию элементов
    public ImmutableList(List<T> inputList) {
        // Создаем неизменяемый список, передавая в него копию исходного списка
        this.list = Collections.unmodifiableList(Arrays.asList(inputList.toArray()));
    }

    // Метод для получения элемента по индексу
    public T get(int index) {
        return list.get(index);
    }

    // Метод для получения размера коллекции
    public int size() {
        return list.size();
    }

    // Метод для получения коллекции (с неизменяемым доступом)
    public List<T> getList() {
        return list;
    }

    // Пример использования
    public static void main(String[] args) {
        List<String> data = List.of("apple", "banana", "cherry");
        ImmutableList<String> immutableList = new ImmutableList<>(data);

        System.out.println(immutableList.get(0));  // Выведет: apple
        System.out.println("Size: " + immutableList.size());  // Выведет: Size: 3

        // Попытка изменения коллекции вызовет исключение
        // immutableList.getList().add("orange"); // UnsupportedOperationException
    }
}

```

[К оглавлению](#ImmutableCollections)

# 9. Какие есть ограничения и недостатки при использовании immutable коллекций в Java?

Основные недостатки immutable коллекций включают невозможность изменения содержимого коллекции после её создания, что
может привести к накладным расходам на память и производительность при частых изменениях. Также они не поддерживают null
элементы, и могут быть неэффективными, если требуется частое изменение данных.

[К оглавлению](#ImmutableCollections)