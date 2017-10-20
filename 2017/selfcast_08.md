# Selfcast #8

Начну с [отличного интервью Стивена Возняка][30] Познеру. Случайно? попало в поле зрения. Очень позитивно.

[30]: https://www.youtube.com/watch?v=cbtJ-IvDzGg

Посмотрел свежую конференцию fwdays Highload. Из всего рекомендую посмотреть только [первый доклад][11] от Никиты Галкина про микросервисную архитектуру.
Обещаю, что понравится. Оттуда взял [полезную подписку][10] на отобранные новости про микросервисы за неделю. И [awesome-репу][12] про микросервисы.

[10]: https://microserviceweekly.com/
[11]: https://www.youtube.com/watch?v=0Bd9QRfR0iA&t=470s
[12]: https://github.com/mfornos/awesome-microservices

И еще кое-что, но из другого доклада...

## Централизованный менеджмент паролей, сертификатов и т.д.
Удобно менеджерим все пароли, токены, сертификаты, API-ключи и т.д. с помощью [Vault от HashiCorp][1] Есть ACL, можно выдавать доступ на время, есть интеграция почти со всем (а если нет, то пишется за 10 минут).

> Vault secures, stores, and tightly controls access to tokens, passwords, certificates, API keys, and other secrets in modern computing. Vault handles leasing, key revocation, key rolling, and auditing. Through a unified API, users can access an encrypted Key/Value store and network encryption-as-a-service, or generate AWS IAM/STS credentials, SQL/NoSQL databases, X.509 certificates, SSH credentials, and more.

В сложной инфраструктуре может потребоваться неделя-две на интеграцию, зато никаких больше hardcoded секурных данных.

[1]: https://www.vaultproject.io/

## Контроль качества кода в Яндекс браузере
Хороший [доклад][2] про контроль качества кода при разработке Яндекс браузера. Заинтересовал [Sonarqube][3]. Легко интегрируется со всеми CI, делает код-инспекцию.
Понятно, что максимально от неё выигрывают языки со статической типизацией, но и для PHP/Python/JavaScript проект применим.
Есть у ребят автотесты через Espresso.  

[2]: https://www.youtube.com/watch?v=yu0gLSm_bTQ
[3]: https://www.sonarqube.org

## Масштабирование PHP-проектов
Разжился [любопытной книжкой][4] о том, как масштабировать PHP-проект.

[4]: https://www.scalingphpbook.com/

## Правильное улучшение в Symfony 3.4
[Теперь][5] можно комфортно делать autowiring. Определяем имена переменных/интерфейсы соответсвующим сервисами и получаем удовольствие.
Ради этого нужно быстро апаться во всех проектах. 
 
[5]: http://symfony.com/blog/new-in-symfony-3-4-local-service-binding

## Что такое CI?
Для сверки понимания обращаемся к [хорошему материалу][6].

[6]: https://www.thoughtworks.com/continuous-integration

## Почти свежий бэнчмарк PHP фреймворков
[Из бэнчмарка][7] вырисовывается картин лидеров:
* phalcon;
* slim;
* lumen;
* silex.

[7]: https://www.nixsolutions.com/blog/comparative-testing-php-frameworks/ 

https://www.nixsolutions.com/blog/comparative-testing-php-frameworks/

## Финишная прямая 

* DevOps culture (Dev + IT + QA) базворд;
* Рамбл-ток о том, почему не только про PHP.
* [Добротный подкаст][20] про AI, big data, etc.

[20]: https://dataskeptic.com/podcast/2017
