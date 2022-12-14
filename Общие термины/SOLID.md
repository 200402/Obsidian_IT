# Принцип единственной ответственности (single responsibility principle)
Для каждого класса должно быть определено единственное назначение. Все ресурсы, необходимые для его осуществления, должны быть [[Инкапсуляция |инкапсулированы]] в этот класс и подчинены только этой задаче.

# Принцип открытости/закрытости (open-closed principle)
Классы должны  быть  открыты для расширения, но закрыты для модификации.
В класс можно добавлять новый функциоонал, но менять старый - не желательно.

# Принцип подстановки Лисков (Liskov substitution principle)
Наследуемый класс должен дополнять/расширять класс родителя, а не замещать его.

# Принцип разделения интерфейса (interface segregation principle)
Интерфейсы должны использоваться на 100%. Если необходимо реализовывать функции интерфейся, которые потом не будут использоваться, то это будет нарушением этого принципа

# Принцип инверсии зависимостей (dependency inversion principle)
1. Абстракции не должны подстраиваться под реализацию, реализация должна подстраиваться под особенности абстракций
2. Изменения в модулях нижнего уровня не должны ломать функционал модулей верхнего уровня.