# Simulation
<img src="https://user-images.githubusercontent.com/36979003/127555058-81392df2-e99d-4119-aa59-2dbbed1001d1.png" width="400">
Программа для симуляции виртуальной жизни. На данный момент я разрабатываю базу для будущих экспериментов.

## Описание правил мира
Мир является клеточным полем. Данное поле замкнуто со всех сторон. Каждая клетка может являться живой или неживой, а также хранит в себе энергию.
Каждый ход у живых клеток отнимается определенное количество энергии. Если клетка живая, то она имеет собственный ген.
Ген представляет из себя последовательность комманд. Во время своего хода клетка выполняет одну команду из своего гена.
При выполнении большинства команд, внутренний счетчик команд клетки увеличивается на 1. При достижении определенного количества энергии, клетка начнет деление.
При делении она отдает половину своей энергии дочерней клетки. Дочерняя клетка создается в случайной ближайшей свободной клетке. Свободными клетками считаются в том числе и клетки по диагонали.
Если не удалось найти свободную клетку, то данная клетка умирает. Также с определенным шансом при делении у клетки может произойти мутация.
При мутации изменятся одна случайная команда в гене на другую случайную. У каждой клетки есть направление, в которое она смотрит. Всего доступно восемь направлений.
> Хочу обратить внимание на то, что правила в процессе разработки будут меняться.

## Описание команд
Номер команды соотвествует её коду в программе

### 0 - Осмотреться  
Переход на 1 команду вперед, если клетка впереди - еда или неродная* клетка.  
Переход на 2 команды вперед, если клетка впереди - родная.  
Переход на 3 команды вперед, если клетка впереди пуста.  
### 1 - Двигаться в текущем направлении  
Переход на 1 команду вперед при успехе.  
Переход на 2 команды вперед при неудаче.  
Клетка не может двигаться в клетку, занятую родной клеткой. Если клетка - неродная или мертвая, то она её съест и получит её энергию.  
### 2 - Повернуться по часовой стрелке  
### 3 - Повернуться против часовой стрелки  
### 4 - Выполнить фотосинтез  
За фотосинтез клетка получит определенное количество энергии.  
>*родной клетка считается, если её ген отличается менее чем на N генов.

## Использованные библиотеки
* [SFML](https://www.sfml-dev.org/)
* [Dear ImGui](https://github.com/ocornut/imgui)
* [JSON for Modern C++](https://github.com/nlohmann/json)
* [IconFontCppHeaders](https://github.com/juliettef/IconFontCppHeaders)

Также мною был использован шрифт [Roboto](https://github.com/googlefonts/roboto) и иконки из [Material design icons](https://github.com/google/material-design-icons).
