## Преобразование типов

Преобразование дает возможность трактовать выражение как имеющее определенный тип. Преобразования делятся на неявные и явные. 

### Неявное преобразование

Неявные преобразования выполняются компилятором без явного указания со стороны программиста. Они разрешены для случаев когда такое преобразование не приводит к потере данных.

- Из sbyte в short, int, long, float, double, или decimal;
- Из byte в short, ushort, int, uint, long, ulong, float, double, или decimal;
- Из short в int, long, float, double, или decimal;
- Из ushort в int, uint, long, ulong, float, double, или decimal;
- Из int в long, float, double, или decimal;
- Из uint в long, ulong, float, double, или decimal;
- Из long в float, double, или decimal;
- Из ulong в float, double, или decimal;
- Из char в ushort, int, uint, long, ulong, float, double, или decimal;
- Из float в double.

Примеры неявных преобразований:
```csharp
int n1 = 100;
long n2 = n1; // Неявное преобразование из int в long

float pi1 = 3.14159f;
double pi2 = pi1; // Неявное преобразование из float в double
```

### Явное преобразование

Явное преобразование выполняется путем записи вида *(ИмяТипа)выражение*. Таким образом мы просим привести выражение к указанному типу.

### Методы Parse/TryParse
Enum.Parse

### Методы ParseExact/TryParseExact

### Класс Convert
NB: Convert.ToInt32(double,float,decimal) округляет значения в отличие от преобразования (int)

### Класс BitConverter

С помощью класса BitConverter можно преобразовать значение встроенного типа в массив байтов или из массива байтов в значение встроенного типа.

```csharp
double a = 3.1415926;
// Преобразование double в массив byte
// Переменная bytes будет содержать {74, 216, 18, 77, 251, 33, 9, 64}
byte[] bytes = BitConverter.GetBytes(pi);
// Преобразование массива byte обратно в double
double b = BitConverter.ToDouble(bytes, 0);
```

### Ключевые слова is и as
