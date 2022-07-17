---
layout: post
title: "The <strong>Flow</strong>"
subtitle: "The <strong>default</strong> behavior of a webpage"
section: css
---

HTML sənədi **canlı** sənəddir

Heş bir CSS tərtib olunmasa belə, HTML sənədinin özünün qaydaları var:

* **fluidity**: məzmunun brauzer olçülərinə necə uyğunlaşdırılmaası
* **ordering**: elementlərin hansı ardıcıllıqla görünməsi
* **stacking**: elementlərin bir birləri üzərində necə görünmələri

Bu təbii davranışları isə **məntiqidir**.

### Fluidity

HTML də, **məzmun** kraldır.

Bütün `block` elementlər **fluid**-dir. Onlar təbii olaraq dizaynlarını daxili məzmunlarına uyğunlaşdıracaqlar:

* **width: 100%**  
blok bütün mövcud genişliyi tutacaq
* **word wrap**  
Əgər blokun inline elementi tək sətirdə olmasa, o zaman həmin element növbəti sətirdə davam edəcək
* **height: auto**  
blokun hündürlüyü daxilindəki məzmunun ölçüsünə uyğun olaraq avtomatik dəyişir

<div class="result" id="result-fluidity">
  <div>
    A block element will fill up the whole <strong>width</strong> available, while its <strong>height</strong> will vary automatically according to the size of its content.
  </div>
  <div>
    This element will be pushed downwards depending on the height of its predecessors.
  </div>
</div>

<style type="text/css">
#result-fluidity{ height: 450px; max-width: 800px;}
#result-fluidity div{ background: coral; padding: 20px;}
#result-fluidity div:first-child{ background: mediumaquamarine; animation: expand 3s alternate infinite both;}

@keyframes expand{
  0%  { width: 100%;}
  100%{ min-width: 100px; width: 50%;}
}
</style>

* `block` default olaraq **tam genişlikdədir**
* **Hündürlüyü** isə məzmunun hündürlüyü qədərdir

### Ordering

HTML elementləri **kodda** necə yazılıbsa həmin **ardıcıllıqla** göstərilir.
Kodda birinci olan -> Brauzerdə də birincidir.

Hər bir <code>block</code> HTML kodunda hansı ardıcıllıqla görünürsə həmin ardıcıllıqla görünür, <strong>yuxarıdan</strong> <strong>aşağı</strong>.

{% highlight html %}
<p>First</p>
<p>Second</p>
<p>Third</p>
<p>Fourth</p>
<p>Fifth</p>
{% endhighlight %}

<div class="result">
  <p>First</p>
  <p>Second</p>
  <p>Third</p>
  <p>Fourth</p>
  <p>Fifth</p>
</div>

### Stacking

Brauzerin **3 ölçüsü** var.

Hər bir HTML elementi xəyali **layer**-a aiddir..

**stack order** elementlərin necə **yerləşdiyindən asılıdır**: child elementləri müvafiq parentlərin **üstlərində** görünür.

* Hər bir **iç-içə ** element əsas elementin üstündə görünür.
*İyerarxiyada **daha dərində olan**, stack daha yüksəkdədir.

{% highlight html %}
<div>
  This parent is behind
  <p>
    This nested child appears <strong>on top</strong> of its parent
  </p>
</div>
{% endhighlight %}

<div class="result">
  <div style="background: midnightblue; color: white; padding: 20px;">
    This parent is behind
    <p style="background: mediumseagreen; padding: 20px;">
      This nested child appears <span style="background: crimson; color: white; padding: 2px 5px;">on top</span> of its parent
    </p>
  </div>
</div>

### Breaking the flow

Brauzerin defolt davranışı _effektiv_ olsa da, dizayn ehtiyaclarınız üçün _kafi_ olmaya bilər.

Bir çox CSS xassəsləri bu axını pozmağa imkan verir:

* `height` və `width` elementlərin **axıcılığını** dəyişə bilər
* `float` elementin davranışını və ətrafını **pozur**
* `position`, `absolute` və `fixed` Elementi Axından **çıxarın**
* `z-index` elementlərin **yığılma sırasını dəyişə bilər**
