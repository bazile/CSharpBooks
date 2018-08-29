# Простой POST запрос

## HttpWebRequest

```csharp
using System.Net;
...
HttpWebRequest request = (HttpWebRequest)WebRequest.Create("http://httpbin.org/post");
// Всегда указывайте User-Agent!
request.UserAgent = ".NET Application";
request.Method = "POST";
request.ContentType = "application/x-www-form-urlencoded";

// Отправляем тело (body) запроса
// Заголовок Content-Length с правильным значением будет добавлен автоматически
string postData = "param1=value1&param2=value2&param3=value3";
using (var writer = new StreamWriter(request.GetRequestStream()))
{
	writer.Write(postData);
}

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
HttpWebRequest request = WebRequest.CreateHttp("http://httpbin.org/post");
// Всегда указывайте User-Agent!
request.UserAgent = ".NET Application";
request.Method = "POST";
request.ContentType = "application/x-www-form-urlencoded";

// Отправляем тело (body) запроса
// Заголовок Content-Length с правильным значением будет добавлен автоматически
string postData = "param1=value1&param2=value2&param3=value3";
using (var writer = new StreamWriter(request.GetRequestStream()))
{
	writer.Write(postData);
}

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

Для отправки POST запросов используются UploadXyz методы класса WebClient.

```csharp
using System.Net;
...
using (WebClient webClient = new WebClient())
{
	// Всегда указывайте User-Agent!
	webClient.Headers.Add(HttpRequestHeader.UserAgent, ".NET Application");
	webClient.Headers.Add(HttpRequestHeader.ContentType, "application/x-www-form-urlencoded");
	
	string postData = "param1=value1&param2=value2&param3=value3";
	string responseText = webClient.UploadString("http://httpbin.org/post", postData);
}
```

## HttpClient

Класс HttpClient не содержит синхронных методов.

## xNet
```csharp
using xNet;
...
HttpRequest request = new HttpRequest();
// Всегда указывайте User-Agent!
request.UserAgent = ".NET Application";

string responseText = request.Post(
	"http://httpbin.org/post",
	"param1=value1&param2=value2&param3=value3",
	"application/x-www-form-urlencoded"
).ToString();
```
