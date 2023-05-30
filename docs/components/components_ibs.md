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


System_Boundary(ibs, "Обработка Заявок на Доклад") {
   Container(lecture_service, "Заявки на Доклад", "Java, Spring Boot", "Сервис обработки заявок на Доклад")    
   Container(lecture_good, "Одобренные доклады", "", "Хранение запланированных словов для конференций")   
   ContainerDb(lecture_db, "Доклады", "PostgreSQL", "Хранение докладов")
}

Container(conference_program, "Программа конференции", "")  
System_Ext(antp, "Антиплагиат", "Российская система обнаружения текстовых заимствований")  
System_Ext(es, "Почтовый сервис", "Сервис отпправки e-mail сообщений")



Rel(pbc, lecture_service, "Прием заявки на сайте", "HTTPS")
Rel(lecture_service, lecture_good, "Допуск доклада", "")
Rel(lecture_good, lecture_db, "Хранение доклада", "")
Rel(adm, lecture_service, "Обработка заявки", "")
Rel(lecture_service, es, "Отправить уведомлени по e-mails", "SMTP")
Rel(es, pbc, "Обратная связь по заявке", "SMTP")
Rel(lecture_service, antp, "Запрос проверки", "")
Rel(antp, lecture_service, "Результат проверки", "")

Rel(lecture_good, conference_program, "Получение одобренных докладов", "")


SHOW_LEGEND()
@enduml
```

## Список компонентов
| Компонент             | Роль/назначение                  |
|:----------------------|:---------------------------------|
| *Название компонента* | *Описание назначения компонента* |