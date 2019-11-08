# fake-api

�� ������������� ���������������� ����� FakeAPI (��� ����� ������, � ������ ��������� � �������). ��������� �������� ������������� json-server, ���� �� �� ������� ��� ������ ��������� ������� � ��� �������� - ������ �����.

��������������:
- ��� ���������� ������������� - ���������� �� ����������� json-server � json-���� � �������
- �������� ��� ���������� �� ������������� - json-server, ���������� � Docker-���������
- ���� ����������� - ������ ����� � FakeAPI (�� ������� ������� ��� �� ���������). �������� ����������� ��� ������� ������

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

- apisprout - ����� ����������, �� �� ���� �������. ������ ����� ��� �������. �������� � ����� �����������������, ����� � ���� ��������� (?)
- prizm - https://stoplight.io/p/docs/gh/stoplightio/prism/README.md
- connexion - https://connexion.readthedocs.io/

������, � ������ �� ���� ������������ json-schema ��� ���������. ����������� ������ ������� ���-�� �������������� ��� ���������, ������ �����������.
? https://express-validator.github.io/docs/
? ��� ���� ������ ��� ���������, ����� �����.


https://github.com/anttiviljami/openapi-backend

https://habr.com/ru/post/467099/#link_swagger
��� ���������� swagger � Hapi (express.js app?)

==== ��������
https://apisyouwonthate.com/blog/the-many-amazing-uses-of-json-schema-client-side-validation
https://assertible.com/blog/testing-and-validating-api-responses-with-json-schema
https://community.smartbear.com/t5/SoapUI-Open-Source/Schema-Validation-in-Mock-services/td-p/3795
https://apisyouwonthate.com/blog/server-side-validation-with-api-descriptions
https://bxcodec.io/posts/utilize-open-api-3-for-the-faster-software-development-process/

==== ������ ������
���-�� ��� json-����� �� ����������� - https://vk.com/dev/json_schema
https://github.com/JamesNK/Newtonsoft.Json - ����� �����