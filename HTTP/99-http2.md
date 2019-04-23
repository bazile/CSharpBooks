# HTTP 2

ИНФОРМАЦИЯ НЕ ПРОВЕРЕНА ДО КОНЦА

.NET Framework пока не поддерживает HTTP2

В .NET Core поддержка HTTP2 есть начиная с версии 1.1 (?). Необходимо установить пакет System.Net.Http версии 4.3.0 или старше.

```csharp
HttpClient httpClient = new HttpClient();
HttpRequestMessage requestMessage = new HttpRequestMessage(HttpMethod.Get, "https://google.by");
requestMessage.Headers.Add("User-Agent", "LINQPad");
requestMessage.Version = new Version(2,0);
HttpResponseMessage responseMessage = await httpClient.SendAsync(requestMessage);
responseMessage.EnsureSuccessStatusCode();
//Console.WriteLine(responseMessage.Version);
string html = await responseMessage.Content.ReadAsStringAsync();

requestMessage.Dispose();
responseMessage.Dispose();
httpClient.Dispose();
```
