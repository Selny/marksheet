---
sxem: post
başlıq: "HTML <strong>Images</strong>"
altbaşlıq: "Webdəki başlıca olan <strong>media</strong>"
bölmə: html
---

**Şəkillər** Web üzərində olan ilk qeyri-mətn elementidir. Kompüterinizdə olan əksər şəkil formatları brauzerinizdə açıla bilir: `.jpg`, `.gif` (animasiyalı və ya animasıyasız), `.png` (şəffaf və ya qeyri-şəffaf), `.bmp`...

### Sintaksis

**Şəkillər** `<img>` elementin işlədirlər, hansı ki, **özü-bağlanan** elementdir (ancaq açılış taqı var).

`src` atributu şəklin **yerini** bəlirliyir. Linklər vaistəsi ilə, _daxili_ vəya _tam_ URL-lər işlədə bilərsiniz.

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
        <i class="fa fa-image"></i>
        soyuz-spacecraft.jpg
      </li>
    </ul>
  </li>
</ul>

<p>
  Bu paraşutun enişinə baxın!
  <br>
  <img src="soyuz-spacecraft.jpg">
</p>

### Ölçülər

Hər şəklin **2 ölçüsü** olur: **eni** və **uzunluğu**. Bundan öncə gösdərilən paraşut şəklinin ölçüsü 394 piksel en və 284 piksel uzunluğunda idi.

HTML-ə şəkil əlavə edərkən, siz **şəklin ölçüsün bildirməli deyilsiniz**: brauzer özü avtomatik **tam ölçünü** gösdərir.

Baxmayaraq ki, HTML ilə şəklin ölçüsün dəyişə bilərsiniz bunu əsasən CSS ilə edilməyi tövsiyyə olunur, hansı ki, növbəti mövzülarda dəyinmişik.
{: .info}

### Block ya inline? (Blok ya sətr-daxili?)

Baxmayaraq ki, şəklin eni və uzunluğu var, və görünən iri bir dörbucağlıdır, şəkil **HTML block elementi deyildir** əksinə **inline elementdir**.

Bu `<img>` elementinin **özü-bağanan** element olmasına görədir: texniki olaraq daxilində heç bir HTML elementi daşıya bilmədiyindən sətr-daxili element sayılır, 
`<a>`, `<strong>` vəya `<em>` kimi.

Bu sətr-daxili yönü gözlənməyən nəticələr verə bilər:

<div class="result">
  <p>
    Burda bir qurbağa var
    <img src="/images/frog.jpg">
    paraqrafın düz ortasında!
  </p>
</div>

HTML-də **kontent daha əsas** olduğundan şəkillər olduğu yerdən aslı olmayaraq gösdərilir.
