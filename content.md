# **Контекст решений**

```plantuml
@startuml
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml

Person(admin, "Администратор")
Person(moderator, "Модератор")
Person(user, "Пользователь")

System(conference_site, "Магазин", "Веб-сайт для покупки товаров")



Rel(admin, conference_site, "Просмотр, добавление и редактирование информации о товарах, пользователях и их корзинах")
Rel(moderator, conference_site, "Модерация товаров, пользователей и их корзин")
Rel(user, conference_site, "Регистрация, просмотр товаров, редактирование корзины")



@enduml
```

## **Назначение систем**
| Система | Описание |
|---|---|
|Магазин|Веб-интерфейс, обеспечивающий доступ к информации о товарах магазина. Бэкенд сервиса реализован в виде микросервисной архитектуры|
