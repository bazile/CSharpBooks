# Простой POST запрос c использованием async/await

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
using (var writer = new StreamWriter(await request.GetRequestStreamAsync()))
{
	await writer.WriteAsync(postData);
}

using (WebResponse response = await request.GetResponseAsync())
{
	using (Stream responseStream = response.GetResponseStream())
	{
		using (StreamReader reader = new StreamReader(responseStream))
		{
			string responseText = await reader.ReadToEndAsync();
			responseText.Dump();
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
using (var writer = new StreamWriter(await request.GetRequestStreamAsync()))
{
	await writer.WriteAsync(postData);
}

using (WebResponse response = await request.GetResponseAsync())
{
	using (Stream responseStream = response.GetResponseStream())
	{
		using (StreamReader reader = new StreamReader(responseStream))
		{
			string responseText = await reader.ReadToEndAsync();
			responseText.Dump();
		}
	}
}
```

## WebClient

Для отправки POST запросов используются UploadXyzTaskAsync методы класса WebClient.

```csharp
using System.Net;
...
using (WebClient webClient = new WebClient())
{
	// Всегда указывайте User-Agent!
	webClient.Headers.Add(HttpRequestHeader.UserAgent, ".NET Application");
	webClient.Headers.Add(HttpRequestHeader.ContentType, "application/x-www-form-urlencoded");
	
	string postData = "param1=value1&param2=value2&param3=value3";
	string responseText = await webClient.UploadStringTaskAsync("http://httpbin.org/post", postData);
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
	FormUrlEncodedContent postContent = new FormUrlEncodedContent(new Dictionary<string,string>() {
		{ "param1", "value1" },
		{ "param2", "value2" },
		{ "param3", "value3" },
	});
	HttpResponseMessage responseMessage = await httpClient.PostAsync("http://httpbin.org/post", postContent);
	// Убеждаемся что запрос был успешным
	// В случае ошибки метод EnsureSuccessStatusCode сгенерирует исключение
	responseMessage.EnsureSuccessStatusCode();
	string responseText = await responseMessage.Content.ReadAsStringAsync();
}
```

## xNet

Библиотека xNet не содержит async методов.
