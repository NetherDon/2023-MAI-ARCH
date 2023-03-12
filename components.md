# **������������ �����������**
## **������������ ���������**

```plantuml
@startuml
!include  https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml

AddElementTag("microService", $shape=EightSidedShape(), $bgColor="CornflowerBlue", $fontColor="white", $legendText="microservice")
AddElementTag("storage", $shape=RoundedBoxShape(), $bgColor="lightSkyBlue", $fontColor="white")

Person(admin, "�������������")
Person(moderator, "���������")
Person(user, "������������")

System_Ext(web_site, "���������� ���-����", "HTML, CSS, JavaScript, React", $tags = "web_site")

System_Boundary(service_site, "�������") {
   Container(client_service, "������ �����������", "C++", "������ ���������� ��������������", $tags = "microService")    
   Container(post_service, "������ �������", "C++", "������ ���������� ��������", $tags = "microService") 
   Container(blog_service, "������ ������", "C++", "������ ���������� ���������", $tags = "microService")   
   ContainerDb(db, "���� ������", "MySQL", "�������� ������ � �������, ������������� � �� ��������", $tags = "storage")
   
}

Rel(admin, web_site, "��������, ���������� � �������������� ���������� � �������, ������������� � �� ��������")
Rel(moderator, web_site, "��������� �������, ������������� � �� ������")
Rel(user, web_site, "�����������, �������� �������, �������������� �������")

Rel(web_site, client_service, "������ � ��������������", "localhost/account")
Rel(client_service, db, "INSERT/SELECT/UPDATE", "SQL")

Rel(web_site, post_service, "������ � ��������", "localhost/catalog")
Rel(post_service, db, "INSERT/SELECT/UPDATE", "SQL")

Rel(web_site, blog_service, "������ � ��������� ", "localhost/cart")
Rel(blog_service, db, "INSERT/SELECT/UPDATE", "SQL")

@enduml
```

## **������ �����������**
### **������ �����������**
- �������� ������ ������������
  - *������� ���������:* �����, ������, ���, �������, email, ��������� (�-�/�-��)
  - *�������� ���������:* �����������
  
- ����� ������������ �� ������
  - *������� ���������:* �����
  - *�������� ���������:* ���, �������, email, ��������� (�-�/�-��)
  
- ����� ������������ �� ����� ����� � �������
  - *������� ���������:* ����� �������, ����� �����
  - *�������� ���������:* �����, ���, �������, email, ��������� (�-�/�-��)

### **������ �������**
- �������� ������
  - *������� ���������:* ������������ ������, ���     ������, ��������, ������������� � ����
  - *�������� ���������:* ������������� ������

- ��������� ������ �������
  - *������� ���������:* �����������
  - *�������� ���������:* ������ �������, � ������� ��� ������� ������ ������� ������������, ���, ��������, ������������� � ����

### **������ ������**
- ���������� ������ � �������
  - *������� ���������:* ������������� ������, �����
  - *�������� ���������:* �����������

- ��������� ������� ��� ������������
  - *������� ���������:* �����
  - *�������� ���������:* ������ �������, ������������ � �������, ��� ������� �� ������� ������� ������������, ���, ��������, ������������� � ����