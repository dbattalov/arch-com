## Здесь должно быть название ADR
<!-- Название ADR состоит из [ADR.###] [Коротко суть принятого решения] -->
[ADR.02][Выбор интеграционного взаимодействия]

* Статус: Принято
* Владелец: dbattalov@mtsbank.ru

## Контекст
<!-- Описание проблемы, требующей решения, причин, побудивших принять решение, ограничений, действовавших на момент принятия решения -->
В новой проектируемой системе необходимо передавать информацию по докладчикам и темам.  

## Варианты решения
<!-- Описание рассмотренных вариантов c их плюсами и минусами -->
Кретерии выбора - раширяемость функционала и наличие компетенций на рынке.

### Вариант 1. Название варианта
<!-- Описание варианта 1 -->
Использовать в качестве решения Интеграцию через Базу Данных.
* **Плюсы**
  * Универсальное решение.
  * Простота разработки.
* **Минусы**
  * Техрадар - "Запрещено"
  * Сложность работы с большим объемом.

### Вариант 2. Название варианта
<!-- Описание варианта 2 -->
Использовать интеграционную платформу RabbitMQ.
* **Плюсы**
  * Техрадар - "Рекомендовано"
  * Наличие специалистов на рынке и компетенции в команде.
  * Официальная поддержка большого кол-ва языков.
* **Минусы**
  * Нет надежного кластерного решения без потери данных
  * отсутствие в базовом механизме возможности настройки работы с очередью нескольких потребителей
  * Низкая производительность 

## Решение
<!-- Описание выбранного решения. Решение должно быть сформулировано чётко ("Мы используем...", "Мы не используем", а не "Желательно.." или "Предлагается..."). 
Должна быть понятна связь между решением и проблемой, почему выбрали именно это решение из вариантов -->
В качестве интеграционного решения выбрано брокера RabbitMQ 

## Последствия
<!-- Положительные и отрицательные последствия (trade-offs). Арх. решения, которые потребуется принять как следствие принятого решения. Если решение содержит риски, то описано, как с ними планируют поступить (за счет чего снижать, почему принять). -->
Выбранное решение позволит в будущем подключать различные модули, реализованные на разных языках программирования, так как RabbitMQ официально поддерживает большинство популярных из них, а наличие компетенций на рынке позволит оказывать поддержку и развивать продукт.    
