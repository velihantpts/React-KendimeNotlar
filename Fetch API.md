# React-KendimeNotlar

### Fetch API 

React ile çalışırken API üzerinden veri almak-göndermek oldukça sıkça kullanılan bir konsepttir. Bu API işlemlerini yapan frameworkler olduğu gibi js ile birlikte gelen Fetch API vardır.
Fetch API veriler ile işlem yapmamızı sağlayan bir arayüz sağlar. XMLHttpRequest'in daha güçlü ve esnek hali olarak da görebiliriz.

Fetch API Request ve Response objelerini kullanır. Bildiğimiz üzere bir client-server ilişkişinde requestlerle ne yapmak istediğimizi, ne veri almak istediğimizi server'a iletirken onlardan da bu istekleri işleyip döndürdüklere cevaplara
Response'lar deriz.

* Fetch API'lar nasıl kullanılır?

Fetch API, fetch() fonksiyonu ile asenkron olarak verileri getirmemizi sağlar.
Bu noktada da XMLHttpRequest'ten ayrılan bir özelliği karşımıza çıkıyor, Fetch API promise-based çalışan bir yapıdır. Ayrıca Fetch API CORS gibi gelişmiş HTTP konseptlerini kullanır.
Peki nedir bu promise-based yaklaşım?
  
* Fetch API ve Promise-based yaklaşım
Fetch API, temel olarak Promise tabanlıdır, yani istekler ve yanıtlar Promise nesneleri şeklinde işlenir.
Promis, bir askenkron işlemin sonucunu temsil eden ve bu sonucu başarılı veya başarısız olduğunu belirten bir JavaScript nesnesidir. Promise'ler, bir işlem tamamlandığında veya hata oluştuğunda belirli bir işlemi tetiklemek için kullanılır ve asenkron işlemleri düzenlemeye ve sıralamaya
yardımcı olur.
[Promiselar](!https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
  
```
fetch('https://api.example.com/data')
  .then(response => {
    // İstek başarılı oldu, response işlenir
    return response.json();
  })
  .then(data => {
    // JSON verisi işlendi
    console.log(data);
  })
  .catch(error => {
    // Hata yakalandı
    console.error('Hata:', error);
  });

  ```
* Örnek bir basit Fetch API kullanımı
```
async function logMovies() {
  const response = await fetch("http://example.com/movies.json");
  const movies = await response.json();
  console.log(movies);
}
```
Burada bir JSON dosyasını getirip daha sonra çözümlemek için .json(); fonksiyonu kullanıyoruz.

* Request'in Yapılandırılması
Fetch API ikinci parametre olarak bazı opsiyonel secenekleri yapılandırdığımız init nesnesi alabilir.
```
async function postData(url = "", data = {}) {
  // Default options are marked with *
  const response = await fetch(url, {
    method: "POST", // *GET, POST, PUT, DELETE, etc.
    mode: "cors", // no-cors, *cors, same-origin
    cache: "no-cache", // *default, no-cache, reload, force-cache, only-if-cached
    credentials: "same-origin", // include, *same-origin, omit
    headers: {
      "Content-Type": "application/json",
      // 'Content-Type': 'application/x-www-form-urlencoded',
    },
    redirect: "follow", // manual, *follow, error
    referrerPolicy: "no-referrer", // no-referrer, *no-referrer-when-downgrade, origin, origin-when-cross-origin, same-origin, strict-origin, strict-origin-when-cross-origin, unsafe-url
    body: JSON.stringify(data), // body data type must match "Content-Type" header
  });
  return response.json(); // parses JSON response into native JavaScript objects
}

postData("https://example.com/answer", { answer: 42 }).then((data) => {
  console.log(data); // JSON data parsed by `data.json()` call
});
```
* Fetch API ile post işlemi de yapabiliriz
Aşagıdaki kodda bir JSON dosyasını post ediyoruz.
```
async function postJSON(data) {
  try {
    const response = await fetch("https://example.com/profile", {
      method: "POST", // or 'PUT'
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify(data),
    });

    const result = await response.json();
    console.log("Success:", result);
  } catch (error) {
    console.error("Error:", error);
  }
}

const data = { username: "example" };
postJSON(data);

```
