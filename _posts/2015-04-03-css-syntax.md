---
layout: post
title: "CSS <strong>Syntax</strong>"
subtitle: "who{ what: how;}"
section: css
---

Css-in məqsədi görünüş təyin etmək _və_ HTML elementlərinizə Stil verməkdir. Sintaksisi çox rahatdır:

{% highlight css %}
/* A CSS rule */
selector{ property: value;}
{% endhighlight %}

Belədə oxuya bilərsiniz:

{% highlight css %}
who{ what: how;}
{% endhighlight %}

CSS 3-hissəli prosesdir:

* **selector** _nəyin_ hədəf alındığını təyin edir, hansı HTML elementinin
* **property** hansı xarakteristikanın dəyişdiriləcəyini müəyyən edir
* **value** bu xarakteristikaları _necə_ necə dəyişdiriləcəyini müəyyən edir

Bütün bu blok (selector/property/value) **CSS qaydasıdır**.

### Tez bir nümunə

diyək ki, siz bütün **blockquoteların** rəngini dəyişmək istəyirsiniz.

{% highlight html %}
<blockquote>Something something</blockquote>
{% endhighlight %}

**teq adına** fokuslanın (böyük kiçin işarələrini <> və mətni unudun). Bu halda, bütün bunlardan sadəcə _"blockquote"_ qalır. teq adı ilə selektor arasında birbaşa əlaqə var.

Gəlin indi bunu CSS-də **selector** kimi istifadə edək, və bəzi stillər tətbiq edək:

{% highlight css %}
blockquote{ background: lightgreen;}
{% endhighlight %}

Maraqlıdır. Ancaq indi, mətn rəngi ilə arxa fon rəngləri bir biri ilə uyğunlaşmır. Gəlin bunu sübut edək:

{% highlight css %}
blockquote{
  background: lightgreen;
  color: darkgreen;
}
{% endhighlight %}

Beləliklə 2 şey baş verir:

* _ikinci_ xassə/dəyər cütlüyü əlavə etdik, yalnız bir selektoru saxlamaqla: hər hansı selektorlar çoxluğuna istədiyiniz kimi bir neçə xassə təyin edə bilərsiniz
* bütün xassə/dəyərləri öz sətirlərində saxlayərəq: HTML-də kimi, **boşlqlar** önəmli deyil. `{}` `:` və `;`xüsusi xaralterlərdir bunların yazılışlarında fərqlilik olsa dərq edəcə. nəticə etibarilə, CSS-zi istədiyiniz kimi format edə bilərsiniz, onu oxunaqlı etmək üçün, nə qədər ki, onun sintaksisi qüvvədə qalır.

`<blockquote>`HTML elementi **blok** elementdir. onun **inline** tərəf müqabili də var: `<q>`. Çünki onların hər ikisi eyni məqsədə xidmət edirlər (ancaq başqa başqa məzmunlarla), biz onların hər ikisini eyni şəkildə tərtib etmək istərdik. Biz CSS qaydalarını kopyalayıb yapışdıra bilərik ancaq selektorları dəyişmək lazımdır, ancaq təxmin etdiyiniz kimi daha sürətli bir yolu var:

{% highlight css %}
q,
blockquote{
  background: lightgreen;
  color: darkgreen;
}
{% endhighlight %}

İndi isə bizim iki selektorumuz və iki xassəmiz var. nəticədə bizim selektorlar _coxluğumuz_ və xassələr _çoxluğumuz_ var (və onların əlaqəli dəyərləri ilə birlikdə).

Çoxlu selektorlarımızda ola bilər, çoxlu xassələrimiz, və bəzən (lakin nadir hallarda) çoxlu dəyərlərimiz.
{: .info}

### Comments/(Kommentlər)

HTML-də kimi, CSS-də də əl yazısı kommentlərimiz ola bilər:

{% highlight css %}
/* This is a CSS comment */
q,
blockquote{
  background: lightgreen;
  color: darkgreen;
}
/*
Kommentlər sadəcə insanlar tərəfindən oxunmaq üçündür
və komputer tərəfində çevirilməyəcəkdir
*/
{% endhighlight %}
