# fake-api

Ќе программируем инфраструктурную часть FakeAPI (как можно дольше, в идеале нисколько и никогда). —тараемс€ обойтись возможност€ми json-server, если их не хватает или растут очевидные костыли и уже неудобно - мен€ем тулзу.

–аспростран€ем:
- дл€ локального использовани€ - инструкци€ по инсталл€ции json-server и json-файл с данными
- веро€тно дл€ локального же использовани€ - json-server, завернутый в Docker-контейнер
- если потребуетс€ - делаем стенд с FakeAPI (на котором запущен тот же контейнер). Ќаверное потребуетс€ дл€ ћишиных тестов

==== json-server
+ создает все, что скажешь. 
+ умеет провер€ть id на уникальность, одинаковые не вставл€ет.

o надо научитьс€ генерировать id guid или запретить создавать счета без указани€ id
o  ак валидировать тело?  ак возвращать ошибки?
  вариант 1: middleware - точно можно, но будет немножко программизма
	https://expressjs.com/ru/guide/using-middleware.html
  вариант 2: json schema - пока непон€тно, как сделать. пока непон€тно, хватит ли ее
  посмотреть еще на: nginx, swagger

! пон€ть что за херн€ с кодировкой в контуровском гитлабе в md-файлах

==== 2019-11-08 ѕоизучал OpenAPI-тулзы
https://openapi.tools
https://apis.guru/awesome-openapi3/top100.html

пока без вн€тных достижений. json-server выгл€дит рабочим вариантом. Ќо:
- надо подключить валидацию по json-schema в middleware
- надо подключить swagger дл€ генерации док по схемам - непон€тно где
выгл€дит как много возни. ≈сть готовые комбайны дл€ такого.

- apisprout - много провозилс€, но не смог завести. —корее всего сам виноват. ѕочитать у более документированных, потом к нему вернутьс€ (?)
- prizm - https://stoplight.io/p/docs/gh/stoplightio/prism/README.md
- connexion - https://connexion.readthedocs.io/

ѕохоже, € просто не умею пользоватьс€ json-schema дл€ валидации. ѕопробовать совсем простое что-то отвалидировать без комбайнов, просто валидатором.
? https://express-validator.github.io/docs/
? еще были модули дл€ экспресса, найти снова.


https://github.com/anttiviljami/openapi-backend

https://habr.com/ru/post/467099/#link_swagger
как подключать swagger в Hapi (express.js app?)

==== ѕочитать
https://apisyouwonthate.com/blog/the-many-amazing-uses-of-json-schema-client-side-validation
https://assertible.com/blog/testing-and-validating-api-responses-with-json-schema
https://community.smartbear.com/t5/SoapUI-Open-Source/Schema-Validation-in-Mock-services/td-p/3795
https://apisyouwonthate.com/blog/server-side-validation-with-api-descriptions
https://bxcodec.io/posts/utilize-open-api-3-for-the-faster-software-development-process/

==== просто разное
что-то про json-схему во вконтактике - https://vk.com/dev/json_schema
https://github.com/JamesNK/Newtonsoft.Json - умеет схему