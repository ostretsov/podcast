# PHP подкаст #4

## В ожидании [PHP 7.1](https://github.com/php/php-src/blob/php-7.1.0RC3/UPGRADING)

* добавлен void;
* добавлен iterable (аналог callable);
* отрицательные индексы для доступа к элементам в типе string с конца;
* `list` с ключами в виде квадратных скобок `foreach ($iterable as ['x' => $a, 'y' => $b])`;
* `var_dump("footbal"+1)` // warning in 7.1, но корректно для 7.0;
* преобразование `callable` в Closure-объект при помощи метода `Closure::fromCallable`.
* `public`/`protected`/`private` константы;
* возвращаемый тип может быть значением или `NULL`: `function a(int $x): ?int`.

## Качественный PHP-пакет

Каркас качественного PHP-проекта задается пирамидой трех компонентов:
* инструменты;
* конфигурация;
* исходный код, тесты и документация.

## PHP конференция в Сингапуре, прошедшая в конце августа

На конференции в большей степени обсуждались разные платформы: WordPress, Drupal, Magento. Мне показалась конференция скучной. Смотрел выборочно и на большой скорости. Тем не менее пара докладов позабавили и я их вынес в этот подкаст.

## Тимоти Чендлер про [опыт замены PHP на Hack](https://www.youtube.com/watch?v=wXN-PNk6lHw)

Доклад о главных преимуществах языка Hack. Hack — это PHP со статической типизацией. Для работы Hack нужен установленный HHVM. Заметные отличия Hack от PHP:
* обязательная типизация переменных (+`void`; введен в PHP7.1);
* дженерики: параметризация типов;
* `Vector`, `Map`, `Pair`, `Set` (+Imm*: имьютаблы);
* тайп алиасинг;
* операторы: пайп-оператор (|>), лямбда (==>);
* nullable type (?bool);
* async-функции + await + Awaitable<void>, но не мультитрединг;
* tuples (кортежи);
* enums;
* XHP: что-то вроде JSX;
* аттрибуты (аннотации как часть кода);
* [хорошая документация](https://docs.hhvm.com/hack/).

[Сравнение производительности Hack и PHP](http://benchmarksgame.alioth.debian.org/u64q/hack.html) в решении одинаковых задач. Ресурс может быть полезен для сравнительного анализа синтаксиса языков. Но реализация ужасная местами. В Scala например код запилен не в функциональном, а в императивном виде. Не объективный источник. Может кто подскажет ресурс с одинаковыми задачами и изящным кодом на разных языках?

## Демиан Сеги [о машинном обучении на PHP](https://www.youtube.com/watch?v=s5ogi_ACIeE&index=17&list=PLECEw2eFfW7hq_1TyZn5UtMw5KOoZARJP)

Используете ли вы нейронные сети? Отличный вводный материал про машинное обучение и как его можно применить на PHP. Так сложилось, что PHP не оказался среди стандартного тулсета в академических кругах. Из интерпретируемых языков более по вкусу пришелся Python, поэтому интеграция со Spark’ом есть на Python, но нет на PHP. Тем не менее, есть [расширение](https://github.com/bukka/php-fann) (FANN = Fast Artificial Neural Network) для PHP, позволяющее реализовать простую нейронную сеть. Нейронная сеть может пригодиться, когда описать алгоритмически некую задачу проблематично: слишком много условий и их определенное соотношение приводит к некому результату. Вместо того, чтобы писать все эти условия лучше дать машине это сделать за нас. Мы кормим некий алгоритм данными и говорим, что набор данных X1 — это результат Y1, а набор данных X2 соответствует Y2. Классическая задача классификации. Докладчик раскрыл пошаговый процесс тренировки и применения нейронной сети на PHP для подобной задачи, т.н. supervised learning. Материал будет интересен тем, кто имеет очень отдаленные представления о том, что такое ML.

## Премшри Пилаи из Etsy о Continuous Deployment

Пожалуй самым главным открытием доклада стал блог компании Etsy: <https://codeascraft.com/>.