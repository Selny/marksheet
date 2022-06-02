---
layout: post
title: "CSS <strong>border</strong>"
subtitle: "The <strong>edges</strong> of the rectangle"
section: css
---

HTML elementi düzbucaqlı kimi göstərildiyi üçün onun 4 tərəfi ola bilər: yuxarı, aşağı, sol və sağ. Siz bir anda bütün tərəflərə və ya hər tərəfə ayrı-ayrılıqda sərhəd qoya bilərsiniz.

### Border types and location(Sərhəd tipləri)


CSS -də **border** 3 xüsusiyyətə malikdir:

* `border-color` çərçivənin(kənarların,sərhədlərin) rəngini təyin edir 
* `border-style` kənarlar xətt(solid), nöqtəli(dashed), dotted və s formalarda olur
* `border-width` kənarların qalınlığını təyin edir

Çərçivənin da 4 tərəfi var:
* `border-top` üst-kənar
* `border-bottom` alt-kənar
* `border-left` sol-kənar
* `border-right` sağ-kənar

```css
blockquote{ border-color: yellow; border-style: solid; border-width: 1px;}
```

**border** xüsususiyyəti eyni anda 3 xassəni 1 sətirdə birləşdirə bilir.

```css
blockquote{ border: 1px solid yellow;}
```

### Single border (Tək xətt)

Əgər siz dörd tərəfdən yalnız birində sərhəd qurmaq istəyirsinizsə, bu formada yaza biləsiniz.
```css
blockquote{ border-bottom-color: yellow; border-bottom-style: solid; border-bottom-width: 1px;}
```

```css
blockquote{ border-bottom: 1px solid yellow;}
```

#### 3 sərhəd istəsəm nə olar? Onları ayrıca təyin etməliyəmmi?

Təxmin etdiyiniz kimi, 3 xassəyə sahib olmağın ən qısa yolu onların 4-nü təyin etmək və sonra istəmədiyinizi silməkdir:)

```css
blockquote{ border: 1px solid yellow; border-left: none;}
```

### Shorthand combinations

**border**-ə aid bütün xüsusiyyətləri bir daha ayrıca təkrar edək!

<div class="table">
  <table>
    <tr>
      <th>border</th>
      <th>border-color</th>
      <th>border-style</th>
      <th>border-width</th>
    </tr>
    <tr>
      <th>border-top</th>
      <td>border-top-color</td>
      <td>border-top-style</td>
      <td>border-top-width</td>
    </tr>
    <tr>
      <th>border-bottom</th>
      <td>border-bottom-color</td>
      <td>border-bottom-style</td>
      <td>border-bottom-width</td>
    </tr>
    <tr>
      <th>border-left</th>
      <td>border-left-color</td>
      <td>border-left-style</td>
      <td>border-left-width</td>
    </tr>
    <tr>
      <th>border-right</th>
      <td>border-right-color</td>
      <td>border-right-style</td>
      <td>border-right-width</td>
    </tr>
  </table>
</div>

Bu, bir çox CSS xassələridir. Siz adətən yalnız **5 versiyadan** istifadə edəcəksiniz:

* `border`
* `border-top`
* `border-bottom`
* `border-left`
* `border-right`
