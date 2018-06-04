## Типы

### Классификация типов

Типы в .NET делятся на значимые (value type) и ссылочные (reference type).

### Встроенные типы

Тип C#  | Тип .NET       | Диапазон значений
------- | -------------- | ------------------------------------------------------
byte    | System.Byte    | 0..255
sbyte   | System.Sbyte   | –128..127
short   | System.Int16   | –32 768..32 767
int     | System.Int32   | –2 147 483 648..2 147 483 647
long    | System.Int64   | -9 223 372 036 854 775 808..9 223 372 036 854 775 807
ushort  | System.UInt16  | 0..65535
uint    | System.UInt32  | 0..4 294 967 295
ulong   | System.UInt64  | 0..18 446 744 073 709 551 615
float   | System.Single  | Точность: от 1.5 × 10−45 до 3.4 × 1038, 7 цифр
double  | System.Double  | Точность: от 5.0 × 10−324 до 1.7 × 10308, 14-15 цифр
decimal | System.Decimal | Точность: от 1.0 × 10−28 до 7.9 × 1028, 28 цифр
string  | System.String  | Последовательность символов типа char
char    | System.Char    | Символ в кодировке Unicode
bool    | System.Boolean | true, false
object  | System.Object  | 

У числовых встроенных типов есть константные поля MinValue и MaxValue с помощью которых можно получить соответственно минимальное и максимальное значение для этого типа.
```csharp
Console.WriteLine(short.MinValue); // -32768
Console.WriteLine(short.MaxValue); // 32767
```
