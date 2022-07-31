---
layout: post
title: "Sass <strong>nesting</strong>"
subtitle: "Reusing the same parent selector"
section: sass
---

### Syntax

Sass-da, **iç içə CSS qaydaları** **iyerarxik selektorlarını** müəyyən etməyə imkan verir:

{% highlight scss %}
.title{
  strong{}
  em{}
}
{% endhighlight %}

This will be compiled into:

{% highlight css %}
.title{}
.title strong{}
.title em{}
{% endhighlight %}

`strong` və `em` `.title` qaydası daxilində (2 əyri mötərizə `{` `}` arasında) göründüyü üçün hər ikisi `.title` əsas seçicisi ilə **öncəyə yazılacaq**.

### Yuvalama məqsədi

[CSS prioriteti](/css-priority.html) çətin ola bildiyindən, CSS qaydalarının bir-birini ləğv etməməsi üçün çoxsaylı sinifləri/teqləri birləşdirərək seçiciləri yazarkən **xüsusi** istifadə etmək adi haldır.

{% highlight css %}
.description{}
.description p{}
.description p a{}
.description p a:hover{}
.description p strong{}
.description table{}
.description table tr{}
.description table tr:nth-child(2n){}
.description table th,
.description table td{}
.description table td.empty,
.description table th.empty{}
.description table th{}
{% endhighlight %}

`.description`-in yenidən yazılmasının qarşısını almaq üçün `&` işarəsindən istifadə edək:

{% highlight scss %}
.description{
  p{}
  p a{}
  p a:hover{}
  p strong{}
  table{}
  table tr{}
  table tr:nth-child(2n){}
  table th,
  table td{}
  table th{}
  table td.empty,
  table th.empty{}
}
{% endhighlight %}

Siz **iç-içə** seçicilər yaratmaq üçün `& p` və `& table` `& `ilə əvəz etməklə daha da irəli gedə bilərsiniz:

{% highlight scss %}
.description{
  p{
    a{
      &:hover{}
    }
    strong{}
  }
  table{
    tr{
      &:nth-child(2n){}
    }
    th,
    td{
      &.empty{}
    }
    th{}
  }
}
{% endhighlight %}

**[HTML nesting](/html-hierarchy.html)** xatırlayırsınızmı? Sass-dakı girinti HTML elementlərinin necə iç-içə yerləşdirildiyini _təkrarlamağa_ imkan verir.

Diqqət yetirin, məsələn, `table` and `.empty`  **bir dəfə** necə yazmışdıq.

O, tam olaraq başladığımız CSS-i yaradacaq:

{% highlight css %}
.description{}
.description p{}
.description p a{}
.description p a:hover{}
.description p strong{}
.description table{}
.description table tr{}
.description table tr:nth-child(2n){}
.description table th,
.description table td{}
.description table td.empty,
.description table th.empty{}
.description table th{}
{% endhighlight %}

### The ampersand parent selector

Seçiciləri Sass-da yerləşdirdiyiniz zaman o, əsasən _valideyn_selektoru ilə _uşaq_ arasında **boşluq** əlavə edir. Belə ki:

{% highlight scss %}
//scss
.parent{
  .child{}
}

// becomes in css
.parent .child{}
{% endhighlight %}

`.parent` və `.child` arasındakı **boşluq** **iyerarxiyanı** müəyyən edir: bu seçici `class="child"` _within_ `class="valideyn"` içərisində iç-içə daxil edilmiş HTML elementlərini hədəfləyir.

İndi `:hover` kimi **psevdoselektorlardan** istifadə etmək istəsəniz nə olacaq? Yoxsa siz **joined class**lar olan selektora sahib olmaq istəyirsiniz? Siz parent  seçicisi üçün qısa yol olan **ampersand** istifadə edə bilərsiniz:

Now, what if you want to use **pseudo-selectors** like `:hover`? Or you want to have a selector with **joined classes**? You can use the **ampersand** which is shortcut for the parent selector:

{% highlight scss %}
//scss
.parent{
  &:hover{}
  &.other-class{}
}

// becomes in css
.parent:hover{}
.parent.other-class{}
{% endhighlight %}

`.valideyn` və `:hover` və ya `.digər sinif` arasında necə **boşluğun** olmadığına diqqət yetirin.

`.parent.other-class`, `class="parent other-class"` olan HTML elementlərini hədəf alacaq.

### Full example

{% highlight css %}
.post-content{}
.post-content a{}
.post-content a:hover{}
.post-content aside{}
.post-content blockquote{}
.post-content code{}
.post-content h3{}
.post-content h3 a{}
.post-content h4{}
.post-content h4:before{}
.post-content h4:after{}
.post-content p{}
.post-content p:first-child{}
.post-content p:last-child{}
.post-content ul{}
.post-content ul ul{}
.post-content ul ul ul{}
.post-content dl{}
.post-content dl:before{}
.post-content dl dt{}
.post-content dl dd{}
.post-content pre{}
.post-content pre code{}
.post-content table{}
.post-content table tr{}
.post-content table tr:nth-child(2n){}
.post-content table th,
.post-content table td{}
.post-content table th{}
.post-content table td.empty,
.post-content table th.empty{}
.post-content table code{}
.post-content table pre{}
.post-content table pre:before{}
{% endhighlight %}

{% highlight scss %}
.post-content{
  a{
    &:hover{}
  }
  aside{}
  blockquote{}
  code{}
  h3{
    a{}
  }
  h4{
    &:before{}
    &:after{}
  }
  p{
    &:first-child{}
    &:last-child{}
  }
  ul{
    ul{
      ul{}
    }
  }
  dl{
    &:before{}
    dt{}
    dd{}
  }
  pre{
    code{}
  }
  table{
    tr{
      &:nth-child(2n){}
    }
    th,
    td{
      &.empty{}
    }
    th{}
    code{}
    pre{
      &:before{}
    }
  }
}
{% endhighlight %}

