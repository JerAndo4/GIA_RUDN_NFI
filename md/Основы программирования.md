# Основы программирования

## 1. Базовые типы данных: описание, инициализация переменных. Правила записи констант. Что определяет тип данного.

### Базовые типы данных

В языках программирования существуют следующие основные типы данных:

#### Целочисленные типы
- **int** - целое число (обычно 4 байта, диапазон от -2^31 до 2^31-1)
- **short** - короткое целое число (обычно 2 байта)
- **long** - длинное целое число (обычно 8 байт)
- **byte** / **char** - тип для хранения одного байта данных (0-255)

#### Типы с плавающей точкой
- **float** - число с плавающей точкой одинарной точности (обычно 4 байта)
- **double** - число с плавающей точкой двойной точности (обычно 8 байт)

#### Логический тип
- **bool** / **boolean** - логический тип (true/false)

#### Символьный тип
- **char** - символ (обычно 2 байта в C++/Java, 1 байт в C)

### Инициализация переменных

В C/C++:
```c
int a = 5;                // инициализация при объявлении
int b;                    // объявление без инициализации
b = 10;                   // присваивание значения
int c(15);                // конструкторная инициализация (C++)
int d{20};                // uniform инициализация (C++11)
const int MAX_VALUE = 100; // объявление константы
```

В Java:
```java
int a = 5;                 // инициализация при объявлении
int b;                     // объявление без инициализации
b = 10;                    // присваивание значения
final int MAX_VALUE = 100; // объявление константы
```

В Python:
```python
a = 5                    # динамическая типизация
MAX_VALUE = 100          # константы в Python - это соглашение
```

### Правила записи констант

#### Целочисленные константы
```c
int a = 10;      // десятичное число
int b = 0xA;     // шестнадцатеричное число (10 в десятичной)
int c = 012;     // восьмеричное число (10 в десятичной)
int d = 0b1010;  // двоичное число (10 в десятичной, C++14)
long e = 10L;    // константа типа long
```

#### Константы с плавающей точкой
```c
float a = 3.14f;    // константа типа float
double b = 3.14;    // константа типа double по умолчанию
double c = 3.14e2;  // научная нотация (314)
```

#### Символьные и строковые константы
```c
char a = 'A';       // символьная константа
char b = '\n';      // управляющая последовательность (новая строка)
char c = '\x41';    // шестнадцатеричная запись (символ 'A')
const char* str = "Hello"; // строковая константа (массив символов)
```

#### Логические константы
```c
bool a = true;      // логическая константа истина
bool b = false;     // логическая константа ложь
```

### Что определяет тип данных

Тип данных определяет следующие характеристики переменной:

1. **Размер памяти**, необходимый для хранения данных
2. **Диапазон значений**, которые могут быть сохранены
3. **Множество операций**, которые можно выполнить с данными
4. **Способ представления** данных в памяти (бинарное представление)
5. **Способ интерпретации** битовых шаблонов при выполнении операций

### Пример задачи:
Определить, какой объем памяти (в байтах) занимают следующие переменные в C++:
```cpp
int a;
double b;
char c;
bool d;
short e;
long long f;
```

**Решение:**
```cpp
#include <iostream>
using namespace std;

int main() {
    int a;
    double b;
    char c;
    bool d;
    short e;
    long long f;
    
    cout << "Size of int: " << sizeof(a) << " bytes" << endl;
    cout << "Size of double: " << sizeof(b) << " bytes" << endl;
    cout << "Size of char: " << sizeof(c) << " bytes" << endl;
    cout << "Size of bool: " << sizeof(d) << " bytes" << endl;
    cout << "Size of short: " << sizeof(e) << " bytes" << endl;
    cout << "Size of long long: " << sizeof(f) << " bytes" << endl;
    
    return 0;
}
```

**Вывод:**
```
Size of int: 4 bytes
Size of double: 8 bytes
Size of char: 1 bytes
Size of bool: 1 bytes
Size of short: 2 bytes
Size of long long: 8 bytes
```

## 2. Операторы ветвления: правила записи и выполнения. Примеры.

Операторы ветвления позволяют изменять порядок выполнения инструкций в зависимости от условий.

### Оператор if-else

```c
// Базовая форма
if (условие) {
    // код, если условие истинно
} else {
    // код, если условие ложно
}

// Сокращенная форма
if (условие) {
    // код, если условие истинно
}

// Цепочка if-else
if (условие1) {
    // код для условия1
} else if (условие2) {
    // код для условия2
} else {
    // код, если все условия ложны
}
```

### Тернарный оператор

```c
результат = условие ? значение_если_истина : значение_если_ложь;
```

### Оператор switch

```c
switch (выражение) {
    case значение1:
        // код для значения1
        break;
    case значение2:
        // код для значения2
        break;
    default:
        // код для остальных случаев
}
```

**Важно:**
- Без `break` выполнение "проваливается" в следующий case
- Выражение в `switch` обычно целочисленное или символ
- `default` выполняется, если нет соответствия

### Примеры

#### if-else:
```cpp
int age = 25;
if (age < 18) {
    cout << "Minor" << endl;
} else if (age < 65) {
    cout << "Adult" << endl;
} else {
    cout << "Senior" << endl;
}
```

#### Тернарный оператор:
```cpp
int a = 5, b = 10;
int max = (a > b) ? a : b;  // max будет равен 10
```

#### switch:
```cpp
int day = 3;
switch (day) {
    case 1: cout << "Monday"; break;
    case 2: cout << "Tuesday"; break;
    case 3: cout << "Wednesday"; break;
    default: cout << "Other day"; break;
}
// Выведет: Wednesday
```

#### Проваливание в switch:
```cpp
int month = 7;
switch (month) {
    case 2:
        cout << "28 or 29 days"; break;
    case 4: case 6: case 9: case 11:
        cout << "30 days"; break;
    case 1: case 3: case 5: case 7: case 8: case 10: case 12:
        cout << "31 days"; break;
    default:
        cout << "Invalid month"; break;
}
// Выведет: 31 days
```

## 3. Операторы цикла: правила записи и выполнения. Примеры.

Операторы цикла позволяют выполнять блок кода многократно.

### Цикл for

Используется, когда известно количество итераций.

```c
for (инициализация; условие; инкремент) {
    // тело цикла
}
```

Где:
- **инициализация** - выполняется один раз перед началом цикла
- **условие** - проверяется перед каждой итерацией
- **инкремент** - выполняется после каждой итерации

### Цикл while

Выполняет блок кода, пока условие истинно, проверяя его перед каждой итерацией.

```c
while (условие) {
    // тело цикла
}
```

### Цикл do-while

Проверяет условие после итерации, гарантируя выполнение тела хотя бы один раз.

```c
do {
    // тело цикла
} while (условие);
```

### Операторы управления циклами

- **break** - прерывает выполнение цикла
- **continue** - пропускает текущую итерацию
- **return** - выходит из функции

### Примеры

#### for:
```cpp
// Печать чисел от 1 до 5
for (int i = 1; i <= 5; i++) {
    cout << i << " ";
}
// Вывод: 1 2 3 4 5

// Обратный отсчёт
for (int i = 5; i > 0; i--) {
    cout << i << " ";
}
// Вывод: 5 4 3 2 1
```

#### while:
```cpp
// Вычисление суммы цифр числа
int n = 123;
int sum = 0;
int temp = n;

while (temp > 0) {
    sum += temp % 10;  // Добавляем последнюю цифру
    temp /= 10;        // Удаляем последнюю цифру
}
// sum = 6 (1+2+3)
```

#### do-while:
```cpp
int number;
do {
    cout << "Enter positive number: ";
    cin >> number;
} while (number <= 0);
// Выполнится минимум 1 раз
```

#### break и continue:
```cpp
// Вывести числа от 1 до 10, пропуская кратные 3
for (int i = 1; i <= 10; i++) {
    if (i % 3 == 0) {
        continue;  // Пропускаем числа, кратные 3
    }
    if (i > 8) {
        break;     // Прерываем цикл при i > 8
    }
    cout << i << " ";
}
// Вывод: 1 2 4 5 7 8
```

#### Вложенные циклы:
```cpp
// Таблица умножения 3×3
for (int i = 1; i <= 3; i++) {
    for (int j = 1; j <= 3; j++) {
        cout << i * j << " ";
    }
    cout << endl;
}
/* Вывод:
   1 2 3
   2 4 6
   3 6 9
*/
```

## 4. Функции в программировании. Определение. Параметры. Область применения.

### Определение функции

Функция — именованный блок кода, выполняющий определенную задачу и вызываемый из других частей программы.

#### Синтаксис функции:
```c
тип_возвращаемого_значения имя_функции(параметры) {
    // тело функции
    return значение;
}
```

#### Пример:
```cpp
int add(int a, int b) {
    return a + b;
}
```

### Параметры функций

#### Типы передачи параметров:

1. **По значению** (копия):
```cpp
void modifyValue(int x) {
    x = x * 2;  // изменяет только локальную копию
}
```

2. **По ссылке** (C++):
```cpp
void modifyValue(int& x) {
    x = x * 2;  // изменяет оригинальное значение
}
```

3. **По указателю**:
```cpp
void modifyValue(int* x) {
    *x = *x * 2;  // изменяет значение по адресу
}
```

#### Параметры по умолчанию:
```cpp
void printMessage(string message, bool newLine = true) {
    cout << message;
    if (newLine) cout << endl;
}
// Вызов: printMessage("Hello"); // с переводом строки
// Вызов: printMessage("Hello", false); // без перевода строки
```

### Возвращаемое значение

```cpp
int square(int x) {
    return x * x;  // возвращает число
}

void printHello() {
    cout << "Hello!" << endl;  // ничего не возвращает
}
```

### Прототипы функций

```cpp
// Прототип (объявление)
int add(int a, int b);

int main() {
    int result = add(5, 3);  // использование до определения
    return 0;
}

// Определение
int add(int a, int b) {
    return a + b;
}
```

### Область применения функций

1. **Декомпозиция задач** — разделение сложной задачи
2. **Повторное использование кода** — избегание дублирования
3. **Абстракция** — скрытие деталей реализации
4. **Модульность** — логическое разделение программы

### Примеры

#### Рекурсивная функция:
```cpp
int factorial(int n) {
    if (n <= 1) return 1;
    return n * factorial(n - 1);
}
// factorial(5) = 5 * 4 * 3 * 2 * 1 = 120
```

#### Поиск максимума:
```cpp
int findMax(int a, int b, int c) {
    int max = a;
    if (b > max) max = b;
    if (c > max) max = c;
    return max;
}
// findMax(10, 5, 8) вернёт 10
```

#### Перегрузка функций (C++):
```cpp
int add(int a, int b) { return a + b; }
double add(double a, double b) { return a + b; }
string add(string a, string b) { return a + b; }

// add(5, 3) вызовет первую версию
// add(3.2, 1.8) вызовет вторую версию
// add("Hello", "World") вызовет третью версию
```

## 5. Массивы, многомерные массивы: описание, инициализация, обращение к массиву.

### Массивы

Массив — это структура данных, которая хранит последовательность элементов одного типа, расположенных в памяти последовательно. Каждый элемент массива доступен по своему индексу (обычно индексация начинается с 0).

#### Объявление и инициализация массивов в C/C++:

```cpp
// Объявление массива без инициализации
int arr[5];  // массив из 5 целых чисел

// Объявление с инициализацией
int nums[5] = {1, 2, 3, 4, 5};

// Если указан размер, недостающие элементы инициализируются нулями
int partial[5] = {1, 2, 3};  // будет {1, 2, 3, 0, 0}

// Можно опустить размер, если известны все элементы
int auto_sized[] = {5, 4, 3, 2, 1};  // размер 5 определится автоматически

// Инициализация конкретных элементов (C++11)
int specific[5] = {0};      // все элементы 0
specific[2] = 5;            // изменяем третий элемент
```

#### Доступ к элементам массива:

```cpp
int arr[5] = {10, 20, 30, 40, 50};

int first = arr[0];        // первый элемент (10)
int third = arr[2];        // третий элемент (30)
arr[4] = 99;               // изменяем пятый элемент
```

#### Обход массива в цикле:

```cpp
int arr[5] = {10, 20, 30, 40, 50};

// Вывод всех элементов
for (int i = 0; i < 5; i++) {
    cout << arr[i] << " ";
}
cout << endl;

// Вычисление суммы элементов
int sum = 0;
for (int i = 0; i < 5; i++) {
    sum += arr[i];
}
cout << "Sum: " << sum << endl;
```

### Многомерные массивы

Многомерный массив — это массив массивов. Наиболее распространены двумерные массивы, которые можно представить как таблицу.

#### Объявление и инициализация двумерных массивов:

```cpp
// Объявление двумерного массива 3x3
int matrix[3][3];

// Объявление с инициализацией (по строкам)
int grid[3][3] = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

// Можно опустить размер первого измерения
int another_grid[][3] = {
    {1, 2, 3},
    {4, 5, 6}
};  // размер 2x3
```

#### Доступ к элементам двумерного массива:

```cpp
int matrix[3][3] = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

int center = matrix[1][1];    // элемент в середине (5)
matrix[0][2] = 10;            // изменяем элемент в первой строке, третьем столбце
```

#### Обход двумерного массива:

```cpp
int matrix[3][3] = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};

// Вывод по строкам
for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 3; j++) {
        cout << matrix[i][j] << " ";
    }
    cout << endl;
}

// Вычисление суммы всех элементов
int sum = 0;
for (int i = 0; i < 3; i++) {
    for (int j = 0; j < 3; j++) {
        sum += matrix[i][j];
    }
}
cout << "Sum of all elements: " << sum << endl;
```

### Массивы в динамической памяти (C++)

```cpp
// Одномерный динамический массив
int* arr = new int[5];
for (int i = 0; i < 5; i++) {
    arr[i] = i * 10;
}
// Не забудьте освободить память
delete[] arr;

// Двумерный динамический массив
int rows = 3, cols = 4;
int** matrix = new int*[rows];
for (int i = 0; i < rows; i++) {
    matrix[i] = new int[cols];
    // Инициализация
    for (int j = 0; j < cols; j++) {
        matrix[i][j] = i * cols + j;
    }
}
// Освобождение памяти (в обратном порядке)
for (int i = 0; i < rows; i++) {
    delete[] matrix[i];
}
delete[] matrix;
```

### Примеры задач с массивами

#### Поиск максимального элемента в массиве:
```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[] = {12, 45, 7, 23, 56, 89, 32};
    int size = sizeof(arr) / sizeof(arr[0]);
    
    int max = arr[0];
    for (int i = 1; i < size; i++) {
        if (arr[i] > max) {
            max = arr[i];
        }
    }
    
    cout << "Maximum element: " << max << endl;
    return 0;
}
```

#### Сортировка массива пузырьком:
```cpp
#include <iostream>
using namespace std;

int main() {
    int arr[] = {64, 34, 25, 12, 22, 11, 90};
    int size = sizeof(arr) / sizeof(arr[0]);
    
    // Bubble sort
    for (int i = 0; i < size - 1; i++) {
        for (int j = 0; j < size - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                // Обмен элементов
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
    
    cout << "Sorted array: ";
    for (int i = 0; i < size; i++) {
        cout << arr[i] << " ";
    }
    cout << endl;
    
    return 0;
}
```

#### Умножение матриц:
```cpp
#include <iostream>
using namespace std;

int main() {
    int A[3][2] = {{1, 2}, {3, 4}, {5, 6}};
    int B[2][4] = {{7, 8, 9, 10}, {11, 12, 13, 14}};
    int C[3][4] = {0}; // Результирующая матрица
    
    // Умножение матриц A и B
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 4; j++) {
            for (int k = 0; k < 2; k++) {
                C[i][j] += A[i][k] * B[k][j];
            }
        }
    }
    
    // Вывод результата
    cout << "Result matrix C:" << endl;
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 4; j++) {
            cout << C[i][j] << " ";
        }
        cout << endl;
    }
    
    return 0;
}
```

## 6. Принципы модульности в программировании.

Модульность — это принцип программирования, заключающийся в разделении программы на отдельные, независимые модули, каждый из которых отвечает за выполнение определенной функциональности. Модули должны быть слабо связаны между собой и сильно связаны внутри себя.

### Основные принципы модульности:

#### 1. Разделение ответственности (Separation of Concerns)
Каждый модуль должен отвечать за решение одной конкретной задачи или аспекта системы. Это улучшает понимание кода и упрощает поддержку.

#### 2. Инкапсуляция
Модули должны скрывать детали своей реализации и предоставлять четко определенный интерфейс. Это позволяет изменять внутреннюю реализацию модуля без влияния на другие части программы.

#### 3. Независимость
Модули должны быть максимально независимыми друг от друга. Идеальный модуль можно извлечь из системы и использовать в другой программе без изменений.

#### 4. Повторное использование
Хорошо спроектированные модули можно использовать повторно в разных частях программы или в разных проектах.

#### 5. Тестируемость
Модули должны быть легко тестируемыми в изоляции от остальной системы.

### Реализация модульности в различных языках программирования:

#### В языке C:
В C модульность реализуется через разделение кода на файлы (`.c` и `.h`):

**math_utils.h** (интерфейс):
```c
#ifndef MATH_UTILS_H
#define MATH_UTILS_H

int add(int a, int b);
int subtract(int a, int b);
int multiply(int a, int b);
double divide(int a, int b);

#endif
```

**math_utils.c** (реализация):
```c
#include "math_utils.h"

int add(int a, int b) {
    return a + b;
}

int subtract(int a, int b) {
    return a - b;
}

int multiply(int a, int b) {
    return a * b;
}

double divide(int a, int b) {
    if (b != 0) {
        return (double)a / b;
    }
    // В реальном коде здесь должна быть обработка ошибки
    return 0;
}
```

**main.c** (использование):
```c
#include <stdio.h>
#include "math_utils.h"

int main() {
    int x = 10, y = 5;
    
    printf("Sum: %d\n", add(x, y));
    printf("Difference: %d\n", subtract(x, y));
    printf("Product: %d\n", multiply(x, y));
    printf("Quotient: %.2f\n", divide(x, y));
    
    return 0;
}
```

#### В языке C++:
В C++ модульность реализуется через классы, пространства имен и организацию файлов:

**Vector.h**:
```cpp
#ifndef VECTOR_H
#define VECTOR_H

class Vector {
private:
    double x, y, z;
    
public:
    Vector(double x = 0, double y = 0, double z = 0);
    
    // Геттеры
    double getX() const;
    double getY() const;
    double getZ() const;
    
    // Операции с векторами
    Vector add(const Vector& other) const;
    double dot(const Vector& other) const;
    Vector cross(const Vector& other) const;
    double magnitude() const;
};

#endif
```

**Vector.cpp**:
```cpp
#include "Vector.h"
#include <cmath>

Vector::Vector(double x, double y, double z) : x(x), y(y), z(z) {}

double Vector::getX() const { return x; }
double Vector::getY() const { return y; }
double Vector::getZ() const { return z; }

Vector Vector::add(const Vector& other) const {
    return Vector(x + other.x, y + other.y, z + other.z);
}

double Vector::dot(const Vector& other) const {
    return x * other.x + y * other.y + z * other.z;
}

Vector Vector::cross(const Vector& other) const {
    return Vector(
        y * other.z - z * other.y,
        z * other.x - x * other.z,
        x * other.y - y * other.x
    );
}

double Vector::magnitude() const {
    return std::sqrt(x*x + y*y + z*z);
}
```

**main.cpp**:
```cpp
#include <iostream>
#include "Vector.h"

int main() {
    Vector v1(1, 2, 3);
    Vector v2(4, 5, 6);
    
    Vector sum = v1.add(v2);
    double dotProduct = v1.dot(v2);
    Vector crossProduct = v1.cross(v2);
    
    std::cout << "v1 magnitude: " << v1.magnitude() << std::endl;
    std::cout << "v2 magnitude: " << v2.magnitude() << std::endl;
    std::cout << "Sum: (" << sum.getX() << ", " << sum.getY() << ", " << sum.getZ() << ")" << std::endl;
    std::cout << "Dot product: " << dotProduct << std::endl;
    std::cout << "Cross product: (" << crossProduct.getX() << ", " << crossProduct.getY() << ", " << crossProduct.getZ() << ")" << std::endl;
    
    return 0;
}
```

### Преимущества модульного программирования:

1. **Управление сложностью**: Разделение программы на небольшие модули упрощает понимание и поддержку кода.
2. **Параллельная разработка**: Разные команды могут работать над разными модулями одновременно.
3. **Повторное использование**: Модули могут использоваться в разных проектах или частях одного проекта.
4. **Изоляция ошибок**: Проблемы в одном модуле обычно не влияют на работу других модулей.
5. **Упрощение тестирования**: Модули можно тестировать независимо друг от друга.
6. **Упрощение сопровождения**: Изменения в одном модуле обычно не требуют изменений в других модулях.

### Принципы SOLID в модульном программировании:

1. **S** (Single Responsibility Principle): Каждый модуль должен иметь только одну причину для изменения.
2. **O** (Open/Closed Principle): Модули должны быть открыты для расширения, но закрыты для модификации.
3. **L** (Liskov Substitution Principle): Подклассы должны быть заменяемы на свои базовые классы.
4. **I** (Interface Segregation Principle): Много специализированных интерфейсов лучше, чем один универсальный.
5. **D** (Dependency Inversion Principle): Высокоуровневые модули не должны зависеть от низкоуровневых; оба типа должны зависеть от абстракций.

### Пример организации модульного проекта (структура директорий):

```
project/
├── include/           # Заголовочные файлы (интерфейсы)
│   ├── math/
│   │   ├── vector.h
│   │   └── matrix.h
│   └── utils/
│       ├── logger.h
│       └── config.h
├── src/               # Исходные файлы (реализация)
│   ├── math/
│   │   ├── vector.cpp
│   │   └── matrix.cpp
│   └── utils/
│       ├── logger.cpp
│       └── config.cpp
├── tests/             # Тесты для модулей
│   ├── math_tests.cpp
│   └── utils_tests.cpp
├── docs/              # Документация
├── examples/          # Примеры использования
└── CMakeLists.txt     # Файл сборки
```

## 7. Указатели: описание, операции разадресации и взятия адреса, адресная арифметика.

### Указатели

Указатель — это переменная, которая хранит адрес памяти другой переменной или объекта. Указатели позволяют работать с данными по ссылке, а не по значению, и являются основой для динамического управления памятью.

### Объявление и инициализация указателей

```cpp
// Объявление указателя на int
int* ptr;       // или int *ptr;

// Инициализация нулевым указателем
int* ptr1 = nullptr;  // C++11
int* ptr2 = NULL;     // до C++11
int* ptr3 = 0;        // устаревший способ

// Взятие адреса переменной
int value = 42;
int* ptr = &value;  // ptr теперь указывает на value
```

### Операции с указателями

#### 1. Операция взятия адреса (&)
Оператор `&` возвращает адрес памяти переменной.

```cpp
int x = 10;
int* p = &x;  // p содержит адрес x
```

#### 2. Операция разадресации (*)
Оператор `*` (звездочка) используется для доступа к значению, хранящемуся по адресу, на который указывает указатель.

```cpp
int x = 10;
int* p = &x;
*p = 20;  // изменяет значение x через указатель
cout << x << endl;  // выведет 20
```

#### 3. Адресная арифметика
С указателями можно выполнять арифметические операции, которые зависят от типа данных, на который указывает указатель.

```cpp
int arr[5] = {10, 20, 30, 40, 50};
int* p = arr;  // указатель на первый элемент массива

cout << *p << endl;      // 10 (первый элемент)
cout << *(p + 1) << endl;  // 20 (второй элемент)
cout << *(p + 2) << endl;  // 30 (третий элемент)

// Увеличение указателя на 1 перемещает его к следующему элементу
p++;
cout << *p << endl;  // 20 (теперь p указывает на второй элемент)

// Уменьшение указателя
p--;
cout << *p << endl;  // 10 (снова указывает на первый элемент)

// Разница между указателями
int* p1 = &arr[1];
int* p2 = &arr[4];
ptrdiff_t diff = p2 - p1;  // diff будет равно 3
```

### Указатели и массивы

В C/C++ имя массива автоматически преобразуется в указатель на его первый элемент в большинстве контекстов.

```cpp
int arr[5] = {10, 20, 30, 40, 50};
int* p = arr;  // то же, что и p = &arr[0]

// Два эквивалентных способа доступа к элементам
cout << arr[2] << endl;  // 30
cout << *(arr + 2) << endl;  // 30

// Обход массива с помощью указателя
for (int* p = arr; p < arr + 5; p++) {
    cout << *p << " ";
}
cout << endl;  // Выведет: 10 20 30 40 50
```

### Указатели и функции

#### 1. Передача аргументов по указателю

```cpp
void modifyValue(int* ptr) {
    *ptr = *ptr * 2;  // умножаем значение на 2
}

int main() {
    int x = 10;
    modifyValue(&x);
    cout << x << endl;  // Выведет: 20
    return 0;
}
```

#### 2. Возвращение указателя из функции

```cpp
int* createArray(int size, int value) {
    int* arr = new int[size];
    for (int i = 0; i < size; i++) {
        arr[i] = value;
    }
    return arr;
}

int main() {
    int* myArray = createArray(5, 42);
    
    for (int i = 0; i < 5; i++) {
        cout << myArray[i] << " ";
    }
    cout << endl;  // Выведет: 42 42 42 42 42
    
    delete[] myArray;  // Важно освободить память
    return 0;
}
```

### Указатели на указатели

```cpp
int x = 10;
int* p = &x;
int** pp = &p;  // указатель на указатель

cout << x << endl;    // 10
cout << *p << endl;   // 10
cout << **pp << endl; // 10

**pp = 20;  // изменение значения x через двойной указатель
cout << x << endl;    // 20
```

### Указатели на функции

```cpp
int add(int a, int b) {
    return a + b;
}

int subtract(int a, int b) {
    return a - b;
}

int main() {
    // Объявление указателя на функцию
    int (*operation)(int, int);
    
    // Присваивание адреса функции
    operation = add;
    cout << operation(5, 3) << endl;  // Выведет: 8
    
    // Изменение функции
    operation = subtract;
    cout << operation(5, 3) << endl;  // Выведет: 2
    
    return 0;
}
```

### Динамическое выделение памяти

```cpp
// Выделение памяти для одного int
int* p = new int;
*p = 42;
// Освобождение памяти
delete p;

// Выделение памяти для массива
int* arr = new int[10];
for (int i = 0; i < 10; i++) {
    arr[i] = i * 10;
}
// Освобождение памяти для массива
delete[] arr;
```

### Смарт-указатели (C++11 и выше)

```cpp
#include <memory>

int main() {
    // unique_ptr - эксклюзивное владение
    std::unique_ptr<int> uniq_ptr = std::make_unique<int>(42);
    std::cout << *uniq_ptr << std::endl;  // 42
    
    // shared_ptr - разделяемое владение
    std::shared_ptr<int> shared_ptr1 = std::make_shared<int>(10);
    std::shared_ptr<int> shared_ptr2 = shared_ptr1;
    *shared_ptr1 = 20;
    std::cout << *shared_ptr2 << std::endl;  // 20
    
    // weak_ptr - неовладевающая ссылка на shared_ptr
    std::weak_ptr<int> weak_ptr = shared_ptr1;
    
    return 0;
}
```

### Типичные ошибки при работе с указателями

1. **Разыменование нулевого указателя**:
```cpp
int* p = nullptr;
*p = 42;  // Ошибка времени выполнения
```

2. **Использование неинициализированного указателя**:
```cpp
int* p;
*p = 42;  // Undefined behavior
```

3. **Утечка памяти**:
```cpp
int* p = new int;
p = nullptr;  // Память не освобождена через delete
```

4. **Двойное освобождение**:
```cpp
int* p = new int;
delete p;
delete p;  // Ошибка: двойное освобождение памяти
```

5. **Висячий указатель**:
```cpp
int* p = new int;
delete p;
*p = 42;  // Ошибка: использование после освобождения
```

### Пример: связный список с использованием указателей

```cpp
#include <iostream>
using namespace std;

// Структура для узла связного списка
struct Node {
    int data;
    Node* next;
    
    Node(int val) : data(val), next(nullptr) {}
};

// Функция для добавления узла в конец списка
void append(Node*& head, int val) {
    Node* newNode = new Node(val);
    
    if (head == nullptr) {
        head = newNode;
        return;
    }
    
    Node* temp = head;
    while (temp->next != nullptr) {
        temp = temp->next;
    }
    
    temp->next = newNode;
}

// Функция для вывода списка
void printList(Node* head) {
    Node* temp = head;
    while (temp != nullptr) {
        cout << temp->data << " ";
        temp = temp->next;
    }
    cout << endl;
}

// Функция для освобождения памяти
void freeList(Node*& head) {
    Node* current = head;
    Node* next;
    
    while (current != nullptr) {
        next = current->next;
        delete current;
        current = next;
    }
    
    head = nullptr;
}

int main() {
    Node* head = nullptr;
    
    append(head, 10);
    append(head, 20);
    append(head, 30);
    append(head, 40);
    
    cout << "Linked list: ";
    printList(head);
    
    freeList(head);
    return 0;
}
```