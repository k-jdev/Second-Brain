Для перехвата HTTP запросов используйте [`webRequest`](https://developer.mozilla.org/ru/docs/Mozilla/Add-ons/WebExtensions/API/webRequest) API. Этот API позволит вам добавлять обработчики, на различных этапах создания HTTP запросов. В обработчиках вы можете:

- получить доступ к заголовкам и телам запроса, к заголовкам ответа
- отменять и перенаправлять запросы
- изменять запрос и заголовки ответа

В этой статье мы рассмотрим три разных способа использования `webRequest` модуля:

- Логирование URL сделанных запросов.
- Перенаправление запросов.
- Модификация заголовков запроса.

## [Логирование URL запросов](https://developer.mozilla.org/ru/docs/Mozilla/Add-ons/WebExtensions/Intercept_HTTP_requests#%D0%BB%D0%BE%D0%B3%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5_url_%D0%B7%D0%B0%D0%BF%D1%80%D0%BE%D1%81%D0%BE%D0%B2)

Создайте новый каталог "requests". В нём создайте файл "manifest.json" со следующим содержимым:


``` json
{
  "description": "Demonstrating webRequests",
  "manifest_version": 2,
  "name": "webRequest-demo",
  "version": "1.0",

  "permissions": ["webRequest", "<all_urls>"],

  "background": {
    "scripts": ["background.js"]
  }
}
```

Далее, создайте файл "background.js" со следующим содержимым:


``` js
function logURL(requestDetails) {
  console.log("Загрузка: " + requestDetails.url);
}

browser.webRequest.onBeforeRequest.addListener(logURL, {
  urls: ["<all_urls>"],
});
```

![[Pasted image 20241114234912.png]]
![[Pasted image 20241114234931.png]]
![[Pasted image 20241114235121.png]]

- **🏷️Tags** : #js