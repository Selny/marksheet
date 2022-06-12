---
layout: post
title: "CSS <strong>Color</strong> units"
subtitle: "Different ways to define <strong>colors</strong>"
section: css
---

**Rənglər CSS-də gelişliklə istifadə olunur, istər mətn rəngi olaraq, istər arxa fon əngi olaraq, gradientlər, kölgələr, istərsə də sərhədlərin rəngi olaraq... CSS-də rəngləri təyin etmənin bir çox yolu vardır, hər iki mütbət və mənfi cəhətləri ilə birlikdə.

`Color` xassəsi mətnin rəngini təyin edir. Bu olduqca sadədir. Daha vacib olan müxtəlif növ **rəng vahidlərinin** mövcud olmasıdır.

### Color names/(Rəng adları)

CSS təmin edir [145 rəng adları](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value), ən sadəsindən (qara, ağ, narıncı, sarı, mavi...) çox spesifik olanlara kimi (çəmənlik, səhləb, al qırmızı...).

{% highlight css %}
body{ color: black;}
a{ color: orange;}
{% endhighlight %}

Çünki rəng adları xatırlamaq üçün çətindir, və çünki siz spesifik bir rəng istəyə bilərsiniz, rəng adları sıxlıqla istifadə olunan deyildir.

### rgb/red.green.blue(qırmızı.yaşıl.mavi)

Komputer manitorları, Televizorlar, mobil telefonlar, hamsı ekrana rəngləri çıxarmaq üçün RGB rəng modellərindən istifadə edirlər. Əsasən, hər bir rəng qırmızı, Yaşıl, və Mavi rənglərin kombinasiyasından meydana gəlir. Qırmızı üçün 256 mümünkün dəyər vardır, Yaşıl və ya Mavi. Çünki komputerlər saymağa 0-dan başlayır (sıfır), maksimum dəyər isə 255-dir.

Hər hansı bir rəngi nəzərə alsaq o qırmızı, yaşıl və mavi rənglərin _kombinasiyasıdır_, və çünki bu üç rəngin hər birinin 256 dəyəri var, `256 * 256 * 256 = 16,777,216` mümükin rəng mövcuddur.

  çünki RGB modeli rənglərin necə göstərildikləri ilə birbaşa əlaqəlidir, CSS rəng vahidinə çevrildi.

Məsələn, bu vebsaytın qırmızı rənginin 219 Qırmızı dəyəri var, 78 Yaşıl, və 68 Mavi:

{% highlight css %}
a{ color: rgb(219, 78, 68);}
{% endhighlight %}

Qara rəngin heç bir nə Qırmızı, nə Yaşı nədə Mavi rəng dəyəri mövcuddur:

{% highlight css %}
body{ color: rgb(0, 0, 0);}
{% endhighlight %}

Başqa bir spektrdan baxdıqda, ağ rəng isə hər birinin Qırmızı, Yaşıl və Qırmızının full dəyərlərini alır:

{% highlight css %}
body{ color: rgb(255, 255, 255);}
{% endhighlight %}

### rgba/red.green.blue.alfa(here alfa is the channel(burada alfa sadəcə bir kanaldır))

`rgba` rəngin vahidi `rgb`-dir hansı ki, biz ona **alfa** kanalı əlavə etmişik sadəcə (0 və 1 aralığındadır, ikilik sistemdə), hansı ki, rəngin nə qədər şəffaf olacağını təyin edir:

{% highlight css %}
body{ color: rgba(0, 0, 0, 0.8);}
{% endhighlight %}

Qara rəngin yüngül səffaf halıdır.
{: .info}

Rənglərin şəffaf olmasının səbəbi sadəcə arxa fon ilə qarışdırmaqdır, nəticədə kontekstdən asələ olaraq biraz fərqli görqnqr. Bu xüsusilə **arxa fon rənglərində** istifadə üçün əlverişlidir.

### hsl and hsla/(hue, saturation, lightness) və (hue, saturation, lightness, alfa)

**HSL**rəng təyin etmənin başqa bir yoludur. Bunu rəng çarxı kimidə düşünə bilərsiniz.

<figure>
<img src="/images/hsl-model.png" alt="HSL model">
<figcaption>
Source: <a href="https://en.wikipedia.org/wiki/HSL_and_HSV#/media/File:Hsl-hsv_models.svg/">Wikipedia</a>
</figcaption>
</figure>

Qırmızı, Yaşıl və Mavi rənglərin kombinasiyasından yaranan rənglər yerinə, siz təyin edirsiniz:

* **Hue** 0 ilə 360 arasında bir dəyərdir, istədiyiniz rəndi təyin edir.
* **Saturation** faiz, 0% ilə 100% aralığındadır, bu rəngdən nə qədər istədiyinizi təyin edir.
* **Lightness** faiz, 0% ilə 100% aralığındadır, bu rəngin nə qədər işıqlı olmağını istədiyinizi təyin edir.

Bir daha, bu vebsaytın qırmızı rənginin HSL-i belədir:

{% highlight css %}
a{ color: hsl(4, 68%, 56%);}
{% endhighlight %}

`4` qırmızı olduğunu göstərir
`68%` qırmızının olduqca qabarıq olduğunu göstərir
`56%` qara ilə ağın aralığında yerləşdiyini göstərir

`hsl` rəng vahidi anlamaq üçün `rgb`-dən daha rahatdır gözlənilən dəyər aydındır. Əsasən 3 hissəyə ayırmaqla rəngi təyin edirsən, və istədiyiniz rəngi tapmaq üçün hər bir dəyərlə oynaya bilər. Əgər sarı rəngdə bir kölgə istəyirsinizsə, `hsl(50, 68%, 56%)` dəyəri ilə başlaya bilərsiniz, və istədiyiniz spesifik kölgəni tapana qədər doyğunluq və parlaqlıq dəyərlərini dəyişə bilərsiniz.
Hesab edirəm ki `hsl`**insan tərəfində oxunabiləndir**, halbuki `rgb` daha çox **komputer tərəfindən oxunabiləndir**.

`hsla` `hsl` ilə eynidirlər, **alfa** dəyərini təyin edə biləcəyimiz dəyər əlavə edilmişdir:

{% highlight css %}
body{ color: hsla(4, 68%, 56%, 0.5);}
{% endhighlight %}

Yuxarıda gördüyünüz şəffaf qırmızı rəngdir.
{: .info}

### Hexadecimal/onaltılıq

CSS-də rənglər həmçinin **onaltılıq dəyərlərlədə ** təyin oluna bilər, `#db4e44` kimi.

Onaltılıq dəyərlərin nə olduğunu anlamaq üçün, gəlin ikilik və onluq dəyərlərin necə işlədiyinə nəzər salaq:

<div class="table">
  <table>
    <tr>
      <th>
        binary
        <em>2 possible values</em>
      </th>
      <td>0</td>
      <td>1</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <th>
        decimal
        <em>10 possible values</em>
      </th>
      <td>0</td>
      <td>1</td>
      <td>2</td>
      <td>3</td>
      <td>4</td>
      <td>5</td>
      <td>6</td>
      <td>7</td>
      <td>8</td>
      <td>9</td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <th>
        hexadecimal
        <em>16 possible values</em>
      </th>
      <td>0</td>
      <td>1</td>
      <td>2</td>
      <td>3</td>
      <td>4</td>
      <td>5</td>
      <td>6</td>
      <td>7</td>
      <td>8</td>
      <td>9</td>
      <td>A</td>
      <td>B</td>
      <td>C</td>
      <td>D</td>
      <td>E</td>
      <td>F</td>
    </tr>
  </table>
</div>

0-9 aralığındakı rəqəmlər və A-F aralığındakı hərflər **simvol** kimi hesab olunur

İnsanlar **onluq** sistemdən istifadə edirlər. Rəqəmləri düzəltmək üçün 10 ədəd simvolumuz var.

**onaltılıq sistemdə**, rəqəmləri düzəltmək üçün 16 simvolumuz var. Çünki 0-9 simvollar kifayət qədər deyik, biz həmçinin A-F simvollarıdan da istifadə edirik. Və 0-dan başlayır. Beləliklə:

* `4` rəqəmi onaltılıqda `4`-dür
* `12` rəqəmi onaltılıqda `C`-dir
* `16` rəqəmi onaltılıqda `10`-dur çünki simvollar bitdikdən sonra (ən sonuncusu `F`-dir), sola ikinci simvol əlavə edin və artırın (`0` olacaq `1`) və sağ tərəfdəki isə sondan başlayacaq ( `F`-dən  `0`-a)

#### Bunu xatırlamalayıqmı?

Qətiyyən yox! Burada sadəcə onaltılıq dəyərlərin necə işlədiyini izah etmək üçün yazmışıq. Unutmamağınız lazım olan ən vacib məsələ sadəcə 16 simvolun olmasıdır.

RGB kimi, onaltılıq rəng dəyərlləri sadəcə Qırmızı, Yaşıl və Mavi rənglərinin kombinasiyasıdır, hər biri onaltılıq dəyərləri təqdim edirlər, qırmızı üçün `DB` kimi, Yaşıl üçün `4E`, və Mavi üçün isə `44` kimi.

Çünki Qırmızı, Yaşıl və Mavinin ancaq ikidəyəri var, onların mümkün dəyərləri `16 * 16 = 256`-dır, Hansı ki, RGB rəng vahidini əks etdiri!

#### O zaman nə üçün RGB istifadə etmirik?

Adətən, rəngləri seçərkən, rəngləri birbaşa **yazmırsınız**. Ya rəng seçici istifadə edirsiniz, ya da fotoşopdan kopyalayıb/yapışdırırsınız, və ya başqa bir yerdən [colour palette](https://www.colourlovers.com/palettes) seçirsiniz.

Onaltılıq dəyərlər **kopyalayıb və yapıışdırmaq üçün** rahatdır, onlar sadəcə 6 xarakterdən ibarətdirlər.

![Photoshop one field for hex](/images/photoshop-color-picker.png)

#### Tək bir sahəni kopyalayıb yapışdırmaq 3 ayrı sahədən daha asandır.

CSS-də, yalnız hexadecimal rəng dəyərini diyez `#` ilə yazmalısınız.

### Hansını seçməli?

Əgər hər hansı şəffaf rəngdən istifadə etmək fikrində deyilsinizsə, **onaltılıq** dəyərlərinə sadiq qalın, onlar kopyalamaq/yapışdırmaq üçün rahatdır və kodunuzda çox yer tutmur.

Bir az şəffaflıq istəyirsinizsə, rənginizi hex-dən rgba-ya çevirin və `rgba` rəng vahidindən istifadə edin.

Rənginizlə birbaşa brauzerdə oynamaq istəyirsinizsə,'hsl' cəhd edin.
