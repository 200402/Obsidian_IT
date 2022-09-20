# Имя
## Классификация паттерна 
#СтруктурирующийКлассыИОбъекты 

## Назначение 
Компонует объкты в древовидные структуры для представления иерархий "часть - целое". Позволяет клиентам единообразно трактовать индивидуальные и составные объекты.

## Мотивация


## Применимость


## Структура


## Участники
- Component - 
- Leaf - 
- Composite - 
- Client - манипулирует объектами композиции через интерфейс Component

## Отношения


## Результаты
### Нейтральное


### Плюсы


### Минусы


## Реализация


## Родственные паттерны
1. [[Chain of Responsibility (Цепочка обязанностей)]]
2. [[Composite (Компоновщик)]]
3. [[Flyweight (Приспособленец)]]
4. [[Iterator (Итератор)]]
5. [[Visitor (Посетитель)]]

## Комментарий



#Паттерн





# Компоновщик
## Задача
[[Паттерн]] Компоновщик (Composite) объединяет группы объектов в древовидную структуру по принципу "часть-целое и позволяет клиенту одинаково работать как с отдельными объектами, так и с группой объектов.

Образно реализацию паттерна можно представить в виде меню, которое имеет различные пункты. Эти пункты могут содержать подменю, в которых, в свою очередь, также имеются пункты. То есть пункт меню служит с одной стороны частью меню, а с другой стороны еще одним меню. В итоге мы однообразно можем работать как с пунктом меню, так и со всем меню в целом.

## Решение
```c#
class Client
{
    public void Main()
    {
        Component root = new Composite("Root");
        Component leaf = new Leaf("Leaf");
        Composite subtree = new Composite("Subtree");
        root.Add(leaf);
        root.Add(subtree);
        root.Display();
    }
}

abstract class Component
{
    protected string name;
 
    public Component(string name)
    {
        this.name = name;
    }
 
    public abstract void Display();
    public abstract void Add(Component c); 
    public abstract void Remove(Component c);
}

class Composite : Component
{
    List<Component> children = new List<Component>();
 
    public Composite(string name)
        : base(name)
    {}
 
    public override void Add(Component component)
    {
        children.Add(component);
    }
 
    public override void Remove(Component component)
    {
        children.Remove(component);
    }
 
    public override void Display()
    {
        Console.WriteLine(name);
 
        foreach (Component component in children)
        {
            component.Display();
        }
    }
}
class Leaf : Component
{
    public Leaf(string name)
        : base(name){}
 
    public override void Display()
    {
        Console.WriteLine(name);
    }
 
    public override void Add(Component component)
    {
        throw new NotImplementedException();
    }
 
    public override void Remove(Component component)
    {
        throw new NotImplementedException();
    }
}
```


## Результаты
### Плюсы
1. Предоставляет все для отображения сильно вложенных структур объектов.
2. Понятный программный код.
3.  Легко расширять
### Минусы
1. Реализация компонентных интерфейсов очень сложна.
2. Последующая корректировка составных элементов сложна и обременительна для реализации.
## Часто используется с...
1. [[Iterator (Итератор)]]
2. [[Visitor (Посетитель)]]