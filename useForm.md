# React-KendimeNotlar
### useForm
useFrom hook'u genel olarak formlarımızı yönetmek için kullanılırız. Bazı konuları teorik olarak anlatmak ve anlamak havada kaldığı için bu hooku örnek üzerinden inceleyelim.

```
import React from 'react';
import { useForm } from 'react-hook-form';
function App() {
  const { register, handleSubmit} = useForm();

  const onSubmit=handleSubmit((data => {
  console.log(data);
  }
 
  return (
    <div>
      <h1>React Form Örneği</h1>
      <form onSubmit={handleSubmit(onSubmit)}>
        <label>Adınız:</label>
        <input
          type="text"
          name="firstName"
          ref={register({ required: true, maxLength: 10 })}
        />
        {errors.firstName && (
          <p>Lütfen geçerli bir ad giriniz (en fazla 10 karakter).</p>
        )}

        <label>Soyadınız:</label>
        <input
          type="text"
          name="lastName"
          ref={register({ required: true, maxLength: 10 })} 
        />
        {errors.lastName && (
          <p>Lütfen geçerli bir soyad giriniz (en fazla 10 karakter).</p>
        )}

        <button type="submit">Gönder</button>
      </form>
    </div>
  );
}

export default App;
```
* Öncellikle hookumuzu projemize `import { useForm } from 'react-hook-form';`  ifadesi ile dahil etmemiz gerekiyor.
* Daha sonra `  const { register, handleSubmit} = useForm();` ifadesi ile hookumuzu tanıtıyoruz. Burada handleSubmit işlevini bilmek gerekiyor. Bu fonksiyon eğer
form doğruluması başarılı ise verileri almamızı sağlıyor.
* `const onSubmit=handleSubmit((data => {
   console.log(data);
} ` ile eğer veriler başarılı şekilde alabildiysek konsola yazdırma işlemini yapıyoruz.
* Bundan sonrası useForm'un bize kazandırdığı hata yönetimi ve sınırlamaları kullanmak, burada `register({ required: true, maxLength: 10 }` ile inputumuza gerekli sınırlandırmalarımızı yapabiliriz.
