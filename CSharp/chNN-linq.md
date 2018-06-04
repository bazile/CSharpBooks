## LINQ

### Коллекции которые не реализуют IEnumerable<T>

Для работы многих конструкций LINQ требуется чтобы коллекция реализовывала интерфейс IEnumerable<T>.

```csharp
MatchCollection matches = Regex.Matches("123 abc 456", @"\d+");
// Ошибка компиляции: Could not find an implementation of the query pattern for source type 'System.Text.RegularExpressions.MatchCollection'. 'Select' not found.
IEnumerable<string> values = from m in matches select m.Value;
```

Ошибка компиляции возникает т.к. тип MatchCollection не реализует интерфейс IEnumerable<T>. По этой же причине следующий цикл foreach будет считать элементы коллекции имеют тип object.
```csharp
MatchCollection matches = Regex.Matches("123 abc 456", @"\d+");
foreach (var m in matches)
{
	Console.WriteLine(m.Value); // 'object' does not contain a definition for 'Value' and ...
}
```

Неудачей также закончится следующая попытка

```csharp
MatchCollection matches = Regex.Matches("123 abc 456", @"\d+");
// Ошибка компиляции: 'MatchCollection' does not contain a definition for 'Select' and no extension method 'Select' accepting a first argument of type 'MatchCollection' could be found
IEnumerable<string> values = matches.Select(m => m.Value);
```

Исправить последний случай можно с помощью метода Cast который расширяет IEnumerable
```csharp
IEnumerable<string> values = matches.Cast<Match>().Select(m => m.Value);
```

Первые два случая исправляются путем явного указания типа для переменной m
```csharp
IEnumerable<string> values = from Match m in matches select m.Value;
...
foreach (Match m in matches)
...
```

### Вопросы для самопроверки

1. Откомплируется ли данный код и, если да, то что он выведет на экран?
```csharp
int[] arr = {1,2,3,4,5,6,7,8,9};
List<object> list = new List<object>();
list.Add(from i in arr where i%2==1 select i);
foreach (var element in list)
{
	Console.WriteLine(element);
}
```
Изменится ли поведение программы если List<object> заменить на List<int>?
