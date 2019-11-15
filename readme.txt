# fake-api

Не программируем инфраструктурную часть FakeAPI (как можно дольше, в идеале нисколько и никогда). Стараемся обойтись возможностями json-server, если их не хватает или растут очевидные костыли и уже неудобно - меняем тулзу.

Распространяем:
- для локального использования - инструкция по инсталляции json-server и json-файл с данными
- вероятно для локального же использования - json-server, завернутый в Docker-контейнер
- если потребуется - делаем стенд с FakeAPI (на котором запущен тот же контейнер). Наверное потребуется для Мишиных тестов


== Шкарин, 14.11
Пользуется RAML для дизайна API. Обсуждает и согласовывает с потребителями текстовое неформальное описание. 
Утверждает, что RAML для моделирования  API лучше. Но он его после начала реализации выкидывает.
Проблема проверки соответствия реализации спецификации ему известна, каких-то специальных действий по этому поводу не делает.
Настаивает на robustness-проектировании/развитии
Одна из команд практикует сравнение swagger-спек до/после новой версии. Ищут разрушающие изменения (Паша упоминал какие-то умные diff'ы, но видимо глазками)
Есть канал api.support в слаке.
Максим Васючков, Новосиб. Практикует, делает доклады на тему design-first.

== RAML
- postman умеет читать спеку в Raml
- вроде бы команда влилась в OAS3 и OAS3 содержит возможности RAML

== на завтра
[x] Шкарин
- дочитать доки стоплайта
[x] почитать спеки ребилла, понять, как они их используют. Пишут они их руками, design-first
- разобраться с динамической генерацией респонзов в призме
- поднять конвейер с json-server
- понять где кончается полезность моков

==== динамическая генерация респонзов в призме
ls -l
указание конкретного примера: __example в запросе. Поискать еще варианты, возможно в коде
https://community.stoplight.io/t/how-to-force-prism-mock-server-to-return-different-response-during-test/685/2

НЕ МОГУ ЗАПУСТИТЬ КАК ПРОКСИ



==== StopLight Studio и проба Design First по OpenApi 3
- SLS: не смог добиться генерации доки по спеке (только по маркдаунам). Отложил.
- SLS: плоховато с поддержкой кодировок, если не UTF-8 поможет
- SLS: поддержка гита (коммит) не в курсе про переводы строк
- SLS: не всегда перечитывает измененные файлы с диска, надо перезапускать ее
- никак не связаны (?) примеры из модели и примеры из респонза с этими моделями. Было бы логично сгенерировать пример респонза из примеров моделей
- непонятно, как мокать неуспешные сценарии - на все подряд просто возвращаются примеры
- SLS: не позволяет делать рефы для Path Parameters. Непонятно пока, это ограничение тулзы или openapi

https://habr.com/ru/post/419525/ опыт про RAML/OAS
Про OAS3: Отсутствие автогенерации примеров ответов запросов на основании описания их структур;

-----------------------

==== json-server
+ создает все, что скажешь. 
+ умеет проверять id на уникальность, одинаковые не вставляет.

o надо научиться генерировать id guid или запретить создавать счета без указания id
o Как валидировать тело? Как возвращать ошибки?
  вариант 1: middleware - точно можно, но будет немножко программизма
	https://expressjs.com/ru/guide/using-middleware.html
  вариант 2: json schema - пока непонятно, как сделать. пока непонятно, хватит ли ее
  посмотреть еще на: nginx, swagger

! понять что за херня с кодировкой в контуровском гитлабе в md-файлах

==== 2019-11-08 Поизучал OpenAPI-тулзы
https://openapi.tools
https://apis.guru/awesome-openapi3/top100.html

пока без внятных достижений. json-server выглядит рабочим вариантом. Но:
- надо подключить валидацию по json-schema в middleware
- надо подключить swagger для генерации док по схемам - непонятно где
выглядит как много возни. Есть готовые комбайны для такого.

guid - type: string, format: uuid, но это не стандарт. Можно еще паттерн добавить
.NET: Swashbuckle, NSwag


ПОЛУЧАЕТСЯ КАКАЯ-ТО ХЕРНЯ
попробовать завести connexion


- apisprout - много провозился, но не смог завести. Скорее всего сам виноват. Почитать у более документированных, потом к нему вернуться (?)
- prizm - https://stoplight.io/p/docs/gh/stoplightio/prism/README.md
  можно поставить как прокси перед json server
- connexion - https://connexion.readthedocs.io/
  вроде тоже можно как проки использовать
  https://github.com/hjacobs/connexion-example

- dredd - ломается на примерах от OpenApi, не полностью поддерживает v3.0
- microsoft/OpenAPI.NET - только парсеры для чтения/записи OpenAPI-спецификаций
- unmock, openapi-backend, OpenAPI Enforcer Middleware, https://github.com/isa-group/oas-tools?

Похоже, я просто не умею пользоваться json-schema для валидации. Попробовать совсем простое что-то отвалидировать без комбайнов, просто валидатором.
? https://express-validator.github.io/docs/
? еще были модули для экспресса, найти снова.


https://github.com/anttiviljami/openapi-backend

https://habr.com/ru/post/467099/#link_swagger
как подключать swagger в Hapi (express.js app?)

https://itnext.io/creating-a-java-spring-rest-service-from-an-openapi-3-0-definition-94fbd5b8aa9e
статья с большим примером openapi-спеки


==== Почитать
https://apisyouwonthate.com/blog - почитать
https://apisyouwonthate.com/blog/the-many-amazing-uses-of-json-schema-client-side-validation
https://apisyouwonthate.com/blog/server-side-validation-with-api-descriptions
 - примерно то, что я собрался сделать в json-server middleware
 - и оттуда еще есть ссылка на express-gateway.io, выглядит хорошо

https://assertible.com/blog/testing-and-validating-api-responses-with-json-schema
это SaaS с бесплатным планом - https://assertible.com

https://community.smartbear.com/t5/SoapUI-Open-Source/Schema-Validation-in-Mock-services/td-p/3795

https://bxcodec.io/posts/utilize-open-api-3-for-the-faster-software-development-process/
 - пример с apisprout

==== еще категория - mock-сервера
Node.js HTTP Server Mock - https://www.npmjs.com/package/mock-http-server
Nock - https://github.com/nock/nock
Почитать про них

==== просто разное
что-то про json-схему во вконтактике - https://vk.com/dev/json_schema
https://github.com/JamesNK/Newtonsoft.Json - умеет схему

https://github.com/APIs-guru/openapi-directory
какие-то примеры

==== немного мимо темы
про версионирование апи
https://apisyouwonthate.com/blog/api-versioning-has-no-right-way


==== опыт яндекс.кассы
https://habr.com/ru/company/yamoney/blog/347390/
- design-first (не рекомендуют code-first, когда спецификация API генерируется из существующей реализации)
- yaml (читабельнее json)
- спека и дока вместе
- для написания спек используют Atom text editor с linter-swagger plugin, Swagger Editor, JetBrains IDEA Swagger plugin
- проект содержит файл index.html с настройками инициализации Swagger-UI. Благодаря плагину Web Pages это позволяет отображать документацию в виде HTML. Таким образом, каждая ветвь репозитория отображает HTML-документацию онлайн, и на нее можно ссылаться из внешних систем и документов.

чем я.касса пользуется для валидации?

==== rebilly  :) https://www.rebilly.com/ - Rebilly - Cloud subscription billing partner
https://github.com/Rebilly/RebillyAPI/tree/master/spec - предположительно хороший пример спеки
дока сделана ReDoc - очень красиво. Заводится локально по их инструкции. А swagger-editor локально у них не завелся.
они публикуют результат редока в гитхаб.пейджес. А в гитлабе так получится?
??? как они валидируют?

https://rebilly.github.io/rebilly-js-sdk
 - есть разные среды запуска (Live, Sandbox)
 
https://github.com/Rebilly/RebillyUserAPI
 еще апи со спекой
 
 
==== Phil Sturgeon , WeWork
https://phil.tech/api/2018/03/30/openapi-and-json-schema-divergence/
пишут json-schema, валидируют и тестируют по ней. Потом используют ее как часть OpenAPI для генерации доков в Redoc.
точнее, их мастер-дата - json-schema последнего драфта, потом они ее даунгрейдят то версии, которую можно конкретнуть в OpenAPI

- speccy - валидация OpenAPI, собирает один файл со спекой, рендерит в redoc, поднимает сервер с ним.
 В ее же репозе есть конвертер json-to-openapi

https://phil.tech/api/2018/04/13/openapi-and-json-schema-divergence-solved/
вторая часть

https://apisyouwonthate.com/blog


==== к презентации
- не планировал исследований, но получилось так
api Rebilly - prj\FakeApi\RebillyAPI. 
NSwag - может сгенерировать клиента (ts/c#) по спеке
Postman MockServer
Postman API / Import 
 - Define и Generate Collection - генерирует коллекцию тестов по методам из спеки (и можно прогнать их по серверам, указанным в спеке). Умеет импортировать примеры (непонятно, как это использовать)
 - Develoop - регистрация группы мок-серверов (где они?)
 - Test - описания тест-сьютов и переход на онлайн-среду запуска (?)
   не разобрался до конца. Кажется, что это не работает в обе стороны - можно импортировать спеку и дальше использовать сгенерированное для богатых ручных тестов
   
- обоснование мок-сервера https://stoplight.io/p/docs/gh/stoplightio/prism/docs/guides/workflow.md
https://stoplight.io/blog/dont-code-fake-apis/
https://stoplight.io/blog/mock-api-test/
https://stoplight.io/blog/python-rest-api/


https://github.com/stoplightio/prism/issues/435 - упоминается возможность кастомных моков