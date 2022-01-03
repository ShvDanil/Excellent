# Excellent — API для сервисов по поиску учеников и репетиторов
В этом репозитории описано решение кейса **Excellent — API для сервисов по поиску учеников и репетиторов**.

## Содержание
* [Описание доменной области](-Excellent/tree/master/Описание доменной области)
* Use Cases
* Функциональные и нефункциональные требования
![](https://github.com/ShvDanil/-Excellent/blob/main/searching_photo.jpeg)

## Описание доменной области

### А. Введение
Из года в год увеличивается количество учеников и репетиторов, которые помогают школьникам готовиться к сдаче государственных экзаменов и улучшать свои навыки в ходе изучения различных предметов. [По данным интернет-портала Рамблер:](https://news.rambler.ru/sociology/43812515-eksperty-obyasnili-pochemu-k-2021-godu-v-rossii-vyrastet-potrebnost-v-repetitorah/?utm_content=news_media&utm_medium=read_more&utm_source=copylink) "70% российских школьников продолжают посещать репетиторов и курсы дополнительного образования после уроков", - а научно-образовательный портал [IQ.HSE](https://iq.hse.ru/news/361059490.html) сообщает о том, что приблизительный оборот рынка частного репетиторства за три года вырос практически на 70 млрд.руб. Это говорит о неотъемлемой потребности в дополнительных занятиях и показывает необходимость расширения и улучшения рынка сервисов, обеспечивающих учеников кадрами, а также необходимость в самих кадрах.

Из-за многих проблем крупнейшие сервисы и маркетплейсы теряют часть прибыли, а также потенциальную платежеспособную аудиторию. О каких проблемах идет речь?
* Платные пробные занятия и их низкая эффективность;
* несоответствие портфолио действительности;
* нежелание продолжать занятия после первой встречи;
* потеря времени - самого ценного ресурса 21 века;
* уменьшение коэффициента конверсии или отказ от пользования услугами сервиса.

Все это является ключевыми факторами, которые послужили идеей для поиска различных решений. Цель данного программного обеспечения — создать API для сервисов по поиску учеников и репетиторов, которое позволит им экономить время и деньги при поиске друг друга. API будет подбирать репетитора на основе результатов вступительного тестирования ученика, что позволит сделать поиск максимально быстрым, удобным и эффективным. Используя это программное обеспечение, каждая платформа сможет грамотно выстроить взаимодействие между клиентами и репетиторами, повысить доходы и увеличить популярность на рынке.

Доступ к API будет осуществляться в качестве b2b (business to business) решения для конткретного сервиса, где сервис платит за пользование API.
 
### Б. Клиенты и пользователи
Потенциальные клиенты - это как небольшие онлайн-школы, так и крупные сервисы и маркетплейсы, специализирующиеся на предоставлении услуг в сфере образования. Всего в России насчитывается около сотни сервисов и онлайн-школ, задействованных в сфере образования. Каждая из них в настоящее время активно развивается и расширяет аудиторию своих потенциальных клиентов, а также работает над улучшением user-experience.
 
### В. Окружение
Сервис, использующий наше API, обеспечит клиентам полный доступ к требуемым функциям. Так, пользователи, используя любое устройство (мобильный телефон, планшет, ноутбук, ПК), имеющее доступ к сервису, смогут выбрать необходимую проверочную работу для написания, внести ответы в тестирующую систему или прикрепить файлы с решением при необходимости. В результате они получат результат написанной работы, а также увидят рекомендации для выбора преподавателя. Преподаватели также увидят рекомендации учеников для занятий. 
Данный алгоритм работы имеет ряд преимуществ:
1.  Пользователям не нужно устанавливать дополнительные расширения или скачивать дополнительное ПО для использования данной функции, поскольку она уже будет встроена в сервис;
2. Написание проверочной работы позволит внести актуальные данные о знаниях клиента в общую информацию о нем, что облегчит поиск и подбор преподавателя и сэкономит время обеих сторон;
3. API - гибкое и адаптивное решение для множества различных маркетплейсов, сервисов и онлайн-школ.

 
### F. Tasks and procedures currently performed
•    Informing others about events: The organizer of the event (or someone who has heard about it) compiles information concerning an event and posts it so members of the organization can see it.
 
     One approach is to post the event on a physical bulletin board at a place that most users pass each day. In a large organization, this method is too unreliable due to the sheer volume of events.
 
Another approach is to send email and paper leaflets to all members of the staff without knowing exactly who will be interested. In some cases there are mailing lists to make event notification more selective, however mailing lists are often poorly maintained, so some people who might be interested never find out about an event.
 
In either approach, there is typically no central listing of available events and the information about an event is not presented in a standard fashion.
 
It can be useful to allow anybody to post and remove events, to ensure the information is current. However this can lead to duplication and inconsistency.
 
•    Informing oneself about events. At irregular intervals, employees check the list of upcoming events and seek more information about ones of interests.
 
When interested in an event, a user must check to see whether he or she has a schedule conflict. This is commonly done by maintaining a calendar. However there is a duplication of effort since all users have to keep their own records.
 
### G. Competing software
Several software tools exist that can manage events. However, since these are usually included as part of a larger system (e.g. agenda software, email software or teamwork software) they are quite complex to use. Hence they are not generally adopted by the entire staff.
These applications allow you to check for the availability of rooms and to book them. They might also maintain the personal schedules of staff members such that it is possible to find the best schedule for a given event.
 
### H. Similarities to other domains
There is a need to share many types of information in any organization, for example the telephone and office numbers of employees. In most cases, updating this information is the responsibility of one designated employee. This is also very similar to personal agenda, except that in the present case, only events of interest to everyone are added to the system.
 

## Use Cases

## Функциональные и нефункциональные требования
