# Потоки

В Rust имеется механизм для запуска потоков ОС посредством функции `scoped`,
которая принимает перемещающее окружение замыкания в качестве аргумента.

```rust,editable
use std::thread;

static NTHREADS: i32 = 10;

// Это основной поток `main`
fn main() {
    // Создадим вектор, в котором будет хранить созданные потоки.
    let mut children = vec![];

    for i in 0..NTHREADS {
        // Запустить ещё один поток
        children.push(thread::spawn(move || {
            println!("Это поток под номером  {}", i)
        }));
    }

    for child in children {
        // Ждём завершения работы потока. Возвращаем результат.
        let _ = child.join();
    }
}
```

Эти потоки управляются ОС.
