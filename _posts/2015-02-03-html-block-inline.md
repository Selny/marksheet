---
sxem: post
başlıq: "HTML <strong>Block</strong> and <strong>Inline</strong>"
altbaşlıq: "HTML has 2 main <strong>types</strong> of elements"
bölmə: html
---

HTML-də əsasən 2 növ elementlə rastlaşırsınız:

* **block** elementlər, misal:

    * paraqraflar `<p>`
    * listlər: sırasız (qara nöqtələr ilə) `<ul>` vəya sıralı listlər (ədədlər ilə) `<ol>`
    * başlıqlar: 1-ci səviyyədən `<h1>` 6-cı səviyyəyə kimi `<h6>`
    * artikıllar `<article>`
    * bölmələr `<section>`
    * uzun statlar `<blockquote>`

* **inline** elementlər, misal:

    * linklər `<a>`
    * vurğulanan sözlər `<em>`
    * mühim sözlər `<strong>`
    * qısa statlar `<q>`
    * qısaltmalar `<abbr>`

**Block** elementlər səhifənizin əsas hissələrini **təşkil** etmək üçündür, bununla kontentinizi _müntəzəm_ bloklara bölürsünüz.

**Inline** elementlər yazıların _hissələrini_ fərqləndirmək üçündür, bununla yazılara məxsusi məna yükləyə bilirsiniz. Inline elementlər əsasən tək vəya bir neçə sözdən ibarət olur.

{% highlight html %}
<p>Youtube-daki bu <a href="https://www.youtube.com">marağlı videonu</a> görmüsən?</p>
{% endhighlight %}

### Açılış və bağlanış taqları

**Bütün** block səviyyəsində elementlərin açılış və bağlanış taqları var.

Nətciə olaraq, bütün bir tərəfli elementlər **inlilne** elementlər olur, çünki bunların sintaksı daxillərində başqa bir HTML elementi saxlamağa imkan vermir.

<div class="table">
  <table>
    <tr>
      <th class="empty"></th>
      <th>Açılış və bağlanış taqı var</th>
      <th>Bir-tərəflidir</th>
    </tr>
    <tr>
      <th>Block elementlər</th>
      <td>
        <code>&lt;p&gt;</code>
        <code>&lt;/p&gt;</code>
        <br>
        <code>&lt;ul&gt;</code>
        <code>&lt;/ul&gt;</code>
        <br>
        <code>&lt;ol&gt;</code>
        <code>&lt;/ol&gt;</code>
      </td>
      <td>
        <strong>Mümkünsüzdür</strong>
      </td>
    </tr>
    <tr>
      <th>Inline elementlər</th>
      <td>
        <code>&lt;a&gt;</code>
        <code>&lt;/a&gt;</code>
        <br>
        <code>&lt;strong&gt;</code>
        <code>&lt;/strong&gt;</code>
        <br>
        <code>&lt;em&gt;</code>
        <code>&lt;/em&gt;</code>
      </td>
      <td>
        <code>&lt;input&gt;</code>
        <br>
        <code>&lt;br&gt;</code>
        <br>
        <code>&lt;img&gt;</code>
      </td>
    </tr>
  </table>
</div>

### Başqa növ HTML elementləri

Block/inline elementlərə bəzi instisnalar var, bunlardan ən çox rastlaşa biləcəkləriniz bunlardır:

* **list items** `<li>` ilə işlənir
* **table**, **table rows**, **table cells** isə sırası ilə `<table>`, `<tr>` və `<td>` ilə işlənir
