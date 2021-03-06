# PHP подкаст #6

Позавчера вышел PHP7.1 RC5. 10 ноября выйдет последний RC6 и далее ждем официального стабильного релиза.

К релизу Symfony 3.2 в конце ноября будет также приурочено [дополнение](http://symfony.com/blog/new-in-symfony-3-2-csv-and-yaml-encoders-for-serializer). Добавлено два encoder’а в Serializer-компонент: CSV и YAML. Также возможна сериализация объекта. К объекту применяется serialize и полученная строка снабжается префиксом. Результат в CSV или YAML. Кстати, никогда не приходила в голову в YAML-конфигах хранить сериализованный объект.

Также в Console-компонент [добавлено](http://symfony.com/blog/new-in-symfony-3-2-console-improvements-part-3) пару новых фич: приватные команды и стилизация консольного текста. Приватная CLI-команда не отображается в списке всех доступных команд, но все же может быть выполнена. А среди дополнительных стилизаций стоит отметить ненавистный blink. Не используйте его пожалуйста :).

Улучшен Web Debug Toolbar. Это одна из крутейших вещей, которая облегчает разработку на Symfony. Среди нововведений появилась совместимость с [Content-Security-Policy](https://developer.mozilla.org/en-US/docs/Web/Security/CSP/Using_Content_Security_Policy) заголовком, VarDumper теперь используется для отображений содержимого переменных, а также небольшое улучшение в отображении ошибок формы.

Кстати, для тех, кто не в курсе — я тоже не был — Content-Security-Policy позволяет регулировать сторонние ресурсы, с которых можно загружать контент. Например, изображения могут подгружаться с разных ресурсов, а этим заголовком вы можете ограничить их спектр. Проблемы XSS все еще актуальны и этот инструмент — это еще один шаг в сторону их решения.

Среди замечательных фич в Symfony 3.2 добавлена полноценная поддержка переменных окружения. Под словом полноценная я имею в виду поддержку, при которой любые изменения этих переменных моментально используются в приложении. Таким образом Symfony-приложении проще стало привести в соответствие с [12 факторами software-as-a-service](https://12factor.net/) (см. принцип 3).

Девей Шафик [рассказал](https://daveyshafik.com/archives/70430-im-sorry.html), что в ближайшее время мы реже сможем его наблюдать на конференциях. Возможно, это и к лучшему и выйдет Zend Certification Guide для PHP7.

[Hamcrest PHP](https://github.com/hamcrest/hamcrest-php) может значительно улучшить читаемость тестов. Сама библиотека — это порт Hamcrest matcher, написанной на Java. Суть её в том, что тесты выглядят почти как естественные предложения на английском. Например, “assert that a variable is an instance of some class”. Проверка, написанная на Hamcrest PHP практически также будет писаться, плюс несколько пар скобок. Есть TestListener для PHPUnit, т.о. можно считать проверки для репортов PHPUnit (зелененькая статистика по завершению тестов). Сабж можно использовать также и в коде для теста переменных. Я использую beberlei/assert, но теперь серьезно подумываю мигрировать на Hamcrest, т.к. и в коде его можно эффективно использовать и в тестах. Посмотрите короткую презентацию: <https://www.youtube.com/watch?v=9TnKOnY9qI4>.

Не PHPUnit’ом единым. Atoum — другой любопытный [фреймворк для тестирования](https://www.sitepoint.com/testing-php-code-with-atoum-an-alternative-to-phpunit/). Миленький инструмент с котиками в консоли. Посмотреть можно, тем более, что его достаточно широко используют и есть интеграции для Blackfire и CI. Из заявленного кажется привлекательным параллельное выполнение тестов  из коробки. Немного цифр. Более 5000 комитов, более 50 контрибьюторов и почти 1000 звездочек [на гитхабе](https://github.com/atoum/atoum). Посмотреть стоит.

Я считаю, что для каждого инструмента своя ниша, но есть те, кто считает иначе. Всегда мечтали написать свою игру? Пожалуйста. Змейка в консоли: <https://www.sitepoint.com/howd-they-do-it-phpsnake-detecting-keypresses/>.

Кстати, код мало чем отличается от того, что вы можете прочитать в книгах вроде “Создание игр” от Андре Ламота. На C++ все то же самое.

Опять же из разряда странного, но полезного. <https://www.phparch.com/books/functional-programming-in-php/?utm_source=functionalphpcom2nded> — книга о ФП на PHP. Мы часто используем элементы ФП на PHP, например, функции высшего порядка. И все же PHP — в отличии от его сородича Hack lang’а — не хватает встроенных immutable структур данных для полного счастья. Тем не менее, ФП на PHP возможно начиная с PHP5.3. Рекурсия вам в помощь. Презентация автора для любопытных [прилагается](https://www.simonholywell.com/static/slides/2014-01-20/).

Еще больше странного? Пожалуйста! [Программирование на PHP на iPad’e](https://www.sitepoint.com/is-it-possible-to-write-and-run-php-code-on-an-ipad/). А также [моддинг Minecraft’а](https://www.sitepoint.com/modding-minecraft-with-php-buildings-from-code/).

Практики Continuous Integration нам уже более-менее знакомы. Многие проекты, в которых несколько разработчиков прибегают к автоматизации. Что же насчет Continuous Development’а? Неплохая [статья](https://mwop.net/blog/2016-10-24-watch-phpunit-with-node.html) на эту тему попалась на глаза про использование gulp для реагирование на изменения файловой системы и запуска вспомогательных утилит: php-cs-fixer, PHPUnit.

Примерно неделю назад закончился ZendCon 2016. Он длился 3 дня и там выступал даже Uncle Bob. Если появится видео, то обязательно сделаю обзорный подкаст конференции. Среди прочих сервисов был отмечен любопытный ресурс <https://cleancoders.com> (тот же Дядя Боб). Посмотрите список предлагаемого видео и интро — там немало интересных тем. Все платное, но не жалко.

Давайте немного [освежим](https://www.simonholywell.com/post/2016/10/importing-and-aliasing-php-functions/) то, как работают namespace. За рутиной кода забылась возможность включать функции при помощи ключевого слова use functions. Также слово namespace с последующими { и } заключает весь код в скобках в обозначенное именное пространство.

Также недавно вышла забавная штуковина Upsource 3.5 от JetBrains для удобного код ревью. Глянуть [стоит](https://www.jetbrains.com/upsource/).

Любопытный сервис, о котором по крайней мере стоит упомянуть [MS Text Analytics API](https://azure.microsoft.com/en-us/documentation/articles/machine-learning-apps-text-analytics/). Можно вытащить из текста его тему, терминологию, извлечь степень позитива/негатива текста. Заявлено, что поддерживается 120 языков, среди которых есть и [русский](https://azure.microsoft.com/ru-ru/services/cognitive-services/text-analytics/).

Ну и для развлечения можно почитать крайнюю статью на Хабре [о Sky проекте](https://habrahabr.ru/post/313884/). Главное не пытаться относиться к написанному серьезно и вы получите удовольствие :).