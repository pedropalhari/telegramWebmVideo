# telegramWebmVideo
Shows telegram .webm links as videos


## How to use
* Paste on the console or create a tampermonkey script
```javascript
setInterval(() => {
  var textNodes = document.getElementsByClassName("im_message_text");
  var webmTextNodes = [];

  for (var textNode of textNodes)
    if (
      textNode.firstChild != null &&
      textNode.firstChild.href != undefined &&
      textNode.firstChild.href.indexOf(".webm") != -1
    )
      webmTextNodes.push(textNode.firstChild);

  for (var videoLink of webmTextNodes) {
    if (!videoLink.hasAlreadyBeenUpdated)
      videoLink.insertAdjacentHTML(
        "afterend",
        `<video controls style="width: 100%;height: auto;" src="${
          videoLink.href
        }"></video>`
      );

    videoLink.hasAlreadyBeenUpdated = true;
  }
}, 3000);

```

> whoosh, basic js
