# Java и его приложения

## 1. Характеристики простых типов данных. Операции, выражения, правила приведения типов.

### Простые типы данных в Java
Java предоставляет 8 примитивных типов данных:

**Целочисленные типы:**
- `byte`: 8 бит, -128 до 127
- `short`: 16 бит, -32,768 до 32,767
- `int`: 32 бита, -2^31 до 2^31-1
- `long`: 64 бита, -2^63 до 2^63-1

**Типы с плавающей точкой:**
- `float`: 32 бита, одинарная точность
- `double`: 64 бита, двойная точность

**Символьный тип:**
- `char`: 16 бит, Unicode символы

**Логический тип:**
- `boolean`: `true` или `false`

### Операции и выражения
Java поддерживает следующие группы операций:

**Арифметические операции:**
- Сложение: `+`
- Вычитание: `-`
- Умножение: `*`
- Деление: `/`
- Остаток от деления: `%`
- Инкремент: `++`
- Декремент: `--`

**Операции сравнения:**
- Равно: `==`
- Не равно: `!=`
- Больше: `>`
- Меньше: `<`
- Больше или равно: `>=`
- Меньше или равно: `<=`

**Логические операции:**
- И: `&&`
- ИЛИ: `||`
- НЕ: `!`

**Побитовые операции:**
- И: `&`
- ИЛИ: `|`
- Исключающее ИЛИ: `^`
- Дополнение: `~`
- Сдвиг влево: `<<`
- Сдвиг вправо: `>>`
- Беззнаковый сдвиг вправо: `>>>`

### Правила приведения типов
В Java существует два вида приведения типов:

**Автоматическое расширяющее приведение** (неявное):
```
byte → short → int → long → float → double
           ↑
          char
```

**Сужающее приведение** (требует явного указания):
```java
int a = 100;
byte b = (byte)a; // Явное приведение необходимо
```

**Особенности приведения:**
- Приведение примитивных типов к объектным требует автоупаковки
- Приведение между несовместимыми объектными типами требует проверки `instanceof`
- При преобразовании числовых типов возможна потеря точности или переполнение

## 2. Операторы. Блок операторов. Управляющие операторы. Операторы перехода.

### Блок операторов
Блок операторов в Java — группа операторов, заключенных в фигурные скобки:
```java
{
    int x = 10;
    System.out.println(x);
    x++;
}
```

### Управляющие операторы

**Условные операторы:**
```java
// if-else
if (условие) {
    // блок кода
} else if (условие2) {
    // блок кода
} else {
    // блок кода
}

// switch
switch (выражение) {
    case значение1:
        // операторы
        break;
    case значение2:
        // операторы
        break;
    default:
        // операторы
}
```

**Циклы:**
```java
// for
for (инициализация; условие; шаг) {
    // блок кода
}

// while
while (условие) {
    // блок кода
}

// do-while
do {
    // блок кода
} while (условие);

// for-each (с Java 5)
for (тип элемент : коллекция) {
    // блок кода
}
```

### Операторы перехода

**break**: прерывает выполнение цикла или оператора switch
```java
for (int i = 0; i < 10; i++) {
    if (i == 5) break; // выход из цикла при i=5
    System.out.println(i);
}
```

**continue**: переходит к следующей итерации цикла
```java
for (int i = 0; i < 10; i++) {
    if (i % 2 == 0) continue; // пропускает четные числа
    System.out.println(i);
}
```

**return**: возвращает значение из метода и завершает его выполнение
```java
int sum(int a, int b) {
    return a + b; // возвращает сумму и завершает метод
}
```

**labeled break/continue**: управление вложенными циклами
```java
outer: for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 3; j++) {
        if (i * j > 2) break outer; // выход из внешнего цикла
        System.out.println(i * j);
    }
}
```

## 3. Массивы в языке Java. Массив как параметр и тип возвращаемого значения метода. Аргументы метода main().

### Массивы в Java
Массив — объект, содержащий набор переменных одного типа.

**Объявление и инициализация:**
```java
// Объявление
int[] numbers;
String names[];  // альтернативный синтаксис

// Создание
numbers = new int[5]; // массив из 5 целых чисел

// Объявление и создание в одной строке
int[] scores = new int[10];

// Инициализация с указанием значений
int[] values = {1, 2, 3, 4, 5};
String[] fruits = new String[]{"Apple", "Orange", "Banana"};
```

**Доступ к элементам:**
```java
int third = values[2]; // доступ (индексация с нуля)
values[1] = 20;        // изменение значения
int length = values.length; // получение длины массива
```

**Многомерные массивы:**
```java
int[][] matrix = new int[3][4]; // двумерный массив 3x4
int[] row = matrix[1];          // получение одномерного массива (строки)
int element = matrix[1][2];     // доступ к элементу
```

### Массив как параметр метода
```java
// Передача массива в метод
void processArray(int[] data) {
    for (int value : data) {
        System.out.println(value);
    }
}

// Вызов
int[] numbers = {1, 2, 3};
processArray(numbers);
```

### Массив как возвращаемое значение
```java
// Метод, возвращающий массив
int[] createSequence(int length) {
    int[] result = new int[length];
    for (int i = 0; i < length; i++) {
        result[i] = i * 2;
    }
    return result;
}

// Использование
int[] sequence = createSequence(5);
```

### Аргументы метода main()
Метод `main()` — точка входа в Java-приложение:
```java
public static void main(String[] args) {
    // args содержит аргументы командной строки
    for (String arg : args) {
        System.out.println(arg);
    }
}
```

**Особенности `args`:**
- `args` — массив строк, содержащий аргументы командной строки
- Если программа запущена без аргументов, массив пуст (не null)
- Аргументы можно передать при запуске: `java MyProgram arg1 arg2 arg3`

## 4. Классы в языке Java. Компоненты класса: данные и методы. Конструкторы. Ссылка this. Перегрузка методов. Final-компоненты. Статические компоненты класса. Операция «сборка мусора».

### Определение класса

```java
public class Person {
    // поля (данные-члены)
    private String name;
    private int age;
    
    // конструкторы
    public Person() {
        // конструктор по умолчанию
    }
    
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    // методы
    public void sayHello() {
        System.out.println("Hello, my name is " + name);
    }
    
    // геттеры и сеттеры
    public String getName() {
        return name;
    }
    
    public void setName(String name) {
        this.name = name;
    }
}
```

### Компоненты класса

**Поля (данные-члены):**
- Переменные, определяющие состояние объекта
- Могут иметь модификаторы доступа: `private`, `protected`, `public`
- Могут быть объявлены как `final`, `static`, `transient`, `volatile`

**Методы:**
- Функции, определяющие поведение объекта
- Имеют сигнатуру: возвращаемый тип, имя, параметры
- Могут быть перегружены (одно имя, разные параметры)

### Конструкторы

- Специальные методы для инициализации объектов
- Имеют имя, совпадающее с именем класса
- Не имеют возвращаемого типа (даже `void`)
- Вызываются при создании объекта с помощью `new`
- Могут быть перегружены для разных параметров

### Ссылка this

Ключевое слово `this` ссылается на текущий объект:
```java
public void setName(String name) {
    this.name = name; // this.name - поле объекта, name - параметр
}
```

**Применения `this`:**
- Разрешение конфликта имён между полями и параметрами
- Вызов другого конструктора текущего класса
- Передача ссылки на текущий объект другим методам

### Перегрузка методов

Перегрузка — определение нескольких методов с одинаковым именем, но разными параметрами:
```java
public void display(int value) {
    System.out.println("Integer: " + value);
}

public void display(String text) {
    System.out.println("String: " + text);
}

public void display(int x, int y) {
    System.out.println("Coordinates: " + x + ", " + y);
}
```

### Final-компоненты

Ключевое слово `final` может применяться к:
- **Переменным**: запрещает изменение значения
- **Методам**: запрещает переопределение в подклассах
- **Классам**: запрещает наследование

```java
final int MAX_VALUE = 100; // константа
public final void doSomething() { } // нельзя переопределить
final class Immutable { } // нельзя наследовать
```

### Статические компоненты класса

Ключевое слово `static` означает, что компонент принадлежит классу, а не объекту:

```java
public class Counter {
    // статическое поле - общее для всех объектов класса
    private static int count = 0;
    
    // статический метод - можно вызвать без создания объекта
    public static int getCount() {
        return count;
    }
    
    // статический блок инициализации
    static {
        System.out.println("Class loaded");
    }
    
    // конструктор
    public Counter() {
        count++; // увеличиваем при создании объекта
    }
}
```

### Сборка мусора

Сборка мусора — автоматический процесс освобождения памяти, занятой неиспользуемыми объектами.

**Особенности:**
- Автоматически управляется JVM
- Невозможно точно предсказать, когда произойдет
- Можно предложить JVM запустить сборку с помощью `System.gc()`
- Метод `finalize()` вызывается перед уничтожением объекта (устаревший механизм)

## 5. Наследование в Java. Суперкласс и подклассы. Конструкторы подкласса. Доступ к компонентам при наследовании. Переопределение методов.

### Наследование в Java

Наследование — механизм создания новых классов на основе существующих.

```java
// Базовый класс (суперкласс)
public class Animal {
    protected String name;
    
    public Animal(String name) {
        this.name = name;
    }
    
    public void eat() {
        System.out.println(name + " is eating");
    }
    
    public void sleep() {
        System.out.println(name + " is sleeping");
    }
}

// Производный класс (подкласс)
public class Dog extends Animal {
    private String breed;
    
    public Dog(String name, String breed) {
        super(name); // вызов конструктора суперкласса
        this.breed = breed;
    }
    
    public void bark() {
        System.out.println(name + " is barking");
    }
    
    @Override
    public void eat() {
        System.out.println(name + " the " + breed + " is eating dog food");
    }
}
```

### Конструкторы подкласса

- Конструктор подкласса должен явно или неявно вызывать конструктор суперкласса
- Если в суперклассе нет конструктора без параметров, подкласс должен явно вызвать один из конструкторов суперкласса с помощью `super(параметры)`
- Вызов `super(...)` должен быть первым оператором в конструкторе подкласса

```java
public class SubClass extends SuperClass {
    public SubClass() {
        super(); // вызов конструктора суперкласса без параметров
    }
    
    public SubClass(int value) {
        super(value); // вызов конструктора суперкласса с параметром
    }
}
```

### Доступ к компонентам при наследовании

Модификаторы доступа определяют видимость компонентов для подклассов:

| Модификатор  | В том же классе | В подклассе | В пакете | Везде |
|--------------|-----------------|-------------|----------|-------|
| private      | ✓               | ×           | ×        | ×     |
| (по умолчанию)| ✓               | ✓ (в том же пакете) | ✓    | ×     |
| protected    | ✓               | ✓           | ✓        | ×     |
| public       | ✓               | ✓           | ✓        | ✓     |

Особенности:
- `private` члены не наследуются (технически они есть, но недоступны)
- Для доступа к членам суперкласса можно использовать ключевое слово `super`
- Члены с модификатором доступа по умолчанию доступны только в том же пакете

### Переопределение методов

Переопределение (override) — изменение реализации метода в подклассе.

```java
public class Animal {
    public void makeSound() {
        System.out.println("Some animal sound");
    }
}

public class Cat extends Animal {
    @Override
    public void makeSound() {
        System.out.println("Meow");
    }
}
```

**Правила переопределения:**
- Сигнатура метода должна быть идентична (имя, параметры)
- Возвращаемый тип может быть ковариантным (тем же или подтипом)
- Метод не может иметь более строгий модификатор доступа
- Метод не может объявлять больше исключений
- Нельзя переопределить `final` методы
- Аннотация `@Override` помогает избежать ошибок
- Статические методы не переопределяются, а скрываются (hiding)

## 6. Абстрактные методы. Абстрактные классы и интерфейсы и их реализация.

### Абстрактные методы и классы

**Абстрактный метод** — метод без реализации, который должен быть переопределен в подклассе.

**Абстрактный класс** — класс, который не может быть инстанцирован и часто содержит абстрактные методы.

```java
public abstract class Shape {
    protected String color;
    
    public Shape(String color) {
        this.color = color;
    }
    
    // абстрактный метод - без реализации
    public abstract double getArea();
    
    // конкретный метод - с реализацией
    public String getColor() {
        return color;
    }
}

public class Circle extends Shape {
    private double radius;
    
    public Circle(String color, double radius) {
        super(color);
        this.radius = radius;
    }
    
    @Override
    public double getArea() {
        return Math.PI * radius * radius;
    }
}
```

**Особенности абстрактных классов:**
- Не могут быть инстанцированы (`new Shape()` вызовет ошибку)
- Могут содержать абстрактные и конкретные методы
- Могут содержать конструкторы, поля, статические методы
- Подклассы должны реализовать все абстрактные методы или сами быть абстрактными

### Интерфейсы

**Интерфейс** — абстрактный тип, определяющий контракт для классов, которые его реализуют.

```java
public interface Drawable {
    void draw(); // абстрактный метод (public abstract по умолчанию)
    
    // константа (public static final по умолчанию)
    int MAX_DIMENSION = 1000;
    
    // метод по умолчанию (с Java 8)
    default void clear() {
        System.out.println("Default clearing behavior");
    }
    
    // статический метод (с Java 8)
    static boolean isValidSize(int size) {
        return size > 0 && size <= MAX_DIMENSION;
    }
    
    // приватный метод (с Java 9)
    private void internalMethod() {
        // доступен только внутри интерфейса
    }
}
```

**Реализация интерфейса:**
```java
public class Circle implements Drawable {
    @Override
    public void draw() {
        System.out.println("Drawing Circle");
    }
    
    // можно переопределить метод по умолчанию
    @Override
    public void clear() {
        System.out.println("Special clearing for Circle");
    }
}
```

**Особенности интерфейсов:**
- Класс может реализовать несколько интерфейсов
- Интерфейс может расширять другие интерфейсы
- С Java 8 поддерживают методы по умолчанию и статические методы
- С Java 9 поддерживают приватные методы
- Все поля интерфейса автоматически `public static final`
- Все методы интерфейса автоматически `public` (если не указано иное)

### Различия между абстрактными классами и интерфейсами

| Характеристика | Абстрактный класс | Интерфейс |
|----------------|-------------------|-----------|
| Инстанцирование | Нельзя | Нельзя |
| Наследование | Один суперкласс | Множество интерфейсов |
| Поля | Любые | Только константы |
| Конструкторы | Да | Нет |
| Методы | Любые | Абстрактные, default, static, private |
| Реализация | Частичная | Только через default методы |
| Цель | "является" отношение | "может делать" функциональность |

## 7. Оболочки простых типов. Обзор пакета java.lang.

### Оболочки примитивных типов

Java предоставляет классы-оболочки для всех примитивных типов:

| Примитивный тип | Класс-оболочка | Пример создания |
|-----------------|----------------|-----------------|
| byte            | Byte           | Byte b = new Byte((byte)1); |
| short           | Short          | Short s = new Short((short)100); |
| int             | Integer        | Integer i = new Integer(10); |
| long            | Long           | Long l = new Long(100L); |
| float           | Float          | Float f = new Float(1.0f); |
| double          | Double         | Double d = new Double(1.0); |
| char            | Character      | Character c = new Character('A'); |
| boolean         | Boolean        | Boolean b = new Boolean(true); |

**Автоупаковка и автораспаковка** (с Java 5):
```java
Integer num = 10; // автоупаковка: int → Integer
int value = num;  // автораспаковка: Integer → int
```

**Основные методы классов-оболочек:**
- Преобразование строки в примитив: `parseInt()`, `parseDouble()` и т.д.
- Преобразование примитива в строку: `toString()`
- Константы: `MAX_VALUE`, `MIN_VALUE`
- Сравнение: `compareTo()`, `equals()`
- Преобразование типов: `intValue()`, `doubleValue()` и т.д.

### Обзор пакета java.lang

Пакет `java.lang` — основной пакет Java API, автоматически импортируемый во все программы.

**Важные классы:**

1. **Object** — базовый класс для всех классов в Java
   - `equals()` — сравнение объектов
   - `hashCode()` — хеш-код объекта
   - `toString()` — строковое представление
   - `getClass()` — получение мета-информации о классе
   - `clone()` — создание копии объекта
   - `finalize()` — метод, вызываемый перед сборкой мусора (устаревший)

2. **String** — неизменяемая строка
   - `length()` — длина строки
   - `charAt()` — символ по индексу
   - `substring()` — подстрока
   - `equals()` — сравнение строк
   - `indexOf()` — поиск подстроки
   - `replace()` — замена подстроки
   - `split()` — разделение строки

3. **StringBuffer/StringBuilder** — изменяемые строки
   - `append()` — добавление к строке
   - `insert()` — вставка в строку
   - `delete()` — удаление части строки
   - `reverse()` — обращение строки

4. **Math** — математические функции
   - `abs()`, `max()`, `min()`, `pow()`, `sqrt()`, `random()`
   - Константы: `PI`, `E`

5. **System** — взаимодействие с окружением
   - `out` — стандартный вывод
   - `in` — стандартный ввод
   - `err` — стандартный поток ошибок
   - `currentTimeMillis()` — текущее время
   - `arraycopy()` — копирование массивов
   - `gc()` — запрос сборки мусора

6. **Class** — мета-информация о классах (рефлексия)
   - `forName()` — получение класса по имени
   - `newInstance()` — создание экземпляра
   - `getMethods()` — получение методов
   - `getFields()` — получение полей

7. **Thread** — поддержка многопоточности
   - `start()` — запуск потока
   - `run()` — метод, содержащий код потока
   - `sleep()` — приостановка потока
   - `join()` — ожидание завершения потока

## 8. Обработка исключительных ситуаций. Иерархия классов исключений. Создание собственных классов исключений.

### Обработка исключительных ситуаций

Исключения в Java — механизм обработки ошибок и необычных ситуаций, возникающих во время выполнения программы.

**Блок try-catch-finally:**
```java
try {
    // код, который может вызвать исключение
    int result = 10 / 0; // ArithmeticException
} catch (ArithmeticException e) {
    // обработка конкретного исключения
    System.out.println("Деление на ноль: " + e.getMessage());
} catch (Exception e) {
    // обработка всех других исключений
    System.out.println("Ошибка: " + e.getMessage());
} finally {
    // выполняется всегда, независимо от исключения
    System.out.println("Блок finally выполнен");
}
```

**Блок try-with-resources** (с Java 7):
```java
try (FileReader reader = new FileReader("file.txt");
     BufferedReader br = new BufferedReader(reader)) {
    // код, использующий ресурсы
    String line = br.readLine();
} catch (IOException e) {
    // обработка исключения
}
// ресурсы автоматически закрываются
```

**Объявление исключений с помощью throws:**
```java
public void readFile(String path) throws IOException {
    // метод, который может вызвать IOException
    FileReader reader = new FileReader(path);
    // ...
}
```

### Иерархия классов исключений

В Java все исключения наследуются от класса `Throwable`:

- **Throwable** — базовый класс всех исключений
  - **Error** — серьезные ошибки, которые обычно не обрабатываются
    - OutOfMemoryError
    - StackOverflowError
    - VirtualMachineError
  - **Exception** — проверяемые исключения (checked)
    - IOException
    - SQLException
    - ClassNotFoundException
    - **RuntimeException** — непроверяемые исключения (unchecked)
      - NullPointerException
      - ArrayIndexOutOfBoundsException
      - ArithmeticException
      - IllegalArgumentException

**Проверяемые исключения (checked):**
- Должны быть объявлены в сигнатуре метода с помощью `throws` или обработаны в блоке `try-catch`
- Компилятор проверяет их обработку
- Обычно представляют условия, которые можно предвидеть и обработать

**Непроверяемые исключения (unchecked):**
- Не требуют объявления или обработки
- Обычно представляют программные ошибки
- Наследуются от `RuntimeException`

### Создание собственных классов исключений

```java
// Проверяемое исключение
public class InsufficientFundsException extends Exception {
    private double amount;
    
    public InsufficientFundsException(String message, double amount) {
        super(message);
        this.amount = amount;
    }
    
    public double getAmount() {
        return amount;
    }
}

// Непроверяемое исключение
public class InvalidUserDataException extends RuntimeException {
    public InvalidUserDataException(String message) {
        super(message);
    }
    
    public InvalidUserDataException(String message, Throwable cause) {
        super(message, cause);
    }
}
```

**Использование:**
```java
public class BankAccount {
    private double balance;
    
    public void withdraw(double amount) throws InsufficientFundsException {
        if (amount > balance) {
            throw new InsufficientFundsException(
                "Недостаточно средств для снятия", amount - balance);
        }
        balance -= amount;
    }
    
    public void setName(String name) {
        if (name == null || name.isEmpty()) {
            throw new InvalidUserDataException("Имя не может быть пустым");
        }
        // установка имени
    }
}
```

**Рекомендации по созданию исключений:**
- Наследуйте от `Exception` для проверяемых исключений
- Наследуйте от `RuntimeException` для непроверяемых исключений
- Используйте информативные имена классов с суффиксом "Exception"
- Включайте полезную информацию об ошибке
- Предоставляйте разные конструкторы
- Документируйте исключения с помощью JavaDoc