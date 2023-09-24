# React-KendimeNotlar

Server Side Rendering aslında klasik bir yaklaşımdır, yani HTML öğelerini server üzerinde gerçekleştirip response olarak client'e gönderme işlemi 
diyebiliriz. Görselde de görüldüğü üzere öncelikle kullanıcının server'a request  atmasıyla birlikte server HTML öğelerini oluştur daha sonra tarayıcı 
gönderir. Bu oluşturma sırasında tarayıcı js kodunuindirir ve çalıştır, bunun ardından sayfa etkileşimli hale gelir. Şunu unutmamak gerekiyo serverdenyanıt gönderilerken
JavaScript kodları aktif değil, client kendi js kodlarını indirerek aktifleştiriyor.

![image](https://github.com/velihantpts/React-KendimeNotlar/assets/56006189/a71e9a60-a340-48b3-8642-a8430c91d2aa)

* Peki neden SSR'in avantajlı olduğu noktalar nelerdir? 
  1. Her sayfa ayrı render edildip HTML formatında döndürüldüğü için arama motoru botları daha rahat okuma yapabilir.
  2. Ön görülebilir performans, ve daha hızlı sayfa açılma hızı sunar.
  3. CSR'a göre bir avantajı da ilk yükleme sırasında kullanıcıyı boş bir sayfada bekletmemektedir.
     
* SSR'ın dezavantajlı olduğu noktalar
  1. Server'a daha fazla yük bindirir.
  2. İşlemler server'da yapıldığı için server maliyetleri yüksektir.
  3. Veri alımı gönderimi gibi hızın önemli olduğu bazı noktalarda CSR'den yavaştır.
  4. Sayfalar arası gezinme CSR'a göre yavaştır, çünkü her geçişte tekrar render edilmektedir.


  * Kullanıcı sayısının çok olmadığı, sayfa sayısının az olduğu basit projelerde daha çok tercih edilmektedir.
 
  * Angular, NextJS, Express JS SSR mantığında çalışır.
