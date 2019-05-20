# Лабораторная работа №3
Подготовил Кифа Евгений, студент группы TI-164

## Задание
Целью данной лабораторной работы было имплементировать 5 поведенческих паттернов.

## Использованные поведенческие паттерны
1. _Template Method_
2. _Iterator_
3. _Strategy_
4. _Command_
5. _Observer_

## _Template Method_
Шаблонный метод — это поведенческий паттерн проектирования, который определяет скелет алгоритма, перекладывая ответственность за некоторые его шаги на подклассы. Паттерн позволяет подклассам переопределять шаги алгоритма, не меняя его общей структуры.

![alt text](https://refactoring.guru/images/patterns/content/template-method/template-method.png "Logo Title Text 1")

## _Iterator_
Итератор — это поведенческий паттерн проектирования, который даёт возможность последовательно обходить элементы составных объектов, не раскрывая их внутреннего представления.

![alt text](https://refactoring.guru/images/patterns/content/iterator/iterator.png "Logo Title Text 1")

## _Strategy_
Стратегия — это поведенческий паттерн проектирования, который определяет семейство схожих алгоритмов и помещает каждый из них в собственный класс, после чего алгоритмы можно взаимозаменять прямо во время исполнения программы.

![alt text](https://refactoring.guru/images/patterns/content/strategy/strategy.png "Logo Title Text 1")

## _Command_
Команда — это поведенческий паттерн проектирования, который превращает запросы в объекты, позволяя передавать их как аргументы при вызове методов, ставить запросы в очередь, логировать их, а также поддерживать отмену операций.

![alt text](https://refactoring.guru/images/patterns/content/command/command.png "Logo Title Text 1")

## _Observer_
Наблюдатель — это поведенческий паттерн проектирования, который создаёт механизм подписки, позволяющий одним объектам следить и реагировать на события, происходящие в других объектах.

![alt text](https://refactoring.guru/images/patterns/content/observer/observer.png "Logo Title Text 1")

## Решение
В моём проекте реализовано несколько классов:
1. _PotionTemplate_  - реализуется с помощью Template method
2. _Menu_ - реализуется при помощи Iterator
3. _CookStrategy_ - использует Strategy
4. _Command_ -  реализуется при помощи Command
5. _Client_- использует Observer 


![alt text](https://i.redd.it/1sv940xe861z.png "Logo Title Text 1")  

В таверну заходит игрок, который может заказать зелья разных видов. Зелья могут быть приготовлены используя разные стратегии. Также, хозяин таверны был на столько добр в тот день, что если игрок закажет больше чем пять зелий - получит скидку 7 процентов.

*__Iterator Design Pattern__* -  предоставляет доступ к объектам в базовом представлении без предоставления доступа к самому представлению. В моём приложениие есть potionCollection  и potionIterator, и для того чтобы вывести на экран меню создаётся potion collection, который состоит из всех видов зелий которые может предоставить игроку хозяин таверны, а далее используя iterator выводится меню на экран.

 ![alt text](screens/iterator.PNG "Logo Title Text 1")  
 ![alt text](screens/iterator2.PNG "Logo Title Text 1")

*__Template Method Pattern__* - определяет схему или каркас операции, но оставляет определенные шаги, которые должны быть определены подклассами.
Зелья готовятся исходя их следующих шагов: GetIngredients(), Bake(), Pour() , и так как процедура разлива зелий одна и та же для всех видов зелий, она не определена как абстрактный метод, и предоставляется имплементацию в базовом классе, для готовки и ингридиентов используются абстрактные классы, и предоставляется имплементация в child классах, которые наследуются от предыдущего. 


 ![alt text](screens/template.PNG "Logo Title Text 1")   
 
  *__Strategy Design Pattern__* - Зелья готовятся используя разные стратегии в зависимости от пожелания игрока. К примеру, в проекте есть ElixirofRevelationsPotion, и DraughtofWeaknessPotion. 
  
```csharp
 potion.Amount = amount;
 potion.Price = potion.Amount * potion.Price;
 potion.CookStrategy = new DraughtofWeaknessPotion();
```
  ![alt text](screens/strategy.PNG "Logo Title Text 1")  
 
 *__Command Design Pattern__* - в проекте реализован AddCommandClass который имплиментирует ICommand интерфейс. Он добавляет зелья в заказ игрока
  В коде это выглядит вот так: 
    ![alt text](screens/command.PNG "Logo Title Text 1") 
    
   *__ObserverDesignPatter__*-  используется когда существует отношение один-ко-многим между обьектами. Если один из обьектов изменён, обьект который был от него зависим автоматически будет проинформирован
   В данном проекте observer используется, чтобы сообщить игроку, что он получит скидку в 7 процентов, так как он заказал больше чем 5 зелий
   
       ![alt text](screens/observer.PNG "Logo Title Text 1") 

Вывод в консоль:    
       ![alt text](screens/ex1.PNG "Logo Title Text 1")  
       ![alt text](screens/ex2.PNG "Logo Title Text 1") 


  
