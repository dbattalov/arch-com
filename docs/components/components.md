# Компонентная архитектура
<!-- Состав и взаимосвязи компонентов системы между собой и внешними системами с указанием протоколов, ключевые технологии, используемые для реализации компонентов.
Диаграмма контейнеров C4 и текстовое описание. 
Подробнее: https://confluence.mts.ru/pages/viewpage.action?pageId=375783368
-->
## Контейнерная диаграмма

```plantuml
@startuml
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml

AddElementTag("microService", $shape=EightSidedShape(), $bgColor="CornflowerBlue", $fontColor="white", $legendText="microservice")
AddElementTag("storage", $shape=RoundedBoxShape(), $bgColor="lightSkyBlue", $fontColor="white")

Person(pbc, "Докладчик", "Персона, которая хочет выступить на конференции с докладом по теме")
Person(adm, "Администратор оргкомитета", "Представитель оргкомитета, который рецензирует доклады и составляет расписание")
Person(usr, "Слушатель", "Участник конференции")

System_Boundary(ibs, "Обработка Заявок на Доклад") {
   Container(lecture_service, "Заявки на Доклад", "Java, Spring Boot", "Сервис обработки заявок на Доклад")       
   ContainerDb(lecture_db, "Одобренные доклады", "PostgreSQL", "Хранение докладов")
}

System_Boundary(cnf, "Проведение конференции") {
   ContainerDb(programm_db, "Доклады конференции", "PostgreSQL", "Хранение докладов")
   Container(access_demo, "Доступ к Демонстрации", "", "")
   Container(access_broadcast, "Доступ к Просмотру", "", "")   
   Container(feetback, "Оценка выступления", "", "")    
}

System_Boundary(ppt, "Компоновка программы конференции") {
   Container(conference_program, "Программа конференции", "", "") 
   ContainerDb(conference_db, "Расписание", "PostgreSQL", "Хранение запланированных словов для конференций")
}

System_Ext(antp, "Антиплагиат", "Российская система обнаружения текстовых заимствований")  
System_Ext(es, "Почтовый сервис", "Сервис отпправки e-mail сообщений")



Rel(pbc, lecture_service, "Прием заявки на сайте", "HTTPS")
Rel(lecture_service, lecture_db, "Допуск доклада", "")
Rel(adm, lecture_service, "Обработка заявки", "")
Rel(lecture_service, es, "Отправить уведомлени по e-mails", "SMTP")
Rel(es, pbc, "Обратная связь по заявке", "SMTP")
Rel(lecture_service, antp, "Запрос проверки", "")
Rel(antp, lecture_service, "Результат проверки", "")

Rel(conference_program, programm_db, "Повестка конференции на сегодня", "")

System_Ext(yt, "Видеосервис", "Видеосервис для проведения онлайн-трансляций")
System_Ext(es, "Почтовый сервис", "Сервис отпправки e-mail сообщений")

Rel(pbc, access_demo, "Выступление с докладом", "")
Rel(usr, access_broadcast, "Просмотр выступления", "")
Rel(usr, feetback, "Оценить выступление", "SMTP")
Rel(feetback, es, "Отправить уведомлени по e-mails", "SMTP")
Rel(es, pbc, "Обратная связь по докладу", "SMTP")
Rel(access_demo, programm_db, "Права на просмотр", "")
Rel(access_broadcast, programm_db, "Права на трансляцию", "")


Rel(access_demo, yt, "Трансляция выступления", "")
Rel(access_broadcast, yt, "Просмотр выступления", "")



Rel(adm, conference_program, "Составление программы из докладов", "")
Rel(conference_db, conference_program, "Свободны слоты проведения", "")


Rel(conference_program, lecture_db, "Тематика конференции", "")

Rel(feetback, programm_db, "Обратная связь по Докладу", "")

Rel(programm_db, access_demo, "Программа", "")
Rel(programm_db, access_broadcast, "Программа", "")


SHOW_LEGEND()
@enduml
```

## Список компонентов
| Компонент             | Роль/назначение                  |
|:----------------------|:---------------------------------|
| *Название компонента* | *Описание назначения компонента* |