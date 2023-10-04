###  useEffect - useState Örnek 1
```
 const [idCount, setIDSetCount] = useState(0);

 useEffect(() => {
        fetch("/api/idCount") // Soru seti sayısını almak için API
            .then((response) => response.json())
            .then((data) => {
                setIDSetCount(data.idCount);
            })
            .catch((error) => {
                console.error("ID sayısı alınamadı: ", error);
            });
    }, []);
```

Bu yapıdaki ana amacımız ilgili endpointimizle ( `/api/idCount`) id sayısını çekip kullanmak, ilk satırda useState hooku ile birlikte idCount'u tutuyoruz. 
useState'te parantez içine yazılan alan başlangıç değerini ayarlamak içindir. Bu örnekte 0 değerinden başlayıp setIDSetCount ile birlikte değişiklik yapabilceğimizi
ifade ediyoruz. 

Daha sonra useEffect kodunda fetch api `/api/idCount` api'ına istek atıyoruz. `.then` ifadesi istek başarılı olursa çalıştırılır. Burada `response.json()` methodu ile cevabı
JSON formatına çeviriyoruz. Bu dönüşüm cevabı JavaScript nesnelerine döndüşdürmemiz için gereklidir. Bu aşama da başarılı ile tamamlandığında diğer `.then` işleme alınır ve
useState ile tuttuğumuz `idCount`u `setIDSetCount(data.idCount)` ile değiştiririz. Eğer isteğimiz başarılı olmaz ise `console.error` ile loglama işlemizi yapıp hatayı yönetiriz.
