# **�������� �������**

```plantuml
@startuml
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Container.puml

Person(admin, "�������������")
Person(moderator, "���������")
Person(user, "������������")

System(conference_site, "�������", "���-���� ��� ������� �������")



Rel(admin, conference_site, "��������, ���������� � �������������� ���������� � �������, ������������� � �� ��������")
Rel(moderator, conference_site, "��������� �������, ������������� � �� ������")
Rel(user, conference_site, "�����������, �������� �������, �������������� �������")



@enduml
```

## **���������� ������**
| ������� | �������� |
|---|---|
|�������|���-���������, �������������� ������ � ���������� � ������� ��������. ������ ������� ���������� � ���� �������������� �����������|
