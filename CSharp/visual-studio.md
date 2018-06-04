## Visual Studio

### Введение

Старайтесь пользоваться Visual Studio с последними обновлениями:

- Visual Studio 2015 - Update 3 (27 июня 2016);
- Visual Studio 2013 - Update 5 (20 июля 2015);
- Visual Studio 2012 - Update 5 (21 августа 2015);
- Visual Studio 2010 - Service Pack 1 (март 2011).

Узнать какое обновление уже установлено можно через диалог в меню Help -> About Visual Studio.


### Общее

NN. Быстрый поиск команд с помощью Quick Launch (Ctrl+Q). Введите текст и Visual Studio отобразит выпадаюший список команд или настроек содержащих его. Например, по слову font можно быстро открыть настройки шрифтов. По слову C# настройки редактора относящиеся к C#.

NN. Shift+Alt+Enter переключение в полноэкранный реэим и обратно. Visual Studio запоминает какие окна были открыты у вас в обоих режимах.


### Окно Solution Explorer

NN. Вверху Solution Explorer есть текстовое поле при вводе в которое дерево элементов фильтруется и отображает только элементы в имени которых есть введенный текст. Горячая клавиша Ctrl+;


### Редактор кода

NN. На саите studiostyl.es можно скачать готовые цветовые схемы для подсветки синтаксиса

NN. Текущую строку можно двигать вверх-вниз с помощью Alt+стрелка вверх/вниз. Это работает и для нескольких выделенных строк.

NN. Одну или несколько выделенных строк можно быстро двигать вправо и влево по позициям табуляции используя клавиши Tab и Shift+Tab.

NN. Текст в редакторе можно прокрутить не меняя позицию курсора путем удержания Ctrl и нажатия стрелок вверх или вниз

NN. Двойной щелчок мышью выделяет слово, тройной - строку.

NN. {VS05} Буфер обмена в Visual Studio содержит список последних скопированных элементов по которым можно перемащаться с помощью Ctrl+Shift+V. При этом текст как обычно вставляется из буфера обмена. При повторном нажатии вместо него вставляется следющий элемент. И так по кругу.

NN. Если включить переключатель «Enable virtual space» в настройках редактора, то курсор можно будет ставить в любое место в документе, а не только туда где введен текст.

NN. Для быстрого перехода к открывающей или закрывающей скобке используйте комбинаццию Ctrl+]

NN. Чтобы выделить содержимое внутри блока { } установите курсор на открывающую или закрывающую скобку и нажмите Ctrl+Shift+]

NN. Комбинация Ctrl+L удалит текущую строку и вставит её в буфер обмена. Удобство в том что строку не нужно выделять.

NN. Чтобы быстро закоментировать выделенный блок текста используйте комбинацию Ctrl+K+C, а для удаления символов комментария Ctrl+K+U. Соответствующие команды меню называются Comment Selection Uncomment Selection и находятся в меню Edit \ Advanced.

NN. Сниппеты кода (Code snippets)
Список сниппетов можно посмотреть в окне Tools \ Code Snippets Manager (Ctrl+K+B).
Типы: E - Expansion, SW - SurroundsWith.
Expansion-сниппет раскрывается в текущей позиции курсора. SurroundsWith-сниппет раскрывается вокруг выделенного блока текста с помощью комбинации Ctrl+K+X.

Сниппет   | Тип   | Описание
----------|-------|----------
#if       | E, SW | Блок условной компиляции #if ... #endif
#region   | E, SW | Блок #region ... #endregion
~         | E     | Деструктор (финализатор)
attribute | E     | Шаблон класса атрибута
checked   | E,SW  | Блок checked { ... }
class     | E,SW  | Шаблон пустого класса
ctor      | E     | Конструктор без аргументов
cw        | E     | Console.WriteLine()
do        | E,SW  | Цикл do { ... } while
else      | E,SW  | Блок else { ... }
enum      | E,SW  | Шаблон enum-типа 
equals    | E     | Заготовка для методов Equals(object) и GetHashCode
exception | E     | Шаблон класса исключения
for       | E,SW  | Цикл for {int i=0; i<len; i++} { ... }
foreach   | E,SW  | Цикл foreach { }
forr      | E,SW  | Цикл for с обратным порядком for (int i=len-1; i>0=0; i--) { ... }
if        | E,SW  | Блок if (cond) { ... }
indexer   | E     | Свойство-индексатор
interface | E,SW  | Шаблон пустого интерфейса
invoke    | E     | Безопасный вызов события
iterator  | E     | Заготовка метода IEnumerator<T> GetEnumerator() { ... }
iterindex | E     | Именованный итератор/индексатор с вложенным классом 
lock      | E,SW  | Блок lock (smth) { ... }
mbox      | E     | MessageBox.Show()
namespace | E,SW  | Блок namespace Name { ... }
prop      | E     | Автоматически реализуемое свойство
propfull  | E     | Свойство с полем
propg     | E     | Автоматически реализуемое свойство с private set
propdp    | E     | Свойство использующее DependencyProperty для поля
propa     | E     | Attached-свойство использующее DependencyProperty для поля
sim       | E     | int Main() { ... }
struct    | E,SW  | Шаблон struct-типа
svm       | E     | void Main() { ... }
switch    | E     | Блок switch (expr) { ... }
try       | E,SW  | Блок try { ... } catch { } 
tryf      | E,SW  | Блок try { ... } finally { }
unchecked | E,SW  | Блок unchecked { ... }
unsafe    | E,SW  | Блок unsafe { ... }
using     | E,SW  | Блок using (obj) { ... }
while     | E,SW  | Цикл while (cond) { ... }

NN. Вы можете создавать свои сниппеты. Для этого вам нужно быть знакомым с языком XML. Подробности читайте в статье [Walkthrough: Creating a Code Snippet](https://msdn.microsoft.com/en-us/library/ms165394.aspx).

NN. Для некоторых типов файлов поддерживается несколько редакторов. Перелючение между ними делается через команду контекстного меню "Open with ...". Один из редакторов можно назначить редактором по умолчанию с помощью кнопки "Set As Default".


### Перемещение по вкладкам (tabs) редактора

NN. Ctrl+Tab - вперед, Ctrl+Shift+Tab назад (Ctrl+F6 и Ctrl+Shift+F6)

NN. Закрыть текущую вкладку - Ctrl+F4


### Отладчик

NN. Текушую точку исполнения, которая представлена желтой стрелкой можно двигать с помощью мыши меняя таким образом путь исполнения программы. Это полезно, например, для пропуска части кода которая содержит ошибку или для повторного исполнения кода.

NN. Используйте "function breakpoints" для отслеживания подписки на события используя имя функции Namespace.ClassName.add_EventName. Для отслеживания отписки - имя Namespace.ClassName.remove_EventName.

NN. В файле AutoExp.cs из папки Common7\Packages\Debugger\Visualizers\Original находятся настройки визуализаторов отладки. Туда можно добавить свои правила, после чего перекомпилировать (csc /t:library AutoExp.cs) и поместить в оригинальную папку или в папку My Documents\Visual Studio ????\Visualizers.

NN. IntelliTrace поддерживается в старших редакциях Visual Studio - Enterprise и Ultimate.
	

### Package Manager Console

NN. Через консоль можно быстро добавить ссылку на сборку в несколько проектов
```powershell
Get-Project -all | % { $_.Object.References.Add("C:\ProjectPath\Libs\SomeAssembly.dll").Version }
Get-Project -all | % { $_.Object.References.Add("System.Configuration, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a").Version }
```


### Запуск внешних утилит

NN. Чтобы настроить список утилит выберите команду Tools \ External Tools...


### Расширения

NN. На сайтах [visualstudiogallery.msdn.microsoft.com](https://visualstudiogallery.msdn.microsoft.com/) и [marketplace.visualstudio.com](https://marketplace.visualstudio.com/) можно найти и скачать расширения для Visual Studio.

NN. Расширения можно также установить через команду меню Tools \ Extensions and Updates


### Полезные бесплатные расширения

NN. [CodeMaid](http://www.codemaid.net/). An open source Visual Studio extension to cleanup and simplify C#, C++, F#, VB, PHP, PowerShell, R, JSON, XAML, XML, ASP, HTML, CSS, LESS, SCSS, JavaScript and TypeScript coding.

NN. C# outline (VS 2010 ... VS 2015) - свертывание развертывание любых { } блоков. См. также Visual Basic and C# Outliner

NN. EditorConfig - хранение настроек редактора на уровне проекта

NN. File Icons - иконки для файлов в Solutuion Explorer

NN. File Nesting - возможность вкладывать (группировать) произвольные файлы друг в друга

NN. Productivity Power Tools

NN. SlowCheetah - поддержка XML трансформаций для любых xml файлов, а не только для web.config из ASP.NET

NN. Visual Basic and C# Outliner (VS 2015) - свертывание развертывание блоков кода в C# и Visual Basic.NET.

NN. [Visual Studio String Debug Visualizer](https://vsstringdebugvisualizer.codeplex.com/)

NN. VSColorOutput - раскраска строк в окне Output


### Полезные бесплатные расширения (ASP.NET)

NN. Web Essentials


### Полезные платные расширения

NN. [JetBrains ReSharper](http://www.jetbrains.com/resharper/)

NN. [CodeRush](https://www.devexpress.com/products/coderush/)

NN. [OzCode](http://www.oz-code.com/) Debugger extensions (79$)

NN. [Visual Assist](http://www.wholetomato.com/) (99$ Personal, 279$ Standard)
