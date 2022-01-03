# Excellent — API для сервисов по поиску учеников и репетиторов
В этом репозитории описано решение кейса **Excellent — API для сервисов по поиску учеников и репетиторов**. В этом репозитории будет описана предлагаемая архитектура и дизайн решения.

## Описание доменной области

### A. Введение
Из года в год увеличивается количество учеников и репетиторов, которые помогают школьникам готовиться к сдаче государственных экзаменов и улучшать свои навыки в ходе изучения различных предметов. [По данным интернет-портала Рамблер:](https://news.rambler.ru/sociology/43812515-eksperty-obyasnili-pochemu-k-2021-godu-v-rossii-vyrastet-potrebnost-v-repetitorah/?utm_content=news_media&utm_medium=read_more&utm_source=copylink) "70% российских школьников продолжают посещать репетиторов и курсы дополнительного образования после уроков", - а [научно-образовательный портал IQ.HSE](https://iq.hse.ru/news/361059490.html) сообщает о том, что приблизительный оборот рынка частного репетиторства за три года вырос практически на 70 млрд.руб. Это говорит о неотъемлемой потребности в дополнительных занятиях и показывает необходимость расширения и улучшения рынка сервисов, обеспечивающих учеников кадрами, а также необходимость в самих кадрах.


This document describes background information that has been gathered about events in organizations and how they are handled. This information is to be used to guide the development of software to automate the process of informing people of events.
 
### B. Glossary
• Event: A meeting, a social occasion or an activity involving a significant number of employees. Several categories of events have been identified:
-    Open event: An event that starts at a precise instant but with no predetermined duration. Meetings and celebrations often fall into this category.
-    Fixed event: An event that starts at a precise instant and with a predetermined duration. Course lectures and  seminars are examples of this kind of event.
-    Day events: An event associated with a particular day without precise start and end times. Birthday, thematic journey are such events.
-          Recurrent event: An event that occurs repeatedly on some regular schedule (for example daily, weekly or monthly). The event normally has a starting date and an ending date. Courses and social activities are often recurrent events.
-          Composite event: An event composed of several sub-events. For example, a training activity can be composed of a registration period (fixed event), a series of seminars (recurrent events), and a final evening celebration (open event). 
 
### C. General knowledge about the domain
•    Most events occur during working days.
•    Events are generally associated with a location (where the event is to be held).
•    The name of a contact person is often associated with an event. That person is the one that organize the event or that can give complementary information about the event.
•    Group of interest are often created to target more precisely peoples that might be interested by a certain event.
•    Outdated events are of little interest.
•    Each event has a title, a location and the name of a contact person associated with it.
•    Events may be seen by anyone within the organization, but there should be some control over posting events to reduce the risk of duplicate postings and other clutter.
 
### D. Clients and users
Potential clients are medium or large companies whose staff use computers to perform many kinds of daily work. Others impacted by the system will include:
•   Employees at all levels have an interest in events and are potential users of event manager software. These employees range from computer novices to sophisticated programmers; however they all have a computer on their desk, have access to the corporate intranet and know how to use a web browser. They have been exposed to and accept new technology but are subject to tight time constraints and have little time to learn and customize new software tools.
•    A system administrator normally manages the computer environment.
•   Technicians typically install software that must be available to all users.
 
### E. The environment
The actors all have a computer on their desks; it is most common for this to be MS-Windows based, but a significant minority of potential clients use other platforms.
 
A wide variety of software is installed on these computers, with each actor having a unique configuration. Some software may be installed on every computer using a site-wide license.
 
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
