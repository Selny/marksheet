---
sxem: post
başlıq: "HTML <strong>Sintaksisi</strong>"
altbaşlıq: "Digər dillər kimi HTML-ində mühim <strong>qaydaları</strong>" var
bölmə: html
---

**HTML**-in açılışı, **H**yper**T**ext **M**arkup **L**anguage (Azərbaycanca, Hiper Mətn İşarələmə Dili):


* **HyperText** _(Hiper Mətn)_ İnternetin HTTP hissəsini işlətdiyini bildirir
* **Markup** _(İşarələmə)_ yazdığınız kodun açar sözlər vaistəsi ilə izah olunduğunu bildirir
* **Language** _(Dil)_ bu kodların həm insanlar həm də kompüterlər tərəfindən oxunula bildiyini gösdərir

Digər dillər kimi, HTML-də bir qism **qaydalar** ilə gəlir. Bu qaydalar yetərincə sadədir. İlkin olaraq bizim gərək **çərçivələrimiz** olsun, bir şeyin haradan _başlayıb_ harada _bitdiyini_ görə bilək.

HTML-dən nümunə paraqraf:

{% highlight html %}
<p>O mənə öyrətdiki, bəzi insanlar səhvləri yadda saxlayır, yaxşılığları görmür.</p>
{% endhighlight %}

Gördüyünüz bu `<`{:.language-html} və `>`{:.language-html} **üçbucağ mötərizələr** arasında yazılanlar HTML **taqlarıdır**. Bu taqlar nəyin haradan _başlayıb_ harada _bitdiyini_ gösdərir.

Bunların hər biri məxsusi bir **məna** daşıyır. Bu misalda, `p`{:.language-html} **paraqrafı** bildirirdi.

Bunlar adətən qrup halında olurlar:

* _açılış_ tagı olan `<p>`{:.language-html} paraqrafın **başlanğıcını** bildirir
* _bağlanış_ tagı olan `</p>`{:.language-html} isə harada **bitdiyini** bildirir

Açılış və bağlanış taqı arasında ki, tək fərq **əyri xəttdir** `/`{:.language-html} hansı ki, taqın adından öncə gəlir.

Siz açılış taqı, bağlanış taqı və arasındakıları yazdığınızda bir **HTML elementi** əldə etmiş olursunuz. Bütün bu sətr bir HTML elementidir hansı ki, `<p>`{:.language-html} və `</p>`{:.language-html} HTML taqları ilə yazılıb.

Əgər [bu nümunəni brauzerinizdə açsanız](/html/sample-paragraph.html), **HTML taqlarının brauzer tərəfindən göstərilmədiyinə** fikir verə bilərsiniz. Taqlar brauzer tərəfindən yalnız hansı _növ_ **məlumat** yazdığınız təyin etmək üçün oxunulur.

### HTML-i hara yazaq

Ola bilsin ki, sadə mətn faylları ilə qarşılaşmısınız, bu faylların `.txt` uzantısı olur.

Bu mətn faylının **HTML faylı** olması üçün, siz `.html` uzantısı işlədməlisiniz.

**Mətn redaktorunuzu** açın, və aşağıdakıları ora köçürün.

{% highlight html %}
<p>Bu mənim ilk Websəhifəmdir!</p>
{% endhighlight %}

Bu faylı `my-first-webpage.html` olaraq yadda saxlayın və brauzeriniz ilə açın, və bu görsənir:

<div class="result"><p>Bu mənim ilk Websəhifəmdir!</p></div>

Yadda saxlayın:

* Notepad++ kimi mətn redaktorlarını HTML fayllarını **qurmaq** üçün işlədin
* Firefox kimi brauzerləri isə HTML fayllarını **açmaq** üçün işlədin.

### Atributlar

Atributlar HTML elementinə bağlı **əlavə** məlumatlardır. Bunlar HTML _taqı içində_ yazılır. Bunlarda, brauzer tərəfindən görsənmir.

Misal üçün, `href` atributu aid olduğu qismə **link** əlavə edir (hansı ki, **a**nchor taqı ilə işlənir):

{% highlight html %}
<a href="https://www.mozilla.com/firefox">Firefoxu Yüklə</a>
{% endhighlight %}

Bu [16 HTML atributu](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes) _bütün_ HTML elementləri ilə işləyə bilir. Bunların hamısı **isdəyə bağlıdır** əlavə oluna bilər.

Əsas istifadə olunanlar, `class` (CSS üçün istifadə olunur), və `title`-dır (oxu bir kontentin üzərinə gətirdiyinzə çıxan məlumat). 

Bəzi HTML elementlərinin isə **mütləq** əlavə olunmalı atriubtları var. Misal üçün, şəkil əlavə edərkən `src` (source) atributunu istafə edərək şəklin yerini bildirməlisiniz.

<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/0/09/BRI_kitten_%285467145697%29.jpg/232px-BRI_kitten_%285467145697%29.jpg" alt="Description of the image">

`<img>` elementini şəkil əlavə etmək üçün işlənildiyimizi nəzərə alsaq, şəklin mənbəyini **tələb etməyi** məntiqlidir.

### Commentlər (Şərhlər)

Əgər kodunuza brauzerdə göəsdərilən səhifəni dəyişməyəcək bir şey yazmaq isdəsəniz, sizə **commentlərdən** istifadə edə bilərsiniz. Commentlər brauzer tərəfindən _gösdərilmir_ və əsasən kodu yazanlar üçün yararlı olurlar.

Bir comment, `<!--` ilə başlayır və `-->` ilə bitir.

{% highlight html %}
`<!-- Bu yazı brauzer tərəfindən gösdərilmir -->`
<p>Hello World!</p>
{% endhighlight %}

<div class="result"><p>Hello World!</p></div>

### Bir tərəfli elementlər

Bəzi HTML elementlərinin yalnız açılma taqı var:

`<br> <!-- xətt-arası -->`
<br>
<img src="https://via.placeholder.com/50" alt="Description"> `<!-- şəkil -->`

`<input type="text"> <!-- yazı input -->`

Bunların bağlanma taqı olmadığından və _daxillərində_ bir şey saxlaya bilməyəcəklərindən, bir tərəfli elementlərin adətən az atributu olur, bununla əlavə məlumat verilə bilinir.
