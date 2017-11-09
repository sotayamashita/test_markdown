<div class="framebox-container-container">
<div class="framebox-container">
{% framebox height="100%" %}
#cdata-section><style><#cdata-section>
{% endframebox %}
</div><div data-md-type="block_html">
</div></style>
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
