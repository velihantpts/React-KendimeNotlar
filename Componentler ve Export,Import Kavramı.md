# React-KendimeNotlar

### Export ve Import 
React Component mantığının temel avantajı  yeniden kullanılabilir oluşundan gelmektedir.Normalde bir dosya içinde componentler oluşturup birbirleri içinde kullanabiliriz. Büyük projelerde ise component sayısı git gide fazlalaşması nedeni ile
aynı dosyada yazmaktansa okunulabilirlik ve esneklik açısından farklı dosyada yazmalıyız.
React projesimizi oluşturduğumuzda  bir root js dosyası olur. Bu genellikle `App.js` isminde olur. Biz bu kök bileşeni isteğimize göre değiştirebiliriz. Genellikle genel react dosya mimarimizi bu root dosyada tutarız. 
Örneğin elimizde aşagıdaki gibi bir App.js'imiz olsun
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
Burada demin bahsettiğimiz gibi tek dosya altında componentlerimiz var, ama biz bunu App.js root dosyasına Galery.js dosyamızdaki import ederek orada componentleri cağırabiliriz.
App.js
```
import Gallery from './Gallery.js';

export default function App() {
  return (
    <Gallery />
  );
}

```
Gallery.js
```
function Profile() {
  return (
    <img
      src="https://i.imgur.com/QIrZWGIs.jpg"
      alt="Alan L. Hart"
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

Burada şuna dikkat etmek gerekiyor. `Galery.js` dosyasında dışa aktarılmayan bir Profile componenti varken dışarı aktarılan yani export edilen bir  `Galery` componenti bulunmakta. Başka dosyada kullancağımız componentleri `export` keywordü ile tanıtırız.
Daha sonra bu componenti kullanıcağımız dosyada `import Gallery from './Gallery.js';` ile içe aktarım işlevini yaparız.

* Default export ve adlandırılmış export

  Genellikle export default ile varsayılan dışa aktarım yapsak da bazen  export function Button() {} tarzında isimlendirilmiş dışa aktarımlar yapmaktayız.
  Şunu unutmamak gerekir. Bir dosyada yalnızca bir adet default export bulunması gerekiyor.
![image](https://github.com/velihantpts/React-KendimeNotlar/assets/56006189/d225ac9e-09ca-4b25-9600-1011b890cd13)
![image](https://github.com/velihantpts/React-KendimeNotlar/assets/56006189/fbad0f14-9063-46d2-afaa-a58999537f45)

Bu konuyu derinlemesine anlamak için refanrs aldığım kaynak : [React.dev](https://react.dev/learn/importing-and-exporting-components) 
