---
footer: false
---

# Giriş {#introduction}

:::info Vue 3 dokümantasyonunu okuyorsunuz!

- Vue 2 desteği **31 Aralık 2023** tarihinde sona erdi. Daha fazla bilgi için [Vue 2 EOL](https://v2.vuejs.org/eol/) sayfasını inceleyin.
- Vue 2'den mi yükseltiyorsunuz? [Geçiş Rehberi](https://v3-migration.vuejs.org/) inceleyin.
:::

<style src="@theme/styles/vue-mastery.css"></style>
<div class="vue-mastery-link">
  <a href="https://www.vuemastery.com/courses/" target="_blank">
    <div class="banner-wrapper">
      <img class="banner" alt="Vue Mastery banner" width="96px" height="56px" src="https://storage.googleapis.com/vue-mastery.appspot.com/flamelink/media/vuemastery-graphical-link-96x56.png" />
    </div>
    <p class="description">Vue'yu <span>VueMastery.com</span> üzerinden video eğitimleriyle öğrenin</p>
    <div class="logo-wrapper">
        <img alt="Vue Mastery Logo" width="25px" src="https://storage.googleapis.com/vue-mastery.appspot.com/flamelink/media/vue-mastery-logo.png" />
    </div>
  </a>
</div>

## Vue Nedir? {#what-is-vue}

Vue (telaffuz: /vjuː/, **view** gibi) kullanıcı arayüzleri oluşturmak için bir JavaScript çerçevesidir. Standart HTML, CSS ve JavaScript üzerine kurulur ve herhangi bir karmaşıklıkta kullanıcı arayüzlerini verimli bir şekilde geliştirmenize yardımcı olan beyan edici, bileşen tabanlı bir programlama modeli sağlar.

İşte minimal bir örnek:

<div class="options-api">

```js
import { createApp } from 'vue'

createApp({
  data() {
    return {
      count: 0
    }
  }
}).mount('#app')

```

</div>
<div class="composition-api">

```js
import { createApp, ref } from 'vue'

createApp({
  setup() {
    return {
      count: ref(0)
    }
  }
}).mount('#app')
```

</div>

```vue-html
<div id="app">
  <button @click="count++">
    Count is: {{ count }}
  </button>
</div>
```

**Çıktı**

<script setup>
import { ref } from 'vue'
const count = ref(0)
</script>

<div class="demo">
  <button @click="count++">
    Count is: {{ count }}
  </button>
</div>

Yukarıdaki örnek, Vue'nun iki temel özelliğini göstermektedir:

- **Beyan Edici Görselleştirme**: Vue, standart HTML'yi bir şablon sözdizimi ile genişletir ve JavaScript durumu temelinde HTML çıktısını beyan edici bir şekilde tanımlamamıza olanak tanır.

- **Reaktivite**: Vue, JavaScript durum değişikliklerini otomatik olarak izler ve değişiklikler olduğunda DOM'u verimli bir şekilde günceller.

Zaten sorularınız olabilir - endişelenmeyin. Dokümantasyonun geri kalanında her küçük detayı ele alacağız. Şimdilik, Vue'nun neler sunduğuna dair genel bir anlayışa sahip olabilmeniz için okumaya devam edin.

:::tip Ön Koşullar
Dokümantasyonun geri kalanının temel HTML, CSS ve JavaScript bilgisi gerektirdiğini varsayar. Ön uç geliştirmeye tamamen yeniyseniz, ilk adım olarak doğrudan bir çerçeveye atlamak en iyi fikir olmayabilir - temelleri kavrayın ve sonra geri gelin! İhtiyaç duyduğunuzda bu [JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/A_re-introduction_to_JavaScript), [HTML](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML) ve [CSS](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps) özetleriyle bilgi seviyenizi kontrol edebilirsiniz. Diğer çerçevelerle daha önce deneyiminiz olması yardımcı olabilir, ancak gerekli değildir.
:::

## İlerleyici Çerçeve {#the-progressive-framework}

Vue, ön uç geliştirmede gereken yaygın özelliklerin çoğunu kapsayan bir çerçeve ve ekosistemdir. Ancak web oldukça çeşitlidir - web üzerinde inşa ettiğimiz şeyler biçim ve ölçek açısından büyük farklılıklar gösterebilir. Bunu göz önünde bulundurarak, Vue esnek ve kademeli olarak benimsenebilir şekilde tasarlanmıştır. Kullanım durumunuza bağlı olarak Vue'yu farklı şekillerde kullanabilirsiniz:

- Derleme adımı olmadan statik HTML'yi geliştirme
- Herhangi bir sayfaya Web Bileşenleri olarak gömme
- Tek Sayfa Uygulaması (SPA)
- Tam yığın / Sunucu Tarafı Oluşturma (SSR)
- Jamstack / Statik Site Oluşturma (SSG)
- Masaüstü, mobil, WebGL ve hatta terminali hedefleme

Bu kavramları göz korkutucu buluyorsanız endişelenmeyin! Eğitim ve rehber, yalnızca temel HTML ve JavaScript bilgisi gerektirir ve bu konularda uzman olmadan takip edebilirsiniz.

Eğer deneyimli bir geliştiriciyseniz ve Vue'yu yığınıza nasıl en iyi şekilde entegre edeceğinizi öğrenmek istiyorsanız veya bu terimlerin ne anlama geldiğini merak ediyorsanız, bunları [Vue'nun Kullanım Yolları](/guide/extras/ways-of-using-vue) bölümünde daha ayrıntılı olarak ele alıyoruz.

Esnekliğine rağmen, Vue'nun nasıl çalıştığına dair temel bilgiler tüm bu kullanım durumlarında ortaktır. Şu anda sadece bir acemi olsanız bile, yol boyunca edindiğiniz bilgiler daha iddialı hedeflerle başa çıkmak için büyüdükçe faydalı olmaya devam edecektir. Eğer bir veteranseniz, çözülemeye çalıştığınız sorunlara göre Vue'yu en uygun şekilde kullanabilir ve aynı verimliliği koruyabilirsiniz. Bu yüzden Vue'ya "İlerleyici Çerçeve" diyoruz: ihtiyaçlarınıza göre büyüyebilen ve uyum sağlayabilen bir çerçeve.

## Tek Dosyalık Bileşenler {#single-file-components}

Çoğu derleme aracı etkinleştirilmiş Vue projelerinde, Vue bileşenlerini **Tek Dosyalık Bileşen** (aynı zamanda `*.vue` dosyaları olarak da bilinir, kısaca **SFC**) olarak adlandırılan HTML benzeri bir dosya formatı kullanarak yazarız. Adından da anlaşılacağı gibi, bir Vue SFC, bileşenin mantığını (JavaScript), şablonunu (HTML) ve stillerini (CSS) tek bir dosyada kapsüller. İşte önceki örneğin, SFC formatında yazılmış hali:


<div class="options-api">

```vue
<script>
export default {
  data() {
    return {
      count: 0
    }
  }
}
</script>

<template>
  <button @click="count++">Count is: {{ count }}</button>
</template>

<style scoped>
button {
  font-weight: bold;
}
</style>
```

</div>
<div class="composition-api">

```vue
<script setup>
import { ref } from 'vue'
const count = ref(0)
</script>

<template>
  <button @click="count++">Count is: {{ count }}</button>
</template>

<style scoped>
button {
  font-weight: bold;
}
</style>
```

</div>

SFC, Vue'nun belirleyici bir özelliğidir ve kullanım durumunuz bir derleme kurulumu gerektiriyorsa Vue bileşenlerini yazmanın önerilen yoludur. [SFC'nin nasıl ve nedenini](/guide/scaling-up/sfc) kendi bölümünde daha fazla öğrenebilirsiniz - ancak şimdilik, Vue'nun tüm derleme araçlarını sizin için ayarlayacağını bilin.

## API Stilleri {#api-styles}

Vue bileşenleri iki farklı API stilinde yazılabilir: **Options API** ve **Composition API**.

### Options API {#options-api}

Options API ile, bir bileşenin mantığını `data`, `methods` ve `mounted` gibi seçenekler içeren bir nesne kullanarak tanımlarız. Seçenekler tarafından tanımlanan özellikler, fonksiyonlar içinde bileşen örneğini işaret eden `this` üzerinde erişilebilir hale gelir:

```vue
<script>
export default {
  // data() fonksiyonundan döndürülen özellikler reaktif durum haline gelir
  // ve `this` üzerinde erişilebilir olur.
  data() {
    return {
      count: 0
    }
  },

  // Methods, durumu değiştiren ve güncellemeleri tetikleyen fonksiyonlardır.
  // Şablonlarda olay işleyicisi olarak bağlanabilirler.
  methods: {
    increment() {
      this.count++
    }
  },

  // Yaşam döngüsü kancaları, bir bileşenin yaşam döngüsünün
  // farklı aşamalarında çağrılır.
  // Bu fonksiyon bileşen monte edildiğinde çağrılacaktır.
  mounted() {
    console.log(`Başlangıç sayısı ${this.count}.`)
  }
}
</script>

<template>
  <button @click="increment">Sayı: {{ count }}</button>
</template>

[Try it in the Playground](https://play.vuejs.org/#eNptkMFqxCAQhl9lkB522ZL0HNKlpa/Qo4e1ZpLIGhUdl5bgu9es2eSyIMio833zO7NP56pbRNawNkivHJ25wV9nPUGHvYiaYOYGoK7Bo5CkbgiBBOFy2AkSh2N5APmeojePCkDaaKiBt1KnZUuv3Ky0PppMsyYAjYJgigu0oEGYDsirYUAP0WULhqVrQhptF5qHQhnpcUJD+wyQaSpUd/Xp9NysVY/yT2qE0dprIS/vsds5Mg9mNVbaDofL94jZpUgJXUKBCvAy76ZUXY53CTd5tfX2k7kgnJzOCXIF0P5EImvgQ2olr++cbRE4O3+t6JxvXj0ptXVpye1tvbFY+ge/NJZt)

### Composition API {#composition-api}

With Composition API, we define a component's logic using imported API functions. In SFCs, Composition API is typically used with [`<script setup>`](/api/sfc-script-setup). The `setup` attribute is a hint that makes Vue perform compile-time transforms that allow us to use Composition API with less boilerplate. For example, imports and top-level variables / functions declared in `<script setup>` are directly usable in the template.

Here is the same component, with the exact same template, but using Composition API and `<script setup>` instead:

```vue
<script setup>
import { ref, onMounted } from 'vue'

// reactive state
const count = ref(0)

// functions that mutate state and trigger updates
function increment() {
  count.value++
}

// lifecycle hooks
onMounted(() => {
  console.log(`The initial count is ${count.value}.`)
})
</script>

<template>
  <button @click="increment">Count is: {{ count }}</button>
</template>
```

[Test Ortamında Kodları Deneyin](https://play.vuejs.org/#eNpNkMFqwzAQRH9lMYU4pNg9Bye09NxbjzrEVda2iLwS0spQjP69a+yYHnRYad7MaOfiw/tqSliciybqYDxDRE7+qsiM3gWGGQJ2r+DoyyVivEOGLrgRDkIdFCmqa1G0ms2EELllVKQdRQa9AHBZ+PLtuEm7RCKVd+ChZRjTQqwctHQHDqbvMUDyd7mKip4AGNIBRyQujzArgtW/mlqb8HRSlLcEazrUv9oiDM49xGGvXgp5uT5his5iZV1f3r4HFHvDprVbaxPhZf4XkKub/CDLaep1T7IhGRhHb6WoTADNT2KWpu/aGv24qGKvrIrr5+Z7hnneQnJu6hURvKl3ryL/ARrVkuI=)

### Hangisini Seçmeli? {#which-to-choose}

Her iki API stili de yaygın kullanım senaryolarını tam olarak kapsayabilir. Aslında, Options API, Composition API üzerine kuruludur! Vue hakkındaki temel kavramlar ve bilgiler iki stil arasında ortaktır.

Options API, bir "bileşen örneği" (`this` örnekte görüldüğü gibi) kavramı etrafında toplanır, bu da tipik olarak OOP (Nesne Yönelimli Programlama) dili geçmişine sahip kullanıcılar için daha sınıf tabanlı bir zihinsel modelle daha iyi uyum sağlar. Ayrıca reaktivite detaylarını soyutlayarak ve seçenek grupları aracılığıyla kod organizasyonunu zorunlu kılarak daha yeni başlayan dostudur.

Composition API, reaktif durum değişkenlerini doğrudan bir fonksiyon kapsamında beyan etme ve karmaşıklığı yönetmek için birden fazla fonksiyondan durumu birleştirme etrafında toplanır. Daha serbest formdadır ve Vue'da reaktivitenin nasıl çalıştığını anlamayı gerektirir. Buna karşılık, esnekliği mantığı organize etmek ve yeniden kullanmak için daha güçlü desenler sağlar.

İki stil arasındaki karşılaştırmayı ve Composition API'nin potansiyel faydalarını [Composition API SSS](/guide/extras/composition-api-faq) bölümünde daha fazla öğrenebilirsiniz.

Vue'ya yeniyseniz, işte genel önerimiz:

- Öğrenme amacıyla, size daha kolay anlaşılan stile gidin. Yine, temel kavramların çoğu iki stil arasında ortaktır. Diğer stili daha sonra her zaman öğrenebilirsiniz.

- Üretim kullanımı için:

  - Derleme araçlarını kullanmıyorsanız veya Vue'yu öncelikle düşük karmaşıklık senaryolarında kullanmayı planlıyorsanız, Options API ile devam edin, örneğin kademeli geliştirme.

  - Vue ile tam uygulamalar oluşturmayı planlıyorsanız, Composition API + Tek Dosyalık Bileşenler ile devam edin.

Öğrenme aşamasında yalnızca bir stile bağlı kalmanız gerekmez. Dokümantasyonun geri kalanı, uygulanabilir yerlerde her iki stilde de kod örnekleri sağlayacak ve sol kenar çubuğunun üst kısmındaki **API Tercih Anahtarları** kullanarak bunlar arasında istediğiniz zaman geçiş yapabilirsiniz.

## Hala Sorularınız mı Var? {#still-got-questions}

[SSS](/about/faq) sayfamıza göz atın.

## Öğrenme Yolunuzu Seçin {#pick-your-learning-path}

Farklı geliştiricilerin farklı öğrenme stilleri vardır. Tercihinize uygun bir öğrenme yolunu seçmekten çekinmeyin - mümkünse tüm içeriği gözden geçirmenizi öneririz!

<div class="vt-box-container next-steps">
  <a class="vt-box" href="/tutorial/">
    <p class="next-steps-link">Eğitimi Deneyin</p>
    <p class="next-steps-caption">Her şeyi uygulamalı olarak öğrenmeyi tercih edenler için.</p>
  </a>
  <a class="vt-box" href="/guide/quick-start.html">
    <p class="next-steps-link">Rehberi Okuyun</p>
    <p class="next-steps-caption">Rehber, çerçevenin her yönünü ayrıntılı olarak ele alır.</p>
  </a>
  <a class="vt-box" href="/examples/">
    <p class="next-steps-link">Örnekleri İnceleyin</p>
    <p class="next-steps-caption">Ana özellikler ve yaygın UI görevlerinin örneklerini keşfedin.</p>
  </a>
</div>

