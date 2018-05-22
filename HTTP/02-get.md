# Простой GET запрос с использованием async/await

## HttpWebRequest
```csharp
using System.Net;
...
HttpWebRequest request = (HttpWebRequest)WebRequest.Create("http://example.com");
// Всегда указывайте User-Agent!
request.UserAgent = ".NET Application";

using (WebResponse response = await request.GetResponseAsync())
{
	using (Stream responseStream = response.GetResponseStream())
	{
		using (StreamReader reader = new StreamReader(responseStream))
		{
			string responseText = await reader.ReadToEndAsync();
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

using (WebResponse response = await request.GetResponseAsync())
{
	using (Stream responseStream = response.GetResponseStream())
	{
		using (StreamReader reader = new StreamReader(responseStream))
		{
			string responseText = await reader.ReadToEndAsync();
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
	string responseText = await webClient.DownloadStringTaskAsync("http://example.com");
}
```

## HttpClient

```csharp
using System.Net.Http;
...
using (HttpClient httpClient = new HttpClient())
{
	// Всегда указывайте User-Agent!
	httpClient.DefaultRequestHeaders.Add("User-Agent", ".NET Application");
	string responseText = await httpClient.GetStringAsync("http://example.com");
}
```

## xNet

Библиотека xNet не содержит async методов.
