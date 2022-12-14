# Задание 2
## Наследование. Динамический полиморфизм. Абстрактные классы.

В работе осуществить тестирование и сборку с помощью cmake. Тестирование методов классов осуществлять с помощью gtest. Реализовать иерархию классов с абстрактным базовым классом (интерфейсом) согласно варианту (например, IBase). Во всех классах реализовать необходимые поля, конструкторы, методы получения значений полей и методы установки значений полей, а также организовать перегрузку нужных операторов. Конструкторы и методы обязательно должны проверять параметры на допустимость; в случае неправильных данных генерировать исключение или возвращать код ошибки.

Все классы иерархии дополнить статическими методами Load, считывающими информацию из потока ввода, создающими объект соответствующего класса и возвращающими указатель на созданный объект в виде указателя на абстрактный базовый класс (интерфейс):

```static IBase *Load(std::ifstream& stream);```

Для возможности сериализации (записи в поток) объектов созданной иерархии классов использовать порождающий шаблон “Абстрактная фабрика”, в которой создать реестр указателей на функции, формирующие (в результате чтения из потока) объекты – потомки абстрактного базового класса (интерфейса). Методы Load чтения из потока объекта каждого класса иерархии регистрируются в этом реестре. Реестр организовать в виде контейнера map стандартной библиотеки шаблонов STL с элементами ключ (имя класса) типа ```std::string``` – значение (указатель на функцию – статический метод Load класса).

Сериализацию (запись в поток) объектов созданной иерархии классов осуществлять с помощью специальной функции ```void Save()```.

Создать текстовый файл (например, ```objects.txt```), содержащий информацию об объектах различных классов иерархии (в одном файле в произвольном порядке построчно должна храниться информация об объектах разных классов иерархии – имя класса в виде строки и значения полей объектов).

Десериализацию (считывание из потока) объектов созданной иерархии классов осуществлять с помощью специальной функции ```void Load()```.

В тестах продемонстрировать и проконтролировать работу всех функций и методов всех классов иерархии.

Создать абстрактный класс – интерфейс IFunction (функция) с виртуальными методами вычисления значения функции y = f(x) в заданной точке x и вывода результата на экран. Создать производные классы: Ellipse (эллипс) и Hyperbola (гипербола).