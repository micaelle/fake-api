# fake-api

�� ������������� ���������������� ����� FakeAPI (��� ����� ������, � ������ ��������� � �������). ��������� �������� ������������� json-server, ���� �� �� ������� ��� ������ ��������� ������� � ��� �������� - ������ �����.

��������������:
- ��� ���������� ������������� - ���������� �� ����������� json-server � json-���� � �������
- �������� ��� ���������� �� ������������� - json-server, ���������� � Docker-���������
- ���� ����������� - ������ ����� � FakeAPI (�� ������� ������� ��� �� ���������). �������� ����������� ��� ������� ������

==== StopLight Studio
�� ���� �������� ��������� ���� �� ����� (������ �� ����������). �������.


-----------------------

==== json-server
+ ������� ���, ��� �������. 
+ ����� ��������� id �� ������������, ���������� �� ���������.

o ���� ��������� ������������ id guid ��� ��������� ��������� ����� ��� �������� id
o ��� ������������ ����? ��� ���������� ������?
  ������� 1: middleware - ����� �����, �� ����� �������� ������������
	https://expressjs.com/ru/guide/using-middleware.html
  ������� 2: json schema - ���� ���������, ��� �������. ���� ���������, ������ �� ��
  ���������� ��� ��: nginx, swagger

! ������ ��� �� ����� � ���������� � ������������ ������� � md-������

==== 2019-11-08 �������� OpenAPI-�����
https://openapi.tools
https://apis.guru/awesome-openapi3/top100.html

���� ��� ������� ����������. json-server �������� ������� ���������. ��:
- ���� ���������� ��������� �� json-schema � middleware
- ���� ���������� swagger ��� ��������� ��� �� ������ - ��������� ���
�������� ��� ����� �����. ���� ������� �������� ��� ������.

guid - type: string, format: uuid, �� ��� �� ��������. ����� ��� ������� ��������
.NET: Swashbuckle, NSwag


���������� �����-�� �����
����������� ������� connexion


- apisprout - ����� ����������, �� �� ���� �������. ������ ����� ��� �������. �������� � ����� �����������������, ����� � ���� ��������� (?)
- prizm - https://stoplight.io/p/docs/gh/stoplightio/prism/README.md
  ����� ��������� ��� ������ ����� json server
- connexion - https://connexion.readthedocs.io/
  ����� ���� ����� ��� ����� ������������
  https://github.com/hjacobs/connexion-example

- dredd - �������� �� �������� �� OpenApi, �� ��������� ������������ v3.0
- microsoft/OpenAPI.NET - ������ ������� ��� ������/������ OpenAPI-������������
- unmock, openapi-backend, OpenAPI Enforcer Middleware, https://github.com/isa-group/oas-tools?

������, � ������ �� ���� ������������ json-schema ��� ���������. ����������� ������ ������� ���-�� �������������� ��� ���������, ������ �����������.
? https://express-validator.github.io/docs/
? ��� ���� ������ ��� ���������, ����� �����.


https://github.com/anttiviljami/openapi-backend

https://habr.com/ru/post/467099/#link_swagger
��� ���������� swagger � Hapi (express.js app?)

https://itnext.io/creating-a-java-spring-rest-service-from-an-openapi-3-0-definition-94fbd5b8aa9e
������ � ������� �������� openapi-�����


==== ��������
https://apisyouwonthate.com/blog - ��������
https://apisyouwonthate.com/blog/the-many-amazing-uses-of-json-schema-client-side-validation
https://apisyouwonthate.com/blog/server-side-validation-with-api-descriptions
 - �������� ��, ��� � �������� ������� � json-server middleware
 - � ������ ��� ���� ������ �� express-gateway.io, �������� ������

https://assertible.com/blog/testing-and-validating-api-responses-with-json-schema
��� SaaS � ���������� ������ - https://assertible.com

https://community.smartbear.com/t5/SoapUI-Open-Source/Schema-Validation-in-Mock-services/td-p/3795

https://bxcodec.io/posts/utilize-open-api-3-for-the-faster-software-development-process/
 - ������ � apisprout

==== ��� ��������� - mock-�������
Node.js HTTP Server Mock - https://www.npmjs.com/package/mock-http-server
Nock - https://github.com/nock/nock
�������� ��� ���

==== ������ ������
���-�� ��� json-����� �� ����������� - https://vk.com/dev/json_schema
https://github.com/JamesNK/Newtonsoft.Json - ����� �����

https://github.com/APIs-guru/openapi-directory
�����-�� �������

==== ������� ���� ����
��� ��������������� ���
https://apisyouwonthate.com/blog/api-versioning-has-no-right-way


==== ���� ������.�����
https://habr.com/ru/company/yamoney/blog/347390/
- design-first (�� ����������� code-first, ����� ������������ API ������������ �� ������������ ����������)
- yaml (����������� json)
- ����� � ���� ������
- ��� ��������� ���� ���������� Atom text editor � linter-swagger plugin, Swagger Editor, JetBrains IDEA Swagger plugin
- ������ �������� ���� index.html � ����������� ������������� Swagger-UI. ��������� ������� Web Pages ��� ��������� ���������� ������������ � ���� HTML. ����� �������, ������ ����� ����������� ���������� HTML-������������ ������, � �� ��� ����� ��������� �� ������� ������ � ����������.

��� �.����� ���������� ��� ���������?

==== rebilly  :) https://www.rebilly.com/ - Rebilly - Cloud subscription billing partner
https://github.com/Rebilly/RebillyAPI/tree/master/spec - ���������������� ������� ������ �����
���� ������� ReDoc - ����� �������. ��������� �������� �� �� ����������. � swagger-editor �������� � ��� �� �������.
��� ��������� ��������� ������ � ������.�������. � � ������� ��� ���������?
??? ��� ��� ����������?

https://rebilly.github.io/rebilly-js-sdk
 - ���� ������ ����� ������� (Live, Sandbox)
 
https://github.com/Rebilly/RebillyUserAPI
 ��� ��� �� ������
 
 
==== Phil Sturgeon , WeWork
https://phil.tech/api/2018/03/30/openapi-and-json-schema-divergence/
����� json-schema, ���������� � ��������� �� ���. ����� ���������� �� ��� ����� OpenAPI ��� ��������� ����� � Redoc.
������, �� ������-���� - json-schema ���������� ������, ����� ��� �� ����������� �� ������, ������� ����� ����������� � OpenAPI

- speccy - ��������� OpenAPI, �������� ���� ���� �� ������, �������� � redoc, ��������� ������ � ���.
 � �� �� ������ ���� ��������� json-to-openapi

https://phil.tech/api/2018/04/13/openapi-and-json-schema-divergence-solved/
������ �����

https://apisyouwonthate.com/blog
