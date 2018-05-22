# Простой GET запрос

## HttpWebRequest
```csharp
using System.Net;
...
HttpWebRequest request = (HttpWebRequest)WebRequest.Create("http://example.com");
// Всегда указывайте User-Agent!
request.UserAgent = ".NET Application";

using (WebResponse response = request.GetResponse())
{
	using (Stream responseStream = response.GetResponseStream())
	{
		using (StreamReader reader = new StreamReader(responseStream))
		{
			string responseText = reader.ReadToEnd();
		}
	}
}
```

## HttpWebRequest (.NET Framework 4.5+)
```csharp
using System.Net;
...
HttpWebRequest request = WebRequest.CreateHttp("http://example.com");
// Всегда указывайте User-Agent!
request.UserAgent = ".NET Application";

using (WebResponse response = request.GetResponse())
{
	using (Stream responseStream = response.GetResponseStream())
	{
		using (StreamReader reader = new StreamReader(responseStream))
		{
			string responseText = reader.ReadToEnd();
		}
	}
}
```

## WebClient
```csharp
using System.Net;
...
using (WebClient webClient = new WebClient())
{
	// Всегда указывайте User-Agent!
	webClient.Headers.Add(HttpRequestHeader.UserAgent, ".NET Application");
	string responseText = webClient.DownloadString("http://example.com");
}
```

## HttpClient

Класс HttpClient не содержит синхронных методов, но это можно обойти. Рекомендуется все-таки использовать именно async/await вариант.

```csharp
using System.Net.Http;
...
using (HttpClient httpClient = new HttpClient())
{
	// Всегда указывайте User-Agent!
	httpClient.DefaultRequestHeaders.Add("User-Agent", ".NET Application");
	string responseText = httpClient.GetStringAsync("http://example.com").GetAwaiter().GetResult();
}
```

## xNet
```csharp
using xNet;
...
HttpRequest request = new HttpRequest();
// Всегда указывайте User-Agent!
request.UserAgent = ".NET Application";
string responseText = request.Get("http://example.com").ToString();
```
