---
layout: post
title: "HTML <strong>Semantics</strong>"
subtitle: "HTML is about <strong>meaning</strong>"
section: html
---

HTML teqlərinin məqsədi sənədə **mənanı** çatdırmaqdır. Veb səhifənizin necə göründüyündən narahat olmayın. İstifadə edəcəyiniz hər bir etiketin özünəməxsus funksiyası vardır.

Yazdığınız məzmundan asılı olaraq, mətninizin mənasına uyğun gələn elementi seçə bilərsiniz.

### Struktur elementləri: Səhifənizi təşkil edir

Struktur elementləri səhifənizin **əsas hissələrini** təşkil etməyə imkan verir. Onlar adətən başqa HTML elementlərinin tipində olurlar.

Sadə bir Web səhifə qurarkən aşağıdakı teqlərdən istifadə edirik.

* `<header>` səhifənin **ilk** elementidir. Loqo və slogan kimi componentlər daxil ola bilər.
* `<nav>` websaytın müxtəlif səhifələrinə gedən **linklər** burada yerləşdirilir.
* `<h1>` səhifənin başlığı bu tag-da yazılır.
* `<article>` adətən səhifənin əsas məzmunu yazılır.
* `<footer>` səhifənin **son** elementi kimi, aşağıda yerləşir.

### Text elements: Məzmunun müəyyən edilməsi

Bu struktur elementlərinin içərisində siz adətən məzmununuzun **məqsədini** müəyyən etmək üçün nəzərdə tutulmuş **mətn** elementlərini tapırsınız.

Əsasən istifadə edəcəksiniz:

* `<p>` Paraqraf yazmaq üçün
* `<ul>` yazının altından xətt çəkmək üçün
* `<ol>` nömrələnmiş siyahı
* `<li>` həmin siyahıdakı yazılar

### Inline elements(Daxili elementlər): Mətninizi fərqləndirmək

Mətn elementləri uzun olsa da, müxtəlif məzmunlu ola bildiyi üçün **daxili** elementlər mətninizin hissələrini **fərqləndirməyə** imkan verir.

Çoxlu inline-elements mövcuddur, lakin siz adətən aşağıdakılarla rastlaşacaqsınız:

<ul>
  <li><code>&lt;strong&gt;</code><strong> Önəmli</strong> yazılar üçündür</li>
  <li><code>&lt;em&gt;</code> Yaıları <em>vurğulamaq</em> üçün</li>
  <li><code>&lt;a&gt;</code>  <a href="#">youtube.com</a> link qoymaq üçün</li>
  <li><code>&lt;small&gt;</code> Çox da<small> önəmli olmayan</small> yazılar üçündür</li>
</ul>

<aside class="comments">
 Sadəcə bu HTML kodunu oxumaqla siz hər bir <strong>HTML elementinin</strong> nə demək olduğunu asanlıqla başa düşə bilərsiniz.
</aside>

<article>
  <h1>Səhifənin əsas başlığı</h1>
  <h2>Altyazı</h2>
  <p>
    Digər başqa yazılar və bəzi <em>vurğulu</em> və hətta <strong>vacib</strong> sözlər.
  </p>
  <p>
    Digər paraqraf.
  </p>
  <ul>
    <li>Bir</li>
    <li>İki</li>
    <li>Üç</li>
  </ul>
  <blockquote>
  Bir dəfə dedi
  </blockquote>
</article>
<aside>
  <h3>Axrıncı yazı ola bilər</h3>
  <ul>
    <li><a href="#">Bir</a></li>
    <li><a href="#">Bir</a></li>
    <li><a href="#">Bir</a></li>
  </ul>
</aside>
{% endhighlight %}


### Ümumi elementlər
Göründüyü kimi, heç bir _semantic_ elementi məzmununuz üçün uyğun görünmürsə, lakin siz hələ də HTML elementi daxil etmək istəyirsinizsə, siz iki **ümumi** elementdən birini seçməlisiniz:

* `<div>` blok seviyyəsi elementi
* `<span>` sətir səviyyəsi elementi

Bu HTML elementləri əslində heç nəyi ifadə etməsə də, biz CSS-dən istifadə etməyə başladığımız zaman onlar çox faydalı olacaq!
### Semantika haqqında çox düşünməyin :)

Ancaq bunun üçün narahat olmayın. Hələlik aşağıdakı siyahını bilsəniz başlanğıc üçün bəs edəcəkdir:

<div class="table">
  <table>
    <tr>
      <th>Structure</th>
      <th>Text</th>
      <th>Inline</th>
    </tr>
    <tr>
      <td>
        <code>header</code><br>
        <code>h1</code><br>
        <code>h2</code><br>
        <code>h3</code><br>
        <code>nav</code><br>
        <code>footer</code><br>
        <code>article</code><br>
        <code>section</code>
      </td>
      <td>
        <code>p</code><br>
        <code>ul</code><br>
        <code>ol</code><br>
        <code>li</code><br>
        <code>blockquote</code>
      </td>
      <td>
        <code>a</code><br>
        <code>strong</code><br>
        <code>em</code><br>
        <code>q</code><br>
        <code>abbr</code><br>
        <code>small</code>
      </td>
    </tr>
  </table>
</div>

