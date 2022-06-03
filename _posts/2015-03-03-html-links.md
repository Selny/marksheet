---
layout: post
title: "HTML <strong>Links</strong>"
subtitle: "The <strong>core</strong> of the Web"
section: html
---

HTML-də **Linklər** vacibdir, İnternet ilk başlarda bir biri ilə **əlaqəli** sənədlərin məlumat şəbəkəsi kimi nəzərdə tutulmuşdu.

HTML-in _HiperMətn_ hissəsi bizim hansı növ bağlantılardan istifadə etdiyimizi müəyyən edir: _hipermətn_ .linklər, a.k.a **hipermətnlər**.

HTML-də, linklər **inline elementlərdir** `<a>` teqi kimi yazilir.

`href` atributu (hipermətn istinadları) linklərin **hədəfini** göstərmək üçün istifadə olunur (basildiqda hara naviqasiya edeceyini göstərir).

{% highlight html %}
<p>
  Nə isə axtarmaq üçün, <a href="https://www.google.com">Google</a>-i ziyarət edin.
</p>
{% endhighlight %}

<div class="result">
  <p>
    Nə isə axtarmaq üçün, <a href="https://www.google.com">Google</a> -i ziyarət edin.
  </p>
</div>

Linklər veb sehifənin qarşılıqlı əlaqəsinin **əsasıjdır**: bir sənəddən başqa bir sənədə naviqasiya etmək üçün linklərdən istifadə edilir.

**3** növ hedef aşkar edə bilərsiniz.

* **lövbər** hədəflər,  _eyni səhifə_ içərisində naviqasiya etmək üçün
* **qohum** URL-lər,adətən _həmin veb sayta_ naviqasiya etmək üçün istifadə olunur
* **şərtsiz** URL-lər, adətən _başqa veb sayta_ naviqasiya eymək üçün istifadə olunur

### Lövbər hədəflər

**Lövbər** _eyni səhifə_ içərisində naviqasiya etmək üçün istifadə olunur. href içərisinə `#` yazmaqla hazırlanır, HTML elementini spessifik `id` atributu ilə hədəf ala bilərsiniz.

məsələn, `<a href="#footer">` elementi eyni HTML sənədi içərisində `<div id="footer">` elementinə hədəf alacaq və naviqasiya edəcək. Bu tip hreflər əsasən **yuxarı qayıt** düymələrində istifadə olunur.

### Qohum URL-lər

_eyni_ vebsayt içərisində başqa bir səhifəyə naviqasiya etmək istəyirsinizsə əgərr, **qohum** URL-lər dən istifadə edə bilərsiniz.

Ancaq nəyə nisbətən? **Cari səhifəyə** nisbətən.

İndi isə sadə bir nümumə edək hansı ki, `my-first-website` folderi içərisində 2 HTML faylı var:

<ul class="files">
  <li>
    <i class="fa fa-folder-o"></i>
    my-first-website
    <ul>
      <li>
        <i class="fa fa-file-code-o"></i>
        home.html
      </li>
      <li>
        <i class="fa fa-file-code-o"></i>
        contact.html
      </li>
    </ul>
  </li>
</ul>

`home.html` də, `contact.html`-ə link etmək istəyirsiniz.

Hər iki fayl **eyni folderin içərisindədir**, `home.html`-in içərisində asanlıqla yaza bilərsiniz:

{% highlight html %}
<p>
  Go to the <a href="contact.html">contact page</a>.
</p>
{% endhighlight %}

<div class="result">
  <p>
    Go to the <a href="contact.html">contact page</a>.
  </p>
</div>

aktual vebsaytda, proseslər oxşardır.

`https://ireallylovecats.com` adında bir vebsatyınızın olduğunu hesab edək hansı ki, içərisində iki ədəd səhifə var: `index.html` və`gallery.html`:

<ul class="files">
  <li>
    <i class="fa fa-folder-o"></i>
    ireallylovecats.com
    <ul>
      <li>
        <i class="fa fa-file-code-o"></i>
        index.html
      </li>
      <li>
        <i class="fa fa-file-code-o"></i>
        gallery.html
      </li>
    </ul>
  </li>
</ul>

`index.html`-də aşağıdakı linki yaza bilərsiniz:

{% highlight html %}
<p>
  Visit the <a href="gallery.html">Gallery</a>!
</p>
{% endhighlight %}

Xatırlayaq: vebsaytlar **komputerdə** saxlanılır eynilə hal hazırda istifadə etdiyimiz kimi. Onlar sadəc **server** adlanır çünki onların yeganə məqsədi vebsaytlara ev sahibliyi etməkdir. Ancaq onların hələ də **adi** komputerlər kimi **faylları** və **folderləri** var.
{: .info}

### Şərtsiz URL-lər

  Əgər siz pişiklərinizin qalereyasını dostlarınızla paylaşmaq istəyirsinizsə, sadəcə `gallery.html`-ə göndərməklə buna nail ola bilməyəcəksiniz, çünki bu **nisbi** URL yalnız eyni **kompüter** və ya eyni **domen**-də olan HTML sənədləri üçün işləyir.

Sizə HTML sənədinizə _complete_ URL lazımdır: `https://ireallylovecats.com/gallery.html`.

Bu URL 3 hissə ilə seqmentlənmişdir:

* **protocol** `https://`
* **domain** `ireallylovecats.com`
* **fayl  yolu** `gallery.html`

Bu **şərtsiz URL** **özünü təmin edəndir**: link formasını harada istifadə etdiyinizin fərqi yoxdur, düzgün faylı tapmaq üçün **bütün** məlumatları ehtiva edir, düzgen domain-də, düzgün protoko olə.

_sizin_ saytınızdan basqa bir sayta keçid eləmək üçün siz şərtsiz URL-lərdən istifadə edirsiniz.

Sizin `https://ireallylovecats.com/gallery.html` faylınızda, yaza bilərsiniz

{% highlight html %}
<p>
  Find more images of my cats on my <a href="https://twitter.com/ireallylovecats">Twitter account</a>!
</p>
{% endhighlight %}

### Nisbi və ya şırtsiz bağlantılar?

Birincidən ikinciyə keçid eləmək istədiyinizi deyək. Ən birbaşa yanaşma şərtsiz URL-lərdən istifadə etməkdir. Beləliklə `<a href="https://ireallylovecats.com/gallery.html">Go the second page</a>` elementini sizin `index.html` faylına əlavə edirsiniz.

Çünki hər iki faylınız eyni folderdə yerləşir, **qohum** URL-lərdən istifadə edə bilərsiniz `<a href="first-blog-post.html">`-i istifadə edərək. Bu istifadəlidir əgər  siz kataloqunuzu dəyişmək istəyirsinizsə: linkləriniz pozulmayacaq, çünki link hədəfləri bir-birilə nisbidir,hər iki faylı eyni vaxtda köçürmək və onları eyni qovluqda saxlamaq şərti ilə. Bu nisbi yanaşma domenləri dəyişdirərkən faydalıdır.
