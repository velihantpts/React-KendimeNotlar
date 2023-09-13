# React-KendimeNotlar

### Propsları anlamak

React bileşenleri,componentleri  farklı parçalarını oluşturan bağımsız, yeniden kullanılabilir yapı taşlarıdır. Props bu bağımsız bileşenler arasında veri iletişimini sağlayan
yapılardır. Yani bir bileşenin özellklerini veya verisini başka bir bileşende kullanmak, işlemek istiyorsak propsları kullanıyoruz.

* Bu aktarım  bir üst sınıftan alt sınıfa doğru olur. React bir ata sınıftan cocuk sınıfa aktarımı teşvik eder. Bu teşviğin sebebi aslında uygulamamızı daha iyi kontrol edebilmek, daha test edileiblir uygulamalar
oluşturmak gibi çeşitler sebebiyle olduğu söylenebilir. Linkten bu konuyla ilgili daha derinlemesine incelenebilir [SSOT](https://www.mulesoft.com/resources/esb/what-is-single-source-of-truth-ssot) .

* Propslarda aktarılan veriler, salt okunabilidir. Herhangi bir manipülasyon işlemi yapılamaz.
  
* Veri olarak sayılar, diziler, nesneler gibi çeşitli veri türleri yollanabilir.
  
* İletilen verileri this anahtar kelimesi ile ulaşabilir örneğin aşagıda verilen örnekteki props'a erişmek için `this.ad` kullanabiliriz.

```
import React from 'react';

class Merhaba extends React.Component {
  render() {
    return <div>Merhaba, {this.props.ad}</div>;
  }
}

const App = () => {
  return <Merhaba ad="Ahmet" />;
}

export default App;

```
Yukarıda örnekte Merhaba bileşeni ad propsundaki Ahmet değerini alıp ekrana `Merhaba Ahmet` bastırır.

* Propslarla aynı zamanda işlevsellik, yani fonksiyon da gönderilebilir. Aşagıdaki örnekte bir butona onClick özelligi ile bir fonksiyon iletimi bulunmaktadır.

```
import React from 'react';

function Buton(props) {
  return <button onClick={props.onClick}>Tıkla</button>;
}

function App() {
  function tiklandi() {
    alert('Butona tıklandı!');
  }

  return <Buton onClick={tiklandi} />;
}

export default App;
```

* Gercek hayatta kulanılan bir örnek verelim
 ```
import React from 'react';

function UserProfile(props) {
  return (
    <div>
      <h2>Merhaba, {props.ad}</h2>
      <p>Email: {props.email}</p>
      <p>Ülke: {props.ulke}</p>
    </div>
  );
}

function UserList(props) {
  const kullaniciListesi = props.kullanicilar.map((kullanici) => (
    <UserProfile
      key={kullanici.id}
      ad={kullanici.ad}
      email={kullanici.email}
      ulke={kullanici.ulke}
    />
  ));

  return (
    <div>
      <h1>Kullanıcı Listesi</h1>
      {kullaniciListesi}
    </div>
  );
}

function App() {
  const kullaniciVerileri = [
    {
      id: 1,
      ad: 'Ahmet',
      email: 'ahmet@example.com',
      ulke: 'Türkiye',
    },
    {
      id: 2,
      ad: 'Ayşe',
      email: 'ayse@example.com',
      ulke: 'Türkiye',
    },
    {
      id: 3,
      ad: 'John',
      email: 'john@example.com',
      ulke: 'ABD',
    },
  ];

  return <UserList kullanicilar={kullaniciVerileri} />;
}

export default App;

 ```
UserProfile bileşeni, kullanıcı bilgilerini gösterirken, UserList bileşeni  kullanıcı verislerini alıp bu veriyi işleyerek UserProfile bileşenlerini liste halinde gösterir. 
