---
layout: post
title: "HTML <strong>Hierarchy</strong>"
subtitle: "It's a big family <strong>tree</strong>"
section: html
---

Hər hansi bir HTML sənədi böyük bir **ailə ağacıdır**, valideyinləri, qardaşları, uşaqları, əcdadları, və nəvələri ilə birlikdə.

Bu bir birlərinin içərisində **yerləşmə** qabiliyyətindən irəli gəlir

### Yuvalama

Gəlin sadə bir paraqraf yazaq və mətnin hissələrini _fərqləndirmək_ yolu ilə onu gücləndirək, iki ədəd maraqlı **inline** elementlər:

{% HTML-i vurğulamaq %}
<p>
  Cənab <strong>Alex Ferguson</strong> bir dəfəsində Flippo İnzaqi haqqında demişdi:<q>"Bu oğlan ofsaydda doğulmalı idi."</q>.
</p>
{% vurğunun sonu %}

<div class="result"><p>Cənab <strong>Alex Ferguson</strong>  bir dəfəsində Flippo İnzaqi haqqında demişdi: <q>"Bu oğlan ofsaydda doğulmalı idi."</q>.</p></div>

Bu qurmada:

* `<strong>` elementi "Alex Ferguson" sozlərini daha vurğulu şekildə göstərir
* `<q>` İnzaqi haqqında statını qeyd edir

Fakt odur ki, `<strong>` **qalın** şekilde ekrana çıxarması **sadəcə brauzerin default davranişidir**. HTML elementlərini onların mənalarına gorə seçməli olduğumuzu xatirlayaq, onların necə göründüklərinə görə deyil.

Bu halda:

*  `<strong>` və `<q>` elementləri `<p>` elementinin alt elementləridir

### Sifariş
_açılan_ və _bağlanan_ teqlər arasinda yerləşdirilmiş elementlər məkanından asılı olaraq necə işləyirlər

Çünki HTML elementləri teqlərin acilmasini ehtiva edir, bağlaniş teqi, və _arasındakı hər şey_, _alt elementdir_ Element mütləq bağlanmalıdır **öncə** _üst element_ baglanır.


{% HTML-i vurğulamaq %}
<!-- This is INVALID code! :-( -->
<p>
  Bu HTML teqi işləməyəcək çünki "strong" teqi burada açıqdır <strong> ancaq sadəcə paraqrafdan sonra bağlanmışdır.
</p></strong>
{% vurğunun sonu %}

çünki `<strong>`, `<p>`dən _sonra_ açılmlşdır (və beləliklə `<p>`-in **alt elementi** hesab olunur), `<strong>` elementi onun üst elementi `<p>` -dən **öncə** bağlanmalıdır. 

{% HTML-i vurğulamaq %}
<!-- This is valid code. :-) -->
<p>
  Bu HTML kodu işləyəcəkdir, çünki "strong" teqi açildi <strong>və bağlandı</strong> düzgün.
</p>
{% vurğunun sonu %}

### Dərinlik

Alt elementlər özləri başqa alt elementləri ehtiva edə bilər, HTML faylı daxilində **dərin hiyerarxiya** yazmaq mümkündür.

Bizim yuxarıdakı paraqrafımız blog **məqaləsinin** bir hissəsi ola bilər:

{% HTML-i vurğulamaq %}
<article>
  <h1>Məşhur futbol sitatları</h1>
  <p>
    Cənab <strong>Alex Ferguson</strong> bir dəfəsində Flippo İnzaqi haqqında demişdi:<q>"Bu oğlan ofsaydda doğulmalı idi."</q>.
  </p>
  <p>
    John Carrew tərəfindən tənqid edildikdə, <strong>Zlatan Ibrahimovic</strong> cavabladı: <q>"Carew futbol ilə nə edir, Mən bunu sadəcə bir portağal ilə edə bilərəm"</q>.
  </p>
  <p>
    <strong>George Best</strong> dedi <q>"Mən içkiyə çox pul xərcləyirəm, quşlara və sürətli maşınlara. Mən İstirahətimi sadəcə israf etdim."</q> nə zaman ki, onun         həyat tərzi ilə əlaqəli soruşduqda.
  </p>
</article>
{% vurğunun sonu %}

<div class="result">
  <article>
    <h1>Məşhur futbol sitatları</h1>
    <p>
      Cənab <strong>Alex Ferguson</strong> bir dəfəsində Flippo İnzaqi haqqında demişdi:<q>"Bu oğlan ofsaydda doğulmalı idi."</q>.
    </p>
    <p>
      John Carrew tərəfindən tənqid edildikdə, <strong>Zlatan Ibrahimovic</strong> cavabladı: <q>"Carew futbol ilə nə edir, Mən bunu sadəcə bir portağal ilə edə             bilərəm"
    </p>
    <p>
      <strong>George Best</strong> dedi <q>"Mən içkiyə çox pul xərcləyirəm, quşlara və sürətli maşınlara. Mən İstirahətimi sadəcə israf etdim."</q> nə zaman ki, onun         həyat tərzi ilə əlaqəli soruşduqda.
    </p>
  </article>
</div>

Bu qurmada:

* `<article>` digər _bütün_ elementlərin **əcdadıdır**.
* `<article>` elementi `<h1>` və  3 `<p>` elementlərinin **valideyini** hesab olunur
* `<h1>` və 3 `<p>` elementləri **qardasdirlar
* Hər bir `<p>` elementi `<strong>` elementinin **valideyini** hesab edilir və onlar `<q>` elementini ehtiva edirlər.
* Hər bir `<h1>`, `<p>`, `<strong>` və`<q>` elementləri hamısı `<article>` elementinin **nəvələridir**.

Ailə ağacı bənzətməsi hələ də HTML yuvasının bir neçə qatını **keçərkən** tətbiq edilir:
* X elementini nəsli X-in daxilində ehtiva olunan her hansı bir elementdir
* **övlad**: elemendin birbaşa nəvəsidir
* Y elementinin əcdadı Y elementini daxilinə alan hər hansi bir elementdir
* **valideyin** sadəcə birinci birbasa əcdaddir
* X elementinin **qardaşı** X ilə eyni alideyinlərə sahib olan hər hansı bir elementdir

### Block and inline nesting

**Block** elements can contain either block or inline elements.

However, **inline** elements can only contain other _inline_ elements [^1].

{% highlight html %}
<!-- This is INVALID code! :-( -->
<strong>
  <p>You can't put a paragraph inside a "strong" tag.
</strong>
{% endhighlight %}

Just remember ancestor/descendant, parent/child, and siblings. This hierarchy will be useful in CSS.

[^1]: the link element `<a>` is the only exception.
