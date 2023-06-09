# **Компонентная архитектура**
## **Компонентная диаграмма**

```plantuml
@startuml
!include  https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml

AddElementTag("microService", $shape=EightSidedShape(), $bgColor="CornflowerBlue", $fontColor="white", $legendText="microservice")
AddElementTag("storage", $shape=RoundedBoxShape(), $bgColor="lightSkyBlue", $fontColor="white")

Person(admin, "Администратор")
Person(moderator, "Модератор")
Person(user, "Пользователь")

System_Ext(web_site, "Клиентский веб-сайт", "HTML, CSS, JavaScript, React", $tags = "web_site")

System_Boundary(service_site, "Магазин") {
   Container(client_service, "Сервис авторизации", "C++", "Сервис управления пользователями", $tags = "microService")    
   Container(post_service, "Сервис товаров", "C++", "Сервис управления товарами", $tags = "microService") 
   Container(blog_service, "Сервис корзин", "C++", "Сервис управления корзинами", $tags = "microService")   
   ContainerDb(db, "База данных", "MySQL", "Хранение данных о товарах, пользователях и их корзинах", $tags = "storage")
   
}

Rel(admin, web_site, "Просмотр, добавление и редактирование информации о товарах, пользователях и их корзинах")
Rel(moderator, web_site, "Модерация товаров, пользователей и их корзин")
Rel(user, web_site, "Регистрация, просмотр товаров, редактирование корзины")

Rel(web_site, client_service, "Работа с пользователями", "localhost/account")
Rel(client_service, db, "INSERT/SELECT/UPDATE", "SQL")

Rel(web_site, post_service, "Работа с товарами", "localhost/catalog")
Rel(post_service, db, "INSERT/SELECT/UPDATE", "SQL")

Rel(web_site, blog_service, "Работа с корзинами ", "localhost/cart")
Rel(blog_service, db, "INSERT/SELECT/UPDATE", "SQL")

@enduml
```

## **Список компонентов**
### **Сервис авторизации**
- Создание нового пользователя
  - *входные параметры:* логин, пароль, имя, фамилия, email, обращение (г-н/г-жа)
  - *выходные параметры:* отсутствуют
  
- Поиск пользователя по логину
  - *входные параметры:* логин
  - *выходные параметры:* имя, фамилия, email, обращение (г-н/г-жа)
  
- Поиск пользователя по маске имени и фамилии
  - *входные параметры:* маска фамилии, маска имени
  - *выходные параметры:* логин, имя, фамилия, email, обращение (г-н/г-жа)

### **Сервис товаров**
- Создание товара
  - *входные параметры:* наименование товара, тип     товара, описание, производитель и цена
  - *выходные параметры:* идентификатор товара

- Получение списка товаров
  - *входные параметры:* отсутствуют
  - *выходные параметры:* массив товаров, в котором для каждого товара указаны наименование, тип, описание, производитель и цена

### **Сервис корзин**
- Добавление товара в корзину
  - *входные параметры:* идентификатор товара, логин
  - *выходные параметры:* отсутствуют

- Получение корзины для пользователя
  - *входные параметры:* логин
  - *выходные параметры:* массив товаров, содержащихся в корзине, для каждого из которых указаны наименование, тип, описание, производитель и цена