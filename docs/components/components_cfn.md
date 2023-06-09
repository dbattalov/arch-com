# Компонентная архитектура
<!-- Состав и взаимосвязи компонентов системы между собой и внешними системами с указанием протоколов, ключевые технологии, используемые для реализации компонентов.
Диаграмма контейнеров C4 и текстовое описание. 
Подробнее: https://confluence.mts.ru/pages/viewpage.action?pageId=375783368
-->
## Контейнерная диаграмма

```plantuml
@startuml
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml


Person(pbc, "Докладчик", "Персона, которая хочет выступить на конференции с докладом по теме")
Person(usr, "Слушатель", "Участник конференции")


System_Boundary(cnf, "Проведение конференции") {
   Container(programm_db, "Доклады конференции", "", "")
   ContainerDb(programm_dbase, "Доклады", "PostgreSQL", "Хранение докладов")
   Container(access_demo, "Доступ к Демонстрации", "", "")
   Container(access_broadcast, "Доступ к Просмотру", "", "")   
   Container(feetback, "Оценка выступления", "", "")    
}

Container(conference_program, "Программа конференции", "")  

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



Rel(conference_program, programm_db, "Получение повестки конференции", "")
Rel(programm_db, programm_dbase, "Хранение доклада", "")
SHOW_LEGEND()
@enduml
```

## Список компонентов
| Компонент             | Роль/назначение                  |
|:----------------------|:---------------------------------|
| *Название компонента* | *Описание назначения компонента* |