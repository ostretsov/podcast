# PHP подкаст #8

Абстрагируемся от файлового хранилища, API-first, который приносит счастье, pthreads и холивары, жесткий Code Sniffer, виагру всем поисковым ботам, очень серьезный ClickHouse, рамбл talk о перспективах фреймворков.

Закончилась [серия](https://codeascraft.com/author/sschirmer/) из 3х статей от Etsy о том, как они уверовали в API-first подход и как он помог им мягко перейти на APIv3. Начинайте создавать API с контрактов!

RedHat наконец-то [собирается](https://blog.remirepo.net/post/2016/11/07/Red-Hat-will-provide-PHP-7.0-for-RHEL) выпустить RPM с PHP7.

[Gaufrette](https://knplabs.github.io/Gaufrette/) — библиотека для абстрагирования от конкретного файлового хранилища. Используя специальный класс Filesystem для манипулирования файлами вы можете впоследствии легко мигрировать на почти любое файловое хранилище. От локальной файловой системы до Amazon S3 и GridFS. Также упрощается тестирование, если использовать InMemory адаптер. Вообщем, must have вещь.

[Статья](https://habrahabr.ru/post/312662/) о разработке простого многопоточного (pthreads) сервера на PHP. pthreads-расширение — это реализация POSIX тредов. Предоставляются классы Threaded и несколько наследников. Наследуетесь от одного из классов Threaded и реализуете run-метод, который будет выполняться в отдельном потоке. Также есть Pool для менеджмента воркеров, которым можно сабмитить задачу.

Любопытная [статья](https://habrahabr.ru/post/312974/) о создании крохотного лендинга для организации подписки участников групп на неограниченные сообщения от сообщества.

[Один из вариантов](https://habrahabr.ru/company/SECL_GROUP/blog/313104/) использования Code Sniffer’а. Правила, правда, [предлагают](https://github.com/SECL-Group/phpcs-secl-standard) достаточно жесткие:
1. A function should be no longer than 15 lines of code;
2. The cyclomatic complexity of a function should not exceed 5;
3. Functions should not take more than 4 input arguments.

Мое мнение, что лучше цикломатическую сложность поднять до 10. К слову, в написании ядра линукса используются высокие цикломатические сложности из-за обилия if / else if / else if ….

Забавная [статья](https://habrahabr.ru/post/313332/) о bootleger-limiter.php. Называется она “Всем привет, я вебмастер и меня взломали”, а я бы назвал “Всем привет, я вебмастер и у меня виагра”. Скрипт работал только для поисковых ботов (скомпрометированный .htaccess) и подменял целиком контент отдаваемого сайта и поэтому в поисковой выдаче творились чудеса :).

Любопытная статья о ClickHouse (аналитическая столбцовая СУБД) от Яндекса. Летом Яндекс [опубликовал](https://habrahabr.ru/company/yandex/blog/303282/) этот инструмент, который они используют для Яндекс Метрики. [В статье](https://habrahabr.ru/company/smi2/blog/314558/) от СМИ2 компания выложила свой JS GUI для выполнения запросов к ClickHouse, а также PHP-драйвер. Кстати, ClickHouse использовался в ходе экспериментов на LHC для регистрации более 10 млрд событий с более чем 1000 аттрибутов у каждого. ClickHouse предоставляет SQL-like.  Если вам нужно сделать GROUP BY по триллиону записей, то посмотрите вспомните про ClickHouse :).

Немного рэмбл-токинга, навеянного [несвежим](https://www.youtube.com/watch?v=3AFR1BeiO2Q) докладом о ZF3.

Самые используемые PHP-фреймворки (*):
* Laravel (<https://github.com/laravel/framework/tree/5.3/src/Illuminate>)
* ZF
* Symfony
* Yii (<https://github.com/yiisoft/yii2/tree/master/framework>)
* PHPixie
* CodeIgniter (<https://github.com/bcit-ci/CodeIgniter/tree/develop/system/libraries>)

Мои ощущения от того, каким должен быть современный фреймворк:
* состоять из highly reusable компонентов и не быть монолитным;
* поощрять использовать сторонние компоненты на свой вкус (предоставлять микрофреймворк);
* иметь friendly документацию;
* реализовывать рекомендации от FIG;
* не мешать разработке продукта.

Пруфы:
* <https://www.linkedin.com/pulse/why-laravel-best-php-framework-2016-ramoliya-hitesh>;
* <https://www.webhostface.com/blog/popular-php-frameworks-2015/>;
* <https://www.sitepoint.com/best-php-framework-2015-sitepoint-survey-results/>.