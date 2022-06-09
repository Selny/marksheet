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

`hsl` rəng vahidi anlamaq üçün `rgb`-dən daha rahatdır gözlənilən dəyər aydındır. Əsasən 3 hissəyə ayırmaqla rəngi təyin edirsən, və istədiyiniz rəngi tapmaq üçün hər bir dəyərlə oynaya bilər. If you want a yellow shade, you can start with a value like `hsl(50, 68%, 56%)`, and alter the Saturation and Lightness value to find the specific shade you're looking for.

I consider `hsl` to be **human-readable**, whereas `rgb` is more **computer-readable**.

`hsla` is the same as `hsl`, with the added value of being able to define an **alpha** value:

{% highlight css %}
body{ color: hsla(4, 68%, 56%, 0.5);}
{% endhighlight %}

A transparent red color.
{: .info}

### Hexadecimal

Colors in CSS can also be defined with **hexadecimal values**, like `#db4e44`.

To understand what hexadecimal values are, let's look at how binary and decimal work:

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

Consider the 0-9 numbers and the A-F letters as **symbols**.

Humans use the **decimal** system. We have 10 symbols to form numbers.

In **hexadecimal**, we have 16 symbols to form numbers. Because 0-9 are not enough symbols, we also use A-F. And it starts at zero. So:

* the number `4` in hexadecimal is `4`
* the number `12` in hexadecimal is `C`
* the number `16` in hexadecimal is `10` because after you've run out of symbols (the last one being `F`), you add a second symbol to the left and increment (`0` becomes `1`) and the right one starts over (from `F` to `0`)

#### Do I have to remember this?

Not at all! It is here to provide an explanation of how hexadecimal values work. The most important thing to remember is that there are 16 hexadecimal symbols.

Just like RGB, a hexadecimal color value is a combination of Red, Green, and Blue, each of them being represent as a hexadecimal value, like `DB` for Red, `4E` for Green, and `44` for Blue.

Because Red, Green or Blue can only have 2 symbols, their possible values are `16 * 16 = 256`, which mirrors the RGB color unit!

#### Why not use RGB then?

Usually, when choosing colors, you **don't write** them directly. You either use a color picker, or copy/paste it from Photoshop, or choose a [colour palette](https://www.colourlovers.com/palettes) somewhere.

Hexadecimal values are easier to **copy and paste**, as they only comprise 6 characters.

![Photoshop one field for hex](/images/photoshop-color-picker.png)

#### It is easier to copy paste a single field than 3 separate ones.

In CSS, you only need to prepend a hexadecimal color value with a hash `#`.

### Which one to pick?

If you don't intend to use any transparent color, stick to **hexadecimal** values, as they are easier to copy/paste and don't take much space in your code.

If you want some transparency, convert your color from hex to rgba, and use the `rgba` color unit.

If you want to play around with your color directly in the browser, try `hsl`.
