<div class="framebox-container-container">
<div class="framebox-container">
{% framebox height="100%" %}
<link href="" rel="stylesheet">
<script src="" defer>
</script><script src="" defer>
</script><script src="" defer>
</style><style>
</svg><svg>
</svg><svg>
</div></script>
</div>
<div data-md-type="block_html">
<script></script>
</div>
<p data-md-type="paragraph">{% endframebox %}</p>
<div data-md-type="block_html"></div>
</div>

次の HTML をご覧ください。。

```
<!DOCTYPE html>
An image will appear here in 3 seconds:
<script>
  navigator.serviceWorker.register('/sw.js')
    .then(reg => console.log('SW registered!', reg))
    .catch(err => console.log('Boo!', err));

  setTimeout(() => {
    const img = new Image();
    img.src = '/dog.svg';
    document.body.appendChild(img);
  }, 3000);
</script>
```

これは Service Worker を登録し、3 秒後に犬の画像を追加します。

その Service Worker `sw.js` は次のとおりです。

```
self.addEventListener('install', event => {
  console.log('V1 installing…');

  // cache a cat SVG
  event.waitUntil(
    caches.open('static-v1').then(cache => cache.add('/cat.svg'))
  );
});

self.addEventListener('activate', event => {
  console.log('V1 now ready to handle fetches!');
});

self.addEventListener('fetch', event => {
  const url = new URL(event.request.url);

  // serve the cat SVG from the cache if the request is
  // same-origin and the path is '/dog.svg'
  if (url.origin == location.origin && url.pathname == '/dog.svg') {
    event.respondWith(caches.match('/cat.svg'));
  }
});
```

猫の画像をキャッシュし、`/dog.svg` のリクエストがあるたびに表示します。
ただし、[上記の例を実行](https://cdn.rawgit.com/jakearchibald/80368b84ac1ae8e229fc90b3fe826301/raw/ad55049bee9b11d47f1f7d19a73bf3306d156f43/){:
.external}した場合、ページを最初に読み込んだときは犬が表示されます。
更新を押すと、猫が表示されます。

注: 猫の方が犬よりよいです。猫の方がよいと言ったらよいのです。

### スコープと制御

Service Worker 登録のデフォルトのスコープは、スクリプト URL に対して相対的な `./` です。
つまり、`//example.com/foo/bar.js` に Service Worker を登録すると、デフォルトのスコープは `//example.com/foo/` になります。

ページ、ワーカー、共有ワーカーは、`clients` と呼ばれます。Service Worker で制御できるのは、スコープ内のクライアントのみです。
クライアントが制御されるようになると、その fetch はスコープ内の Service Worker を通過するようになります。
クライアントを制御している `navigator.serviceWorker.controller` が null と Service Worker インスタンスのどちらであるかを判別できます。

### ダウンロード、解析、実行

最初の Service Worker は、`.register()` を呼び出すとダウンロードされます。スクリプトがダウンロードや解析に失敗したか、初期実行時にエラーをスローした場合、登録 Promise は棄却され、Service Worker は破棄されます。

Chrome の DevTools によって、エラーがコンソールと [Application] タブの Service Worker セクションに表示されます。

<figure>
  <img src="images/register-fail.png" class="browser-screenshot" alt="Service Worker の DevTools タブに表示されたエラー">
</figure>
