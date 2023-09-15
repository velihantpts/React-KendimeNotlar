# React-KendimeNotlar

### Component

* React'ın temel yapı taşı componentlerdir. Örnegin html ile `<li>` `<\li>` etiketleri arasında `<a>` etiketi ile bir tıklanabilir liste oluşturduğumuzu düşünelim. Daha sonra bu listeyi CSS ile görünüşünü düzeltip,JavaScript ile dinamik hale getirelim.
İşte tüm işlemleri React bize tek çatı altında yapma olanaığı sunuyor. Ve bu yapıyo `component` diyoruz. Örnegin bir Liste.jsx dosyasımızda bu yapıyı oluşturduğumuzu düşünelim. 
Bu yapıyı her listeye ihtiyacımız olduğu zaman <Liste /> etiketi ile çağırabiliriz. React'ın component bazlı modüler yapısı da tam olarak burada başlıyor.
Yine bir örnekle devam edelim, günümüz web sitelerinin tüm sayfalarında bir nagivasyon cubugu yani navbar bulunmakta. Bu navbarı React'ta bir Navbar componenti olarak tanımlayıp her sayfamızda
```
<HomePage>
  <NavigationHeader>
    <Navbar />
  </NavigationHeader>
</HomePage>

```
şeklinde kullanabiliriz. Peki bu neden gerekli?

* Projelerimiz büyüdükçe aynı bileşeni tekrar tekrar yazmak hem maliyet hem zaman hem de işlemçi güçü acısından kötü etkiliyor.
React'ın kendi sitesinde yazan *React component is a JavaScript function that you can sprinkle with markup.* bu cümle aslında çok önemli, web siteleri popülerleştiği ilk zamanlar geliştiriceler sitelerini hazırladıklarından sonra üzerine biraz javascript 
yazıp az da olsa etkileşimli olmaısnı sağlıyolardı. O zaman için bu avantajlıydı çünkü cok fazla dinamik yapı istenmiyodu. Günümüzde ise her şeyde dinamik yapılar ön plana çıkıyor. React geliştiriçileri de bu yaklaşımla dinamik yapılar 
üzerine mark-up mantığı ile component yapısına yaklaşımlarını oluşturmuşlar.

Örnek bir component :
```
export default function Profile() {
  return (
    <img
      src="https://i.imgur.com/MK3eW3Am.jpg"
      alt="Katherine Johnson"
    />
  )
}
```
* Componentlerimizi başka yerlerden erişmek için `export` anahtar sözcüğü ile aslında import edilmesine ön hazırlık yaparız. Bu React'a özgü bir özellik değildir.
* React componentleri normal JavaScript fonksiyonları gibi kullanılabilir ama büyük harfle başlamalıdır yoksa çalışmaz.

* Örnek bir Profile componenti ile galeri oluşturma
```
function Profile() {
  return (
    <img
      src="https://i.imgur.com/MK3eW3As.jpg"
      alt="Katherine Johnson"
    />
  );
}

export default function Gallery() {
  return (
    <section>
      <h1>Amazing scientists</h1>
      <Profile />
      <Profile />
      <Profile />
    </section>
  );
}
```
Yukarıda örnekte Profile component'imizi bir fonksiyon gibi oluşturduktan sonra Gallery componentimizin içinde istediğimiz kadar çağırdık.
* React büyük harfle başlayan bir ifade görünce onu component gibi algılarken küçük harfli bir etiketi html tag olarak algılar.
* Peki componentleri aynı sayfada mı yoksa farklı sayfalarda saklayıp mı çağırmak mantıklı?
Bu noktada React'ın resmi dökümantasyonunda eğer component küçük bir işlevi yerine getiriyosa ve aynı sayfadaki component tarafından sık sık kullanılıyorsa aynı sayfada kullanmak mantıklı, ama bir dosya karmaşıklaşıyosa ve compoment başka sayfalar tarafından da kullanılıyosa
ayrı bir sayfada tutmanın avantajlı olduğunu belirtiyor. Bu yazıda React'ın belki de en önemli kavramı olan componentler üzerine derinlemesine incelemeye çalıştık.
