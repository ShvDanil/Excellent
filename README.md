# Excellent — API для сервисов по поиску учеников и репетиторов
В этом репозитории описано решение кейса **Excellent — API для сервисов по поиску учеников и репетиторов**.
В нем будет информация о предлагаемой архитектуре и дизайне решения.
## Содержание
* [Описание доменной области](./README.md#Описание-доменной-области)
* [Use Cases](./README.md#Use-Cases)
* [Функциональные и нефункциональные требования](./README.md#Функциональные-и-нефункциональные-требования)
* [Компонентная модель](./README.md#Компонентная-модель)
* [Референсная архитектура и паттерны](./README.md#Референсная-архитектура-и-паттерны)

## Описание доменной области

### А. Введение
Из года в год увеличивается количество репетиторов, которые помогают подготовиться
- к первому классу;
- к поступлению в престижную школу; 
- к сдаче государственных экзаменов;
- к творческому испытанию в вузе;
- к олимпиаде;
- подтянуть успеваемость;
- изучить предмет углубленно.

Более того, растет и количество клиентов. По данным интернет-портала [Рамблер:](https://news.rambler.ru/sociology/43812515-eksperty-obyasnili-pochemu-k-2021-godu-v-rossii-vyrastet-potrebnost-v-repetitorah/?utm_content=news_media&utm_medium=read_more&utm_source=copylink) "70% российских школьников продолжают посещать репетиторов и курсы дополнительного образования после уроков", - а научно-образовательный портал [IQ.HSE](https://iq.hse.ru/news/361059490.html) сообщает о том, что приблизительный оборот рынка частного репетиторства за три года вырос практически на 70 млрд.руб. Это говорит о неотъемлемой потребности в дополнительных занятиях и показывает необходимость расширения и улучшения рынка сервисов, обеспечивающих учеников кадрами, а также необходимость в самих кадрах.

Из-за многих проблем крупнейшие сервисы и маркетплейсы теряют часть прибыли, а также потенциальную платежеспособную аудиторию. О каких проблемах идет речь?
* Платные пробные занятия и их низкая эффективность;
* несоответствие портфолио действительности;
* нежелание продолжать занятия после первой встречи;
* потеря времени - самого ценного ресурса 21 века;
* уменьшение коэффициента конверсии или отказ от пользования услугами сервиса.

Все это является ключевыми факторами, которые послужили идеей для нахождения различных решений. Цель данного программного обеспечения — создать API для сервисов по поиску учеников и репетиторов, которое позволит им экономить время и деньги. API будет подбирать репетитора на основе результатов вступительного тестирования ученика, что позволит сделать поиск максимально быстрым, удобным и эффективным. Используя это программное обеспечение, каждая платформа сможет грамотно выстроить взаимодействие между клиентами и репетиторами, повысить доходы и увеличить популярность на рынке.

Доступ к API будет осуществляться в качестве b2b (business to business) решения для конткретного сервиса, где сервис платит за пользование API.
 
### Б. Клиенты и пользователи
Потенциальные клиенты - это как небольшие онлайн-школы, так и крупные сервисы и маркетплейсы, специализирующиеся на предоставлении услуг в сфере образования. Всего в России насчитывается около сотни сервисов и онлайн-школ, задействованных в сфере образования. Каждая из них в настоящее время активно развивается и расширяет аудиторию своих потенциальных клиентов, а также работает над улучшением user-experience.
 
### В. Как устроен поиск репетитора и мэтчинг клиента с ним в настоящее время?
1. Клиент выбирает платформу, на которой он хочет подобрать себе репетитора.
2. Клиент регистрируется и составляет свою анкету.
3. Клиент ищет преподавателя и отправляет ему предложение о проведении вводного урока или же преподаватель предлагает клиенту воспользоваться своими услугами.
4. Клиент и преподаватель договариваются о проведении пробного занятия (либо за бесплатно с ограничением по времени, либо за цену одного занятия).
5. Если после проведения пробного занятия репетитор не подходит клиенту, клиент продолжает поиски репетитора.

Пункт *(2)* может влечь за собой несоответствие знаний клиента тому портфолио, которое составил он или его родители. Также можно заметить, что пункты *(3)*, *(4)* и *(5)* могут быть крайне времязатратными и иметь низкую эффективность, поэтому возникает необходимость в повышении эффективности мэтчинга между двумя сторонами. 

### Г. Окружение
Сервис, использующий наше API, обеспечит клиентам полный доступ к требуемым функциям. Так, пользователи, используя любое устройство (мобильный телефон, планшет, ноутбук, ПК), имеющее доступ к сервису, смогут выбрать необходимый предмет для написания проверочной работы, внести ответы в тестирующую систему или прикрепить файлы с решением при необходимости. В результате они получат результат написанной работы, а также увидят рекомендации для выбора преподавателя. Преподаватели также увидят рекомендации учеников для занятий.
Данный алгоритм работы имеет ряд преимуществ:
1. Пользователям не нужно устанавливать дополнительные расширения или скачивать дополнительное ПО для использования данной функции, поскольку она уже будет встроена в сервис;
2. Написание проверочной работы позволит внести актуальные данные о знаниях клиента в общую информацию о нем, что облегчит поиск и подбор преподавателя и сэкономит время обеих сторон;
3. API - гибкое и адаптивное решение для множества различных маркетплейсов, сервисов и онлайн-школ.

### Д. Конкуренты
Познакомившись с конкурирующими решениями, мы можем отметить следующие типы конкурентов: непрямые и косвенные.

К первому типу относятся компании, предлагающие смежные по своим свойствам услуги. Например, это компания Skyeng, мэтчинг клиентов и преподавателей которой происходит благодаря анализу психотипов студентов и учителей: "Мы ведём эксперименты по скорингу учителей с помощью психологических тестов во время отбора", - [заявляет](https://habr.com/ru/post/446970/) руководитель продакт-менеджмента детского направления онлайн-школы.

Второй тип - это компании, ориентирующиеся на одни и те же потребности клиентов одного рынка, то есть Ed-tech рынка. К примеру, это сервисы [Profi.ru](https://profi.ru), [Repetitor.ru](https://repetitor.ru), [Ассоциация репетиторов](https://repetit.ru/?roistat_visit=39748148) и другие.
 
### Е. Общая информация о сфере
1. Спрос на услуги частных репетиторов растет, соответственно требуются новые функции для улучшения работы сервисов по поиску преподавателей.
2. Проанализировав рынок, связанный с услугами в сфере образования, мы выявили нашу цель - увеличение денежного оборота сервисов по подбору репетиторов за счет улучшения качества их работы и сокращение времени, отводимого на поиск преподавателя. 
3. Примерный оборот рынка частного репетиторства по данным [IQ.HSE](https://iq.hse.ru/news/361059490.html) составляет 100 млрд.руб. Этот оборот - емкость всего рынка.

## Use Cases
**1.** Получение проверочной работы
---

**Описание:** Клиент получает проверочную работу в соответствии со своим запросом. 

**Предусловия:** Клиент авторизован (имеет доступ к сервису). 

**Результат:** Клиент получает вариант проверочной работы в формате JSON. 

**Триггер:** Клиент отправляет запрос сервису. 

**Успешный сценарий:**

1. Система получает запрос.

2. Система проверяет запрос на корректность. 

3. Система распаковывает тело запроса, получает данные об ученике и сохраняет их.

4. Система создает вариант проверочной работы в соответствии с данными об ученике.

5. Система формирует из проверочной работы ответ клиенту.

6. Система отправляет ответ клиенту.

**Альтернативные сценарии:** 

(2) Если запрос некорректный, сервис сообщает об ошибке клиенту. 

**2.** Создание проверочной работы.
---

**Описание:** Система создает проверочную работу.

**Предусловия:** Запрос клиента корректен.

**Результат:** Создается проверочная работа. 

**Триггер:** --

**Успешный сценарий:**

1. Система получает задания с сайта ФИПИ в соответствии с категорией ученика.

2. Система определяет тему каждого задания.

3. Система определяет правильный ответ каждого задания.

4. Система создает уникальный идентификатор проверочной работы.

5. Система добавляет проверочную работу в базу данных.

**Альтернативные сценарии:** 

(1) Если доступа к сайту ФИПИ нет или нужных заданий там не оказалось, система берет заготовленные задания из базы данных.

**3.** Получение ответов 
---

**Описание:** Клиент отправляет ответы ученика сервису.

**Предусловия:** Клиент успешно получил проверочную работу.

**Результат:** Система получает ответы ученика. 

**Триггер:** Клиент отправляет запрос с ответами ученика и уникальным идентификатором проверочной работы.

**Успешный сценарий:**

1. Система получает запрос.

2. Система проверяет запрос на корректность. 

3. Система распаковывает тело запроса, получает ответы ученика и сохраняет их.

4. Система получает по уникальному идентификатору проверечную работу из базы данных.

**Альтернативные сценарии:** 

(2) Если запрос некорректный, сервис сообщает об ошибке клиенту. 


**4.** Отправка результатов оценивания клиенту 
---

**Описание:** Систему отправляет результаты оценивания ученика в ответ на запрос с его ответами.

**Предусловия:** Запрос с ответами учениками был корректен.

**Результат:** Клиент получает результаты оценивания ученика. 

**Триггер:** --

**Успешный сценарий:**


1. Система сравнивает ответы ученика с правильными ответами проверочной работы, взятой из базы данных по уникальному идентификатору.

2. Система определяет знания ученика в каждой теме проверочной работы на основе сравнения из пункта (1).

3. Система составляет список тем проверочной работы и набранный учеником балл в этой теме.

4. Система формирует ответ из этого списка.

5. Система отправляет ответ клиенту.

**Альтернативные сценарии:** 

--
## Функциональные и нефункциональные требования
### А. Функциональные
1.	Система должна получать входные данные об ученике в формате JSON.
2.	Система должна обрабатывать входные данные об ученике и выбирать, какой КИМ необходимо сгенерировать.
3.	Система должна “парсить” сайт ФИПИ и генерировать КИМ по входным данным об ученике на основе заданий из “открытого банка”.
4.	Система должна отправлять на сервер КИМ в формате JSON.
5.	Система должна получать ответы в формате JSON на отправленный ранее тест.
6.	Система должна анализировать ответы на тест и проверять его.
7.	Система должна генерировать сообщение, в котором: указание на пробелы в знаниях, указание на хорошо освоенные темы, оценка тестирования по 100 бальной шкале.
8.	Система должна отправлять сообщение из п.7 серверу в формате JSON.
### Б. Нефункциональные
1.	Система должна проверять работу очень быстро. 
2.	Для работы с системой необходимо интернет-подключение.
3.	Все исходные файлы должны быть полностью задокументированы.
4.	Формат принимаемых и отправляемых сообщений должен быть указан в документации.
5.	Система должна быть конфиденциальна.
6.	Система не должна завершаться аварийно.
7.	Система должна работать в любом браузере и на любом устройстве.
8.	Система должны быть декомпозирована и позволять вносить изменения в код без ущерба.

## Компонентная модель

## Референсная архитектура и паттерны
Одними из ключевых вещей при разработке архитектуры служат референсная архитектура и паттерны, которые соответствуют исследуемой предметной области.
### Сервис-ориентированная архитектура (SOA)
Один из [основных источников](https://www.ibm.com/ru-ru/cloud/learn/soa) о сервис-ориентированной архитектуре определяет ее следующие базовые элементы:
* сервисы (Services);
* сервисная шина (Service Bus);
* сервисный репозиторий (Service Repository catalogue of services);
* безопасность SOA (SOA Security);
* управление SOA (SOA Governance).

Для того, чтобы показать значение каждого пункта в общем решении, проведем их анализ.

Существуют разные виды и типы сервисов, однако более подходящий для данного решения - **композиционный вспомогательный сервис (Composite Utility Service)**. Так как сервис композиционный, подразумевается, что он будет сочетать в себе несколько атомарных сервисов, не подлежащих дальнейшей декомпозиции. Это обеспечит сложную составную функциональность и позволит принимать данные, обрабатывать их и выдавать необходимый ответ для разных, отличающихся друг от друга запросов (request and response).

**Сервисная шина, или ESP (Enterprise Service Bus)** - связующее звено системы, обеспечивающее обмен информацией между клиентом и сервером. Она отвечает за оркестровку и маршрутизацию данных, поступивших с пользовательской стороны. 

С помощью **сервисного репозитория (Service Repository catalogue of services)** ESB направляет запрос в специальный сервис, который взаимодействует с другим сервисом (сервисами) и базой (базами) данных, чтобы подготовить данные для ответа.

Два заключительных раздела - **безопасность SOA (SOA Security) и управление SOA (SOA Governance)** регулируют правила безопасности и управления SOA, обеспечивая выполнение безопасной и корректной транзакции между клиентом и сервером (API).

*<ins>[Схематичное представление взаимодействия основных компонентов сервис-ориентированной архитектуры](https://github.com/ShvDanil/Excellent/blob/main/readme_images/SOA_scheme.png)</ins>*
![Схематичное представление взаимодействия основных компонентов сервис-ориентированной архитектуры](./readme_images/SOA_scheme.png)

Рассмотрев референсную архитектуру, стоит также описать **паттерны**, которые будут задействованы в ходе разработки API.

### Client / Server / Service pattern
Перед разработкой возникает вопрос, как возможно связать SOA с пользовательским интерфейсом сервиса, где клиентская сторона не поддерживает SOA или использует несовместимые с данной архитектурой технологии? 

Для этого используем **Client / Server / Service pattern**, позволяющий связать сервис с нашим API. Интеграция данного паттерна в качестве нового сервиса на серверной стороне позволит минимизировать воздействие на UI и иные существующие системы. Далее будет представлена схема данного паттерна, где роль нашего API изображает нижний слой server agent'а и его взаимодействие с сервервами А и В.

*<ins>[Общая схема паттерна](https://github.com/ShvDanil/Excellent/blob/main/readme_images/Client_Server_Service_pattern.png)</ins>*                          
![Client/Server/Service pattern](./readme_images/Client_Server_Service_pattern.png)

Однако изображение данного паттерна носит лишь обобщенный характер, так как он в общих чертах без какой-либо конкретики описывает методы взаимодействия API и сервиса. Для более детального описания взаимодействий перейдем к следующему паттерну, содержащему конкретную информацию о взаимодействии.

### Request / Reply pattern
Как мы можем выстроить взаимодействие клиент-сервер-API напрямую и без сложностей?

Для этого нам понадобится **Request / Reply pattern**, который полностью удовлетворяет требованиям по работе между указанными выше сторонами. Работа данного паттерна заключается в получении запроса и ответа на него. Когда сервис получает запрос от пользователя, он передает данные в соотвествующую подсистему API в должном формате, затем происходит моментальная синхронная обработка данных и их возврат в соответствующем формате в виде ответа на исходный запрос. Далее будет представлена схема данного паттерна, на которой изображен сервис, посылающий запрос на API и получающий ответ на него.

*<ins>[Общая схема паттерна](https://github.com/ShvDanil/Excellent/blob/main/readme_images/Request_Reply_pattern.png)</ins>*                          
![Request/Reply pattern](./readme_images/Request_Reply_pattern.png)


