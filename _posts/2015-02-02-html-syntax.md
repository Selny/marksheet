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

<div class="result"><a href="https://www.mozilla.com/firefox">Download Firefox</a></div>

There are [16 HTML attributes](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes) that can be used on _any_ HTML element. All of them are **optional**.

You'll mostly use `class` (which is used for CSS), and `title` (which is the tooltip that appears when hovering an item like this one).

Some HTML elements have **obligatory** attributes. For example, when inserting an image, you have to provide the location of the image, using the `src` (source) attribute:

{% highlight html %}
<img src="#" alt="Description of the image">
{% endhighlight %}

Considering that the purpose of the `<img>` element is to display an image, it makes sense for the path to the image to be **required**.

### Comments

If you write something in your code without disrupting how the browser will display your page, you can write **comments**. They will be _ignored_ by the browser, and are only useful for us humans who write the code.

A comment starts with `<!--` and ends with `-->`.

{% highlight html %}
<!-- This sentence will be ignored by the browser -->
<p>Hello World!</p>
{% endhighlight %}

<div class="result"><p>Hello World!</p></div>

### Self-enclosing elements

Some HTML elements only have an opening tag:

{% highlight html %}
<br> <!-- line-break -->
<img src="https://placehold.it/50x50" alt="Description"> <!-- image -->
<input type="text"> <!-- text input -->
{% endhighlight %}

Because they don't have a closing tag and consequently can't contain anything _inside_ them, self-enclosing elements usually carry a few attributes, to provide them with additional information.
