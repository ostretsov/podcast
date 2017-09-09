# PHP подкаст #14

Краткая [серия статей](https://blog.blackfire.io/author/jpauli) ([перевод](https://habrahabr.ru/company/mailru/blog/318008/) от Mail.ru Group) об оптимизациях в PHP7 от Джульена Паули. Blackfire взят в качестве профилировщика. Первое, о чем стоит упомянуть — это оптимизированные массивы. __Избегая ассоциативных массивов__ в угоду обычным — где индексом является число -, а также __сортируя ключи массива по возрастанию__ можно достичь существенного (до 10 раз) повышения производительности. Другая приятная особенность — экономия памяти, которую многие уже заметили. Дело в том, что в 7 версии переиспользуются контейнеры переменных. Единожды выделенная память для переменной может быть повторно использована. Также улучшена работа с encapsed-строками (строки в двойных кавычках/Heredoc): вместо последовательного довыделения буфера происходит его единовременная аллокация. Также существенно улучшена работа со статическими массивами. Теперь интерпретатор различает изменяемые и неизменяемые/immutable массивы (часть OPCache расширения), поэтому сейчас можно не переживать по поводу разных map-массивов. Также существенно улучшена работа со ссылками. В ранних версиях преобразование переменной в ссылку приводило к полному копированию содержимого переменной, поэтому оптимизации как в C/C++ не получалось. В новой версии дополнительных аллокаций памяти не случается в случае преобразования не ссылочной переменной в ссылку. Для погружения в детали лучше прочесть [статью](https://nikic.github.io/2015/05/05/Internal-value-representation-in-PHP-7-part-1.html) от Никиты Попова.

В преддверии выхода Laravel 5.4 Тейлор Отвел [поделился](https://twitter.com/taylorotwell/status/812295836193484800/photo/1?ref_src=twsrc%5Etfw) бенчмарком от blackfire. Hello world приложение с одним дефолтным маршрутом: 8мс, 1.8Мб RAM, 622 rps (mean).

У Laravel (5.3) Collections [появился](https://laravel-news.com/collections-partition) метод partition, который позволяет быстро разбить массив по некоторому признаку. Работа с коллекциями через collect в Laravel организована удобно: код становится значительно более читаемым, если вы используете map/reduce/другие методы, вместо array_map/array_reduce.

Примечательная статья об использовании [Transient](http://clojure.org/reference/transients) паттерна. Вся история вокруг [Money](http://martinfowler.com/eaaCatalog/money.html) типа, который захотелось сделать immutable. Незадача в том, что менеджерский абстрактный класс часто создает “ненужные” временные объекты типа Money. Это повышает требования к RAM. Автором был предложен паттерн Transient, который налагает на разработчика заботу о разделении режима mutable/immutable в сущностном классе. Хотите добавить несколько долларов к существующему объекту типа Money? Не проблема: вместо создания промежуточных объектов, мы можем мутировать текущий, но в определенном mutable-контексте, задаваемом единственным вспомогательным методом (вынесен в trait) withMutable(callable $fn). Функция $fn вызывается в mutable-контексте, задаваемом флагом mutable. Из недостатков — нужно переместить логику из абстрактного класса, который менеджерит манипуляцию immutable сущностями в сами сущности и писать по два обработчика: на случай mutable == true и mutable == false. Мутабельность становится контролируемой и в итоге все равно возвращает immutable объекты при снижении промежуточного инстанцирования.

PHP Australia получилась достаточно скучной. Один [доклад](https://www.youtube.com/watch?v=LEoo1MTQ47k) про тестирование вроде бы неплох, но код со слайдов читать нереально.

Ребята из RIPS — статический анализатор PHP кода для поиска уязвимостей — [опубликовали](https://blog.ripstech.com/2016/osclass-remote-code-execution-via-image-file/) очередной кейс с osClass CMS (что-то вроде WordPress, но несколько лучше, но все равно код выглядит печально). Я и не знал, что include статических файлов кто-то может делать. Поясню. Для вывода изображений вы можете использовать простой file_get_contents, например. Но можно извратиться и сделать include файла, предварив корректными вызовами header (что фиолетово для взломщика). При include файл выполняется, поэтому если запаковать код в EXIF-заголовок, то можно получить шел через shell_exec в несколько строк. Осталось только найти кусок кода, где инклюдится файл из запроса. Вообщем, то ощущение, будто читаешь журнал Хакер в 2009. И да, RIPS платный. Если у вас есть позитивный опыт его использования — отпишитесь в комментариях.

Очередной [рецепт](https://www.sitepoint.com/lets-kill-the-password-magic-login-links-to-the-rescue/). На этот раз как сделать passwordless-авторизацию на Laravel 5.2. Интересна сама стратегия авторизации по ключу на почту.

Забавное именование переменных в [math-php](https://github.com/markrogoyski/math-php).

Symfony 4 — выйдет в конце 2017 — будет требовать PHP7.0+.

Ребята с hh.ru подбили [статистику](https://habrahabr.ru/company/hh/blog/318450/) по вакансиям на разных технологиях. PHP вырос больше других технологий и среди русскоговорящей аудитории это самый востребованный язык. Я связываю это скорее с экономическим кризисом и тенденцию бизнеса сэкономить. Примечателен прорыв Swift и Golang.

Letsencrypt (бесплатные сертификаты) [объявил](https://letsencrypt.org/2016/11/01/launching-our-crowdfunding-campaign.html) кампанию по сбору средств на операционные расходы (месяц стоит 200 000 USD). 21М пользователей! Порадуйте Санту и подонатьте.

Если вы хотите программировать даже в новогоднюю ночь, [то вот неплохой способ сделать это в игровом формате](http://www.zachtronics.com/shenzhen-io/).