<style>
  .framebox-container-container {
    max-width: 466px;
    margin: 1.8rem auto 0;
  }
  .framebox-container {
    position: relative;
    padding-top: 75.3%;
  }
  .framebox-container iframe {
    position: absolute;
    top: 0;
    left: 0;
    height: 100%;
  }
  .browser-screenshot {
    filter: drop-shadow(0 6px 4px rgba(0,0,0,0.2));
  }
</style>

<div class="framebox-container-container">
<div class="framebox-container">
{% framebox height="100%" %}
<link href="" rel="stylesheet">
<script src="" defer>
</script><script src="" defer>
</script><script src="" defer>
</#cdata-section></style><style><#cdata-section>
</svg><svg data-md-type="raw_html" class="lifecycle-diagram" style="display:none">
</svg><svg data-md-type="raw_html" class="lifecycle-diagram register" viewbox="0 0 96.9 73">
</script><div data-md-type="block_html"><script>
</div>
<p data-md-type="paragraph">{% endframebox %}</p>
</div><div data-md-type="block_html">
</div></script></div>
</div>
</div>
<p data-md-type="paragraph">次の HTML をご覧ください。。</p>
<pre data-md-type="block_code" data-md-language=""><code><!DOCTYPE html>
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
</code></pre>
<p data-md-type="paragraph">これは Service Worker を登録し、3 秒後に犬の画像を追加します。</p>
<p data-md-type="paragraph">その Service Worker <code data-md-type="codespan">sw.js</code> は次のとおりです。</p>
<pre data-md-type="block_code" data-md-language=""><code>self.addEventListener('install', event => {
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
</code></pre>
<p data-md-type="paragraph">猫の画像をキャッシュし、<code data-md-type="codespan">/dog.svg</code> のリクエストがあるたびに表示します。
ただし、<a href="https://cdn.rawgit.com/jakearchibald/80368b84ac1ae8e229fc90b3fe826301/raw/ad55049bee9b11d47f1f7d19a73bf3306d156f43/" data-md-type="link">上記の例を実行</a>{:
.external}した場合、ページを最初に読み込んだときは犬が表示されます。
更新を押すと、猫が表示されます。</p>
<p data-md-type="paragraph">注: 猫の方が犬よりよいです。猫の方がよいと言ったらよいのです。</p>
<h3 data-md-type="header" data-md-header-level="3">スコープと制御</h3>
<p data-md-type="paragraph">Service Worker 登録のデフォルトのスコープは、スクリプト URL に対して相対的な <code data-md-type="codespan">./</code> です。
つまり、<code data-md-type="codespan">//example.com/foo/bar.js</code> に Service Worker を登録すると、デフォルトのスコープは <code data-md-type="codespan">//example.com/foo/</code> になります。</p>
<p data-md-type="paragraph">ページ、ワーカー、共有ワーカーは、<code data-md-type="codespan">clients</code> と呼ばれます。Service Worker で制御できるのは、スコープ内のクライアントのみです。
クライアントが制御されるようになると、その fetch はスコープ内の Service Worker を通過するようになります。
クライアントを制御している <code data-md-type="codespan">navigator.serviceWorker.controller</code> が null と Service Worker インスタンスのどちらであるかを判別できます。</p>
<h3 data-md-type="header" data-md-header-level="3">ダウンロード、解析、実行</h3>
<p data-md-type="paragraph">最初の Service Worker は、<code data-md-type="codespan">.register()</code> を呼び出すとダウンロードされます。スクリプトがダウンロードや解析に失敗したか、初期実行時にエラーをスローした場合、登録 Promise は棄却され、Service Worker は破棄されます。</p>
<p data-md-type="paragraph">Chrome の DevTools によって、エラーがコンソールと [Application] タブの Service Worker セクションに表示されます。</p>
<div data-md-type="block_html">
<figure>
  <img src="images/register-fail.png" class="browser-screenshot" alt="Service Worker の DevTools タブに表示されたエラー">
</figure>
</div>
