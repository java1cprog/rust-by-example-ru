# Область и Затенение

Связывание переменных имеет локальную область видимости, и живут эти переменные в *блоке*.
Блок — набор инструкций, заключённый между фигурными скобками `{}`.
Кроме того, допускается [затенение переменных.][variable-shadow].

```rust,editable,ignore,mdbook-runnable
fn main() {
    // Эта переменная живёт в функции main
    let long_lived_binding = 1;

    // Это блок, он имеет меньшую область видимости, чем функция main
    {
        // Эта переменная существует только в этом блоке
        let short_lived_binding = 2;

        println!("inner short: {}", short_lived_binding);

        // Эта переменная *затеняет* собой внешнюю
        let long_lived_binding = 5_f32;

        println!("inner long: {}", long_lived_binding);
    }
    // Конец блока

    // Ошибка! `short_lived_binding` нет в этой области видимости
    println!("outer short: {}", short_lived_binding);
    // ИСПРАВЬТЕ ^ Закомментируйте строку

    println!("outer long: {}", long_lived_binding);

    // Это связывание так же *скрывает* собой предыдущие
    let long_lived_binding = 'a';

    println!("outer long: {}", long_lived_binding);
}
```

[variable-shadow]: https://en.wikipedia.org/wiki/Variable_shadowing
