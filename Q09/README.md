# Вопрос

В коде JavaScript есть цикл `for`, внутри которого вложен вызов `setTimeout`. При каждой итерации локальная переменная `i` увеличивается на единицу, а в анонимной функции которую вызывает `setTimeout` есть вывод той переменной `i` в консоль. Какие цифры отобразятся в консоли при 10 итерациях цикла?

# Ответ

Функция `setTimeout` в любом случае срабаывает после завершения цикла. Однако итоговый результат зависит от того, какой мы использует тип переменной.

## Тип let

```
for (let i = 0; i < 10; i++) {
    setTimeout(function () {
        console.log(i);
    }, 1000);
}
```
Здесь мы объявляем переменную `i` через `let`. Поэтому для каждой итерации будет создаваться отдельная переменная с разным значением. В результате в консоли мы увидим:
```
0
1
2
3
...
9
```

## Тип var

```
for (var i = 0; i < 10; i++) {
    setTimeout(function () {
        console.log(i);
    }, 1000);
}
```

Переменная `i` объявлена через `var`, у которой иная область видимости. В данном случае переменная `i` не будет пересоздаваться каждый раз, поэтому в консоли мы увидим `10`.

## Резюме

Таким образом без явного примера кода нельзя точно сказать, какой именно результат мы увидим в консоли. 