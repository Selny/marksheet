---
layout: post
title: "HTML <strong>Tables</strong>"
subtitle: "For <strong>multi-dimensional</strong> data"
section: html
---

HTML **cədvəllər** yalnız **cədvəl məlumatları** üçün nəzərdə tutulub, w**sətirlərdə** və **sütunlarda** semantik düzülə bilən istənilən məzmun növüdür.

Bu, Excel-də **elektron cədvəlin** olması kimidir.

### Sintaksis

HTML-də cədvəl qurmaq **xüsusi bir struktur** tələb edir:

* `<table>` teqini acin
* `<tr>` ilə sətirləri əlavə edin
* `<td>` ilə _müntəzəm_ xanalar və ya '<th>` ilə _başlıq_ xanaları əlavə edin

Bu **iyerarxiya** tələb olunur, və bu 3 elementin hamisi cədvəl düzəltmək üçün zəruridir.

Kod yazarkən, cədvəlinizin hüceyrələrini soldan sağa doğru təyin etmək lazımdır, və _sonra_ aşağıdan.

{% highlight html %}
<table>
  <tr>
    <td>John Lennon</td>
    <td>Rhythm Guitar</td>
  </tr>
  <tr>
    <td>Paul McCartney</td>
    <td>Bass</td>
  </tr>
  <tr>
    <td>George Harrison</td>
    <td>Lead Guitar</td>
  </tr>
  <tr>
    <td>Ringo Starr</td>
    <td>Drums</td>
  </tr>
</table>
{% endhighlight %}

<div class="result">
  <table>
    <tr>
      <td>John Lennon</td>
      <td>Rhythm Guitar</td>
    </tr>
    <tr>
      <td>Paul McCartney</td>
      <td>Bass</td>
    </tr>
    <tr>
      <td>George Harrison</td>
      <td>Lead Guitar</td>
    </tr>
    <tr>
      <td>Ringo Starr</td>
      <td>Drums</td>
    </tr>
  </table>
</div>

Gördüyünüz kimi,HTML-də cədvəl nisbətən **müfəssəldir**: yalnız bir neçə sıra məlumat üçün çoxlu etiketlər var.

### thead, tfoot və tbody

Vebsəhifə kimi header və footer-i ola bilər, **table**-in head-i ola bilər, body, və foot. HTML-dəki hər hansi bir element kimi, bu sırf **semantik** səbəblərdəndir: cədvəlinizə daha çox quruluş verir.

`<thead>`, `<tfoot>` və `<tbody>` sadəcə sətir kolleksiyalarıdır. `<table>`-in birbaşa uşaqlarıdır və bir və ya daha çox `<tr>`-in _birabaşa_  valideyinləridir. qısacası, **iyerarxiyanın bir səviyyəsini** daha əlavə edirlər.

`<thead>` və `<tfoot>` sütunların **qısa məzmunu** kimi istifadə olunur.

Gəlin əvvəlki cədvəli `<thead>` və `<tbody>` ilə gücləndirək:

{% highlight html %}
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Instrument</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>John Lennon</td>
      <td>Rhythm Guitar</td>
    </tr>
    <tr>
      <td>Paul McCartney</td>
      <td>Bass</td>
    </tr>
    <tr>
      <td>George Harrison</td>
      <td>Lead Guitar</td>
    </tr>
    <tr>
      <td>Ringo Starr</td>
      <td>Drums</td>
    </tr>
  </tbody>
</table>
{% endhighlight %}

<div class="result">
  <table>
    <thead>
      <tr>
        <th>Name</th>
        <th>Instrument</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>John Lennon</td>
        <td>Rhythm Guitar</td>
      </tr>
      <tr>
        <td>Paul McCartney</td>
        <td>Bass</td>
      </tr>
      <tr>
        <td>George Harrison</td>
        <td>Lead Guitar</td>
      </tr>
      <tr>
        <td>Ringo Starr</td>
        <td>Drums</td>
      </tr>
    </tbody>
  </table>
</div>

### tfoot özəllikləri

Gəlin cədvəlimizə həmçinin `<tfoot>` əlavə edək

{% highlight html %}
<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Instrument</th>
    </tr>
  </thead>
  <tfoot>
    <tr>
      <th>Name</th>
      <th>Instrument</th>
    </tr>
  </tfoot>
  <tbody>
    <tr>
      <td>John Lennon</td>
      <td>Rhythm Guitar</td>
    </tr>
    <tr>
      <td>Paul McCartney</td>
      <td>Bass</td>
    </tr>
    <tr>
      <td>George Harrison</td>
      <td>Lead Guitar</td>
    </tr>
    <tr>
      <td>Ringo Starr</td>
      <td>Drums</td>
    </tr>
  </tbody>
</table>
{% endhighlight %}

<div class="result">
  <table>
    <thead>
      <tr>
        <th>Name</th>
        <th>Instrument</th>
      </tr>
    </thead>
    <tfoot>
      <tr>
        <th>Name</th>
        <th>Instrument</th>
      </tr>
    </tfoot>
    <tbody>
      <tr>
        <td>John Lennon</td>
        <td>Rhythm Guitar</td>
      </tr>
      <tr>
        <td>Paul McCartney</td>
        <td>Bass</td>
      </tr>
      <tr>
        <td>George Harrison</td>
        <td>Lead Guitar</td>
      </tr>
      <tr>
        <td>Ringo Starr</td>
        <td>Drums</td>
      </tr>
    </tbody>
  </table>
</div>

Həmçinin cədvəlimizə `<tbody>`-dən **əvvələ** `<tfoot>` əlavl etdik, hələdə **sonda** görünür.

Bu ondan irəli gəlir ki, `<tbody>` çoxlu sayda cərgələrdə ibarət ola bilər. Ancaq brauzer sətirlərdən əvvəl _foot_-ı göstərmək istəyir. buna görə də `<tfoot>` kodda birincidir.

### colspan və rowspan

Siz müvafiq olaraq 'rowspan' və 'colspan' istifadə edərək sütun və ya sətirləri **birləşdirə bilərsiniz**.

Unutmayın ki, sütunları birləşdirmək üçün `rowspan` atributundan istifadə etməlisiniz, çünki o, bir neçə _sətir_ arasında **sütun** _aşdırmağa_ imkan verir.

{% highlight html %}
<table>
  <tr>
    <th colspan="2">Michael Jackson Singles</th>
  </tr>
  <tr>
    <th rowspan="3">1979</th>
    <td>Don't Stop 'Til You Get Enough</td>
  </tr>
  <tr>
    <td>Rock with You</td>
  </tr>
  <tr>
    <td>Off the Wall</td>
  </tr>
</table>
{% endhighlight %}

<div class="result">
  <table>
    <tr>
      <th colspan="2">Michael Jackson Singles</th>
    </tr>
    <tr>
      <th rowspan="3">1979</th>
      <td>Don't Stop 'Til You Get Enough</td>
    </tr>
    <tr>
      <td>Rock with You</td>
    </tr>
    <tr>
      <td>Off the Wall</td>
    </tr>
  </table>
</div>

"Michael Jackson Singles" xanası iki sütunu əhatə olunur, beləliklə aşağıdakı xanaya iki sətir daxildir.

Çünki "1979" xanası 3 sətirə ayrılır, beləliklə buradakə iki sətir bir elementi ehtiva edir, 1979 sətirinə yer vermək üçün.

Nə qədər elementin əksik və ya artıq olduğunu görmək sizin üçün çətin ola bilər. Əvvəlcə tam 2-in 4-ə cədvəl qurmağın asan bir yolu, və daha sonra `colspan` və `rowspan` əlavə etməklə elementləri _silmək_.  
Bizim vəziyyətimizdə hal hazırda **8** elementimiz olmalıdır. Biz sadəcə **5** element yazmışıq,lakin `colspan="2"` və `rowspan="3"` **3 əlavə xana əlavə edir**.
{: .info}

