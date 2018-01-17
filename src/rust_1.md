# Основы синтаксиса

```rust
// Это комментарий. Однострочные комментарии выглядят примерно так...

/*
    Многострочный
    комментарий
*/

/// Комментарии-документация выглядят примерно так и поддерживают markdown-разметку.
/// # Пример
///
/// ```
/// let five = 5
/// ```

// Функции.
// `i32` это тип для 32-разрядных целых чисел со знаком (4 байта в памяти)
fn add2(x: i32, y: i32) -> i32 {
    // Неявный return (без ;)
    x + y
    // Можно также использовать явный return: return x + y;
    // Вызов этой функции: add2(1, 3)
}

// Функция Main
// Отсюда начинается выполнение программы
fn main() {
    // Числа //

    // Неизменяемые привязки
    let x: i32 = 1;
    // x = 3; <-- ошибка времени компиляции

    // Изменяемые переменные
    let mut mutable = 1;
    mutable = 4;
    mutable += 2;

    // Суфиксы для целых чисел(integer) и чисел с плавающей запятой(float)
    let y: i32 = 13i32;
    let f: f64 = 1.3f64;

    // Вывод типов
    //
    // В большинстве случаев компилятор Rust может сам определить тип переменной,
    // поэтому вам не нужно писать явное аннотирование типа.
    // В этом учебном пособии типы явно аннотируются
    // во многих местах в демонстрационных целях.
    // Вывод типов может справиться с этим для вас большую часть времени.

    let implicit_x = 1;
    let implicit_f = 1.3;

    // Арифметика
    let sum = x + y + 13;

    // Строки //

    // Строковые литералы
    let x: &str = "hello world!";

    // Вывод в консоль
    println!("{} {}", f, x); // 1.3 hello world

    // `String` - строка в динамически выделенной памяти
    let s: String = "hello world".into();
    let s2: String = "hello world".to_string();
    let s3: String = String::from("hello world");

    // A string slice: an immutable view into another string.
    //
    // This is essentially an immutable pair of pointers to a string - it
    // doesn't actually contain the contents of a string, just a pointer to the
    // begin and a pointer to the end of a string buffer, statically allocated
    // or contained in another object (in this case, `s`)
    let s_slice: &str = &s;
    let s_slice2: &str = &s[6..11];
    let s_slice3: &str = &s[6..];
    let s_slice4: &str = &s[..5];

    println!("{} {}", s, s_slice); // hello world hello world

    // Vectors/arrays //

    // A fixed-size array
    let four_ints: [i32; 4] = [1, 2, 3, 4];

    // A dynamic array (vector)
    let mut vector: Vec<i32> = vec![1, 2, 3, 4];
    vector.push(5);

    // Mutability is inherited by the bound value. If `vector` is not declared
    // `mut`, then the value cannot be mutated.
    let vector: Vec<i32> = vec![1, 2, 3, 4, 5];
    // vector.push(5); <-- compile-time error

    // A slice - an immutable view into a vector or array.
    let slice: &[i32] = &vector;
    let slice2: &[i32] = &vector[1..4];

    // Use `{:?}` to print something debug-style
    println!("{:?} | {:?}", vector, slice2); // [1, 2, 3, 4, 5] | [2, 3, 4]

    // Array, slice, and vector indexing.
    println!("{}", four_ints[1]); // 2
    println!("{}", vector[2]); // 3
    println!("{}", slice[3]); // 4

    // Tuples //

    // A tuple is a fixed-size set of values of possibly different types
    let x: (i32, &str, f64) = (1, "hello", 3.4);

    // Destructuring `let`
    let (a, b, c) = x;
    println!("{} {} {}", a, b, c); // 1 hello 3.4
    // Structures can also be destructured on assignment, as we'll see later.

    // Tuple indexing.
    println!("{}", x.1); // hello
}
```
