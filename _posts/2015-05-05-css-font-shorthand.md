---
layout: post
title: "CSS <strong>font</strong> shorthand"
subtitle: "A <strong>shortcut</strong> for several font properties"
section: css
---

CSS-də, bəzi xassələr digər bir xassə altında quruplaşa bilər, vaxta və yerə qənaət etmək məqsədilə. 'font' xüsusiyyəti yenidən qruplaşır (aşağıdakı Xüsusi qaydada):

* `font-style`
* `font-variant`
* `font-weight`
* `font-size`
* `line-height`
* `font-family`

Beləliklə 6 xassəni birində təyin edə bilərdiniz:

{% highlight css %}
body{ font: italic small-caps bold 16px/1.5 Arial, sans-serif;}
{% endhighlight %}

Bunlar bu xüsusi ardıcıllıqla yazılmalıdır və slash `font-size` və `line-height` arasında slash  `/` olmalıdır.

Baxmayaraq ki 6 xassəni təyin eləmisəm, yalnız `font-size` və `font-family` məcburidir.Beləliklə, siz onların **defolt** dəyərlərini saxlamaq niyyətindəsinizsə, digər xassələri təyin etməyi buraxa bilərsiniz:

{% highlight css %}
body{ font: bold 16px/1.5 Arial, sans-serif;}
{% endhighlight %}

Çünki `font-style` və `font-variant` təyin olunmalıdır, onlar default dəyərlərini istifadə edəcəklər `normal`.
{: .info}

Diqqətli olun!Əgər siz əvvəllər font xassələrindən birini təyin etmisinizsə və sonra `font` stenoqrafiyasından istifadə etmisinizsə, o, əvvəllər müəyyən edilmiş dəyərləri **əsaslandıracaq**.

{% highlight css %}
body{ font-size: 16px; line-height: 1.5;}
ul{ font: 14px Georgia, serif;}
{% endhighlight %}

`font` da stenoqrafiya, `line-height` təyin edilməmişdir, və ancestor's `1.5` dəyərini itirəcək və default dəyərini `medium` olaraq dəyişəcək (hansı ki, əsasən `1.2` dir).
{: .info}

Başqa stenoqrafiya xassəsi daha mövcuddur, `background`, `border` və `margin` kimi.
