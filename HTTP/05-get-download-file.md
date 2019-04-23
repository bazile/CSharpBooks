# Скачивание файлов

## HttpWebRequest

```csharp
using System.Net;
...
void Main()
{
	string address = "https://sec.ch9.ms/ch9/a099/dda6d52b-1eed-4c46-9496-a37f4a36a099/TwC142.mp345";
	string savePath = @"c:\my\TwC142.mp3";
	
	try
	{
		DownloadFile(address, savePath);
	}
	catch (WebException ex)
	{
		int statusCode = ((HttpWebResponse)ex.Response).StatusCode;
		if (statusCode == 404)
		{
			// Файл не найден
			// ...
		}
		else if (statusCode == 500)
		{
			// Внутренняя ошибка сервера
			// ...
		}
		else throw;
	}
}

void DownloadFile(string address, string filePath)
{
	HttpWebRequest request = (HttpWebRequest)WebRequest.Create(address);
	// Всегда указывайте User-Agent!
	request.UserAgent = ".NET Application";
	// На случай сжатого ответа указываем что ответ необходимо автоматически разжать
	request.AutomaticDecompression = DecompressionMethods.Deflate | DecompressionMethods.GZip;
	
	using (WebResponse response = request.GetResponse())
	{
		using (Stream responseStream = response.GetResponseStream())
		{
			using (FileStream fstream = File.Create(filePath))
			{
				responseStream.CopyTo(fstream);
			}
		}
	}
}
```

## WebClient

```csharp
using System.Net;
...

```

## HttpClient



## xNet

```csharp
using xNet;
...

```
