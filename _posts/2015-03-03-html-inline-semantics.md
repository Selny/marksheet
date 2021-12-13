---
sxem: post
başlıq: "<strong>Inline</strong> semantics"
altbaşlıq: "Mətn bloku <em>daxilində</em> kiçik başlıqlar"
bölmə: html
---

Paraqraf və listlər mətnin bütün **blokunu** əhatə etməli olsada, bəzən yazı _daxilində_ bir sözə (vəya sözlərə) məna yükləmək isdəyə bilirik.

### Güclü

**Mühim** sözlər üçün `<strong>` taqın işlədin:

<p>
  Bu <strong>mühim gösdrilir</strong> bu yox.
</p>

Təməl olaraq `<strong>` elementi mətni **bold** gösdərir amma yadda saxlayın ki, bu brauzerin özündən aslıdır. `<strong>` elementini _yalnız_ mətnə qalınlıq vermək üçün işlətməyin, **əhəmiyyət** qatmaq üçün işlədin.

### Vurğu

Sözləri _vurğulamaq_ üçün `<em>` taqını işlədin:

<p>
  Bu <em>vurğulanıb</em> bamma bu yox.
</p>

Təməl olaraq `<em>` elementi mətni _italic_ gösdərir amma yadda saxlayın ki, bu brauzerin özündən aslıdır. `<em>` elementini _yalnız_ mətnə italiklik vermək üçün işlətməyin, _vurğlamaq_ üçün işlədin.

By default, `<em>` elements are displayed in _italic_, but keep in mind that it is only the browser's default behavior. Don't use `<em>` _only_ to put some text in italic, but rather to give it _stress emphasis_.

### Qısaltmalar

W3C və CD kimi qısaltmalar `<abbr>` elementin işlədə bilərlər:

<p>
  Özümə <abbr>CD</abbr> aldım.
</p>

Siz qısaltmaya `title` **atributu** ilə açığlama verə bilərsiniz, bunlar kurosrla elementin üzərinə gəldikdə gösdərilir:

<p>
  Özümə <abbr title="Compact Disc">CD</abbr> aldım.
</p>

### Sətr daxili statlar

`<blockquote>` **block-səviyyəsi** elementdir. **Iline** versiası belədir: `<q>`:

<p>
  O, <q>“Hello World”</q> dedi və getdi.
</p>

### Digər sətr daxili elementlər

Daha nə qədər gösdərilə biləsi sətr daxili elementlər var [inline semantik elementlər](https://developer.mozilla.org/en/docs/Web/HTML/Element#Inline_text_semantics)  amma biz ən əsaslərını gösdərdik.

*[CD]: Compact Disc
*[W3C]: World Wide Web Consortium
