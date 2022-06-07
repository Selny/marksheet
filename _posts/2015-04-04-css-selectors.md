---
layout: post
title: "CSS <strong>Selectors</strong>"
subtitle: "How to <strong>target</strong> HTML elements"
section: css
---

Çünki biz bütün HTML elememtlərimizi bir dəfədə stayl etmək istəmirik, biz bu HTML elementlərinin alt çoxluğunu **hədəfləyə** bilməliyik.

CSS selektorları səsbiq etmək istədiyimiz üslubumuzun hansı elementlərə tətbiq olunmasını istədiyimizi müəyyənləşdirir

### Ümumi teq selektorları

Ümumi HTML elementlərini hədəf almaq rahatdır: sadəcə teq adını istifadə edin.

{% highlight css %}
a{ /* Links */ }
p{ /* Paragraphs */ }
ul{ /* Unordered lists */ }
li{ /* List items */ }
{% endhighlight %}

HTML teq adları ilə CSS selektorları arasında birbaşa əlaqə var.

### Classes/(Siniflər)

Nəzərə alsaq ki, bütün paraqrafları və ya bütün başlıqları eyni şəkildə tərtib etmək istəmirik, bizim onları _fərqləndirməyə_ ehtiyacımız var.

Bütün HTML atributlarından, `class` attributu CSS üçün çox önəmlidir. Bu, bizə xüsusi olaraq hədəf ala biləcəyimiz HTML elementlərinin **qrupunu** müəyyən etməyə imkan verir. İstifadə etmək istədiyimiz sinif adının qarışısına sadəcə nöqtə qoyuruq `.`:

{% highlight css %}
.date {
  color: red;
}
{% endhighlight %}

Bir tərəfdə, bir tərəfdə `date` dəyəri ilə HTM `class` atributu var. O metləq CSS sinif adı ilə uyğunlaşmalıdır.

CSS sinif adlarını istifadə edə bilərsiniz, hər hansı bir rəqəmlə başlamadığı müddətcə.
{: .info}

`.date` sinif selektoru `class="date"` attributu olan HTML elementlərini hədəf alacaq. Beləliklə, aşağıdakı HTML elementlərini **hamısı** üslublu olacaq:

{% highlight html %}
<p class="date">
  Saturday Feb 21
</p>
<p>
  The event will be on <em class="date">Saturday</em>.
</p>
{% endhighlight %}

<div class="result">
  <p style="color:red;">Saturday Feb 21</p>
  <p>The event will be on <em style="color:red;">Saturday</em>.</p>
</div>

Nəzərə alın ki, teq adı **əlaqəsizdir**. Yalnız `class` HTML attributu əlaqəlidir.

### IDs/(ID-lər)

HTMlL-də `id` attributundan da istifadə edə bilərsiniz, və CSS-də  diyez `#` ilə hədəf ala bilərsiniz:

{% highlight css %}
#tagline{ color: orange;}
{% endhighlight %}

{% highlight html %}
<h1 id="tagline">This heading will be orange.</h1>
{% endhighlight %}

ID-lər siniflərə oxşardırlar, çünki onlar HTML atributuna əsaslanırlar.

### Nümunə

<div class="table">
  <table>
    <thead>
      <tr>
        <th>HTML</th>
        <th>Possible CSS selectors</th>
        <th>What it means</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td><pre><code>&lt;p&gt;&lt;/p&gt;</code></pre></td>
        <td><code>p</code></td>
        <td><code>Every &lt;p&gt;</code></td>
      </tr>
      <tr>
        <td><pre><code>&lt;div class="global"&gt;&lt;/div&gt;</code></pre></td>
        <td>
          <code>div</code><br>
          <code>.global</code><br>
          <code>div.global</code></td>
          <td>Every <code>&lt;div&gt;</code><br>
          Every elements with <code>class=”global”</code><br>
          Every <code>&lt;div&gt;</code> with <code>class=”global”</code>
        </td>
      </tr>
      <tr>
        <td><pre><code>&lt;ul id="menu"&gt;</code></pre></td>
        <td>
          <code>#menu</code><br>
          <code>ul#menu</code>
        </td>
        <td>
          The only element with <code>id=”menu”</code><br>
          The only <code>&lt;ul&gt;</code> with <code>id=”menu”</code>
        </td>
      </tr>
      <tr>
        <td>
          <pre><code>&lt;ol class="dico"&gt;
  &lt;li&gt;Un cobaye&lt;/li&gt;
  &lt;li&gt;Des cobaux&lt;/li&gt;
&lt;/ol&gt;</code></pre>
        </td>
        <td>
          <code>li</code><br>
          <code>ol li</code><br>
          <code>.dico li</code>
        </td>
        <td>
          Every <code>&lt;li&gt;</code><br>
          Every <code>&lt;li&gt;</code> with an <code>&lt;ol&gt;</code> as ancestor <br>
          Every <code>&lt;li&gt;</code> with a <code>class="dico"</code> element as ancestor
        </td>
      </tr>
    </tbody>
  </table>
</div>

### Selektorların birləşdirilməsi

Tarixlərimizin qırmızı olmasını istədiyimiz yerdə əvvəlki nümunəmizi təkrar istifadə edək:

{% highlight css %}
.date {
  color: red;
}
{% endhighlight %}

{% highlight html %}
<p class="date">
  Saturday Feb 21
</p>
<p>
  The event will be on <em class="date">Saturday</em>.
</p>
{% endhighlight %}

<div class="result">
  <p style="color:red;">Saturday Feb 21</p>
  <p>The event will be on <em style="color:red;">Saturday</em>.</p>
</div>

Bəs `em` elementlərində olan tarixlərimizin mavi olmasını istəsək? Aşağıdakə CSS qaydasını **əlavə edə** bilərik:

{% highlight css %}
em.date {
  color: blue;
}
{% endhighlight %}

The `em.date` combines:

* a tag selector `em`
* a class selector `.date`

Bu ancaq `<em class="date"></em>` HTML elementlərinə tətbiq olunacaq. Bu başqa `.date` və ya `em` elementlərinə təsir etməyəcək.

### İyerarxiya selectorları

Selektordakı **boşluq** əcdad/nəsil əlaqəsini müəyyən edir. Tutaq ki, başlığımızda olan keçidlərin qırmızı rəngdə olmasını istəyirik:

{% highlight css %}
header a {
  color: red;
}
{% endhighlight %}

Bunu sağdan sola belə oxumaq olar: _"Başlıq" elementində olan bütün `a` elementlərini seçin"_. Bu, bütün digər bağlantıların (başlıqda olmayan) təsirlənməsinin qarşısını alacaq.

### Pseudo-class selectorlar

HTML elementlərinin müxtəlif **vəziyyətləri** ola bilr. Ən çox rast gəlinən hal, siçanı keçidin üzərinə gətirdiyiniz zaman olur. CSS-də belə bir hadisə baş verdikdə fərqli stayl tətbiq etmək mümkündür.

Pseudo-class selectorlar adi seçicilərə əlavə olunur və **kolon** ilə başlayır `:`:

{% highlight css %}
a {
  color: blue;
}

a:hover {
  color: red;
}
{% endhighlight %}
