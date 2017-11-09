{% framebox height="100%" %}
<style>
.lifecycle-diagram {
  width: 100%;
  height: auto;
  display: block;
}
</style>
{% endframebox %}

次の HTML をご覧ください。

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

これは Service Worker を登録し、3 秒後に犬の画像を追加します。
