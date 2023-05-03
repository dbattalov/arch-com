# Контекст решения
<!-- Окружение системы (роли, участники, внешние системы) и связи системы с ним. Диаграмма контекста C4 и текстовое описание. 
Подробнее: https://confluence.mts.ru/pages/viewpage.action?pageId=375783261
-->
```plantuml
@startuml
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml

LAYOUT_WITH_LEGEND()

Person(pbc, "Докладчик", "Персона, которая хочет выступить на конференции с докладом по теме")
Person(adm, "Администратор оргкомитета", "Представитель оргкомитета, который рецензирует доклады и составляет расписание")
Person(usr, "Слушатель", "Участник конференции")
System(ibs, "Обработка Заявок на Доклад", "Обработка поступающих заявок от докладчиков")
System(ppt, "Компоновка программы конференции", "Составление программы конференции из допущенных докладов по расписанию")
System(cfn, "Проведение конференции", "Организация и проведение мероприятия с использованием видеосервиса")
System_Ext(es, "Почтовый сервис", "Сервис отпправки e-mail сообщений")
System_Ext(yt, "Видеосервис", "Видеосервис для проведения онлайн-трансляций")
System_Ext(antp, "Антиплагиат", "российская система обнаружения текстовых заимствований")


Rel(pbc, ibs, "Подача")
Rel(adm, ibs, "Рецензия")
Rel(ibs, es, "Отправить уведомлени по e-mails", "SMTP")
Rel(es, pbc, "Обратная связь по заявке", "SMTP")
Rel(ibs, antp, "Запрос проверки")
Rel(antp, ibs, "Результат проверки")


Rel(adm, ppt, "Компановка")

Rel(pbc, cfn, "Выступление")
Rel(usr, cfn, "Участие")
Rel(usr, cfn, "Обратная свзяь")
Rel(cfn, es, "Отправить уведомлени по e-mails", "SMTP")
Rel(es, pbc, "Обратная связь по докладу", "SMTP")
Rel(cfn, yt, "Трасляция выступления")


@enduml
```