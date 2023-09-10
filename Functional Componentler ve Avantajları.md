# React-KendimeNotlar

### Functional Component 

React'in 16.8 versiyonu ile birlikte React'in büyük ölçekli olarak değiştiğini söyleyebiliriz. Bu versiyondan önce ana mimari class componentler üzerindeyken bu versiyonla birlikte 
class componentlerin yapabildiği bazı özellikler hook'lar aracılığı ile functional componentlerde de mümkin kılındı. Kısacası hookların gelmesi ile birlikte functional componentlerin oldukça önem kazandığını,React'in bel kemiği haline geldiğini söyleyebiliriz. Peki neden functional componentlere
bazı özellikler kazandırarak class componentler yerine kullanmak istedik ?
Functional componentlerin, class-based componentlere göre bazı avantajları aşagıdaki gibidir.

* Yazması, okunması ve test edilmesi daha kolaydır.
* Daha az kod yazmamızı sağlar
* Daha kolay pratik yapılmasını sağlar.
* Belki en önemlisi React functional componentleri daha hızlı render eder ve daha az bellek harcar.

### Peki nedir bu function component'ler ?

En temelinde bu componentler basit js fonksiyonlarıdır, class componentler gibi function componentler de JSX ifadeler döndürürler. 
Parametre alıp, almamak opsiyoneldir. Bu parametrelere props adı verilir. Bu componentleri istersek normal js fonksiyonu gibi istersek de arrow function olarak tanımlayabiliriz. Arrow function kullanmak kodu daha kısa ve okunaklı hale getirir.

* Arrow function 
```
const Header = () => {
  const titleText = `Lorem ipsum dolor sit amet`;
  return (
    <h1> {titleText}</h1>
  )
}
```
* Normal function 
```
function Header () {
  const titleText = `Lorem ipsum dolor sit amet`;
  return (
    <h1> {titleText}</h1>
  )
}
```
Peki ne zaman arrow function şekline yazmayı, ne zaman da normal js function şeklinde yazmayı tercih edicez ? 
Arrow function şeklinde yazmayı tercih etmenin bazı avantajları vardır

* Kodun daha kısa ve okunaklı olması.
* Fonksiyon kapsamının basitleşmesi. Arrow functionlar, kendi bağlamına sahip olmadığı için, this, arguments veya super gibi bağlayıcıları kullanmazlar. Bu, fonksiyonların başka fonksiyonlara geçirilmesini veya asenkron olarak çağrılmasını kolaylaştırır1.
* Arrow functionlar, async/await gibi özellikleri kullanmanızı sağlar.
  
Arrow function şeklinde yazmayı tercih etmenin bazı dezavantajları vardır

* Arrow functionlar, kendi adlarına sahip olmadığı için, hata ayıklama yapmak zor olabilir.
* Arrow functionlar, constructor olarak kullanılamazlar. Yani new ile çağrıldıklarında TypeError verirler.
* Arrow functionlar, yield ifadesini kullanamazlar ve generator fonksiyon olarak tanımlanamazlar.

Özetle functional componentler, React’in yeni yıldızlarıdır. Hooklar ile birlikte class componentlerin yapabildiği her şeyi yapabilirler ve daha fazlasını sunarlar. 
Functional componentler, kodun kalitesini, performansını ve tekrar kullanılabilirliğini artırır. 

