# Нормализация ссылок

При парсинге HTML можно столкнуться с относительными ссылками на изображения, стили, javascript и другие ресурсы. Для обращения к ним их необхолимо нормализовать - превратить в абсолютные ссылки.

```csharp
// Абсолютная базовая ссылка
Uri baseUri = new Uri("http://example.com/about/");

Console.WriteLine(new Uri(baseUri, "about.html"));    // http://example.com/about/about.html
Console.WriteLine(new Uri(baseUri, "press"));         // http://example.com/about/press
Console.WriteLine(new Uri(baseUri, "../index.html")); // http://example.com/index.html
```
