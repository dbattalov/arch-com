# Компонентная архитектура
<!-- Состав и взаимосвязи компонентов системы между собой и внешними системами с указанием протоколов, ключевые технологии, используемые для реализации компонентов.
Диаграмма контейнеров C4 и текстовое описание. 
Подробнее: https://confluence.mts.ru/pages/viewpage.action?pageId=375783368
-->
## Контейнерная диаграмма

```plantuml
@startuml
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml


Person(adm, "Администратор оргкомитета", "Представитель оргкомитета, который рецензирует доклады и составляет расписание")


System_Boundary(ppt, "Компоновка программы конференции") {
   Container(conference_program, "Программа конференции", "", "") 
   ContainerDb(conference_db, "Расписание", "PostgreSQL", "Хранение запланированных словов для конференций")
}

Container(lecture_good, "Одобренные доклады", "", "Хранение запланированных словов для конференций")
Container(programm_db, "Доклады конференции", "", "Хранение запланированных словов для конференций")

Rel(adm, conference_program, "Составление программы из докладов", "")
Rel(conference_db, conference_program, "Свободны слоты проведения", "")

Rel(lecture_good, conference_program, "Загрузка допущенных докладов", "")
Rel(conference_program, programm_db, "Выгрузка докладов конференций", "")


SHOW_LEGEND()
@enduml
```

## Список компонентов
| Компонент             | Роль/назначение                  |
|:----------------------|:---------------------------------|
| *Название компонента* | *Описание назначения компонента* |