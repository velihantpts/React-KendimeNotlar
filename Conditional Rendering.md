### React-KendimeNotlar

# Conditional Rendering

* React'ta belli koşullara göre belli bileşemleri render etmek isteyebiliriz. Bu tarz durumlarda koşullu renderlamayı kullanıyoruz. Bu işlem JS'deki koşullu renderingle aynıdır. 
```
function Greeting(props) {
  if (props.isLoggedIn) {
    return <h1>Welcome back!</h1>;
  } else {
    return <h1>Please log in.</h1>;
  }
}
```
Yukarıda örnekte olduğu gibi bir durumu `If` kosulu ile bağlayıp, şart buysa şu bileşenleri renderla diyebiliyoruz.

* Koşullu renderlamanın tenary operatörü ile kullanılması da oldukça yaygındır.

```
import React from 'react';

function ConditionalRender(props) {
  return (
    <div>
      {props.condition ? (
        <p>Koşul doğru ise bu metin görüntülenir.</p>
      ) : (
        <p>Koşul yanlış ise bu metin görüntülenir.</p>
      )}
    </div>
  );
}

export default ConditionalRender;
```



* Bazen bir bileşenimizi bir koşula bağlayıp eğer o koşul sağlanırsa bir bileşeni renderla dediğimiz durumlarla da karşılaşayabiliyoruz.
  
```
function UserGreeting(props) {
  return <h1>Welcome back, {props.username}!</h1>;
}

function GuestGreeting() {
  return <h1>Please sign up.</h1>;
}

function Greeting(props) {
  const isLoggedIn = props.isLoggedIn;
  if (isLoggedIn) {
    return <UserGreeting username={props.username} />;
  }
  return <GuestGreeting />;
}
```
* Mantıksal operatörlerle renderlama işlemini de kullanabiliriz.
```
import React from 'react';

function ConditionalRender(props) {
  return (
    <div>
      {props.condition && <p>Koşul doğru ise bu metin görüntülenir.</p>}
    </div>
  );
}

export default ConditionalRender;
```
