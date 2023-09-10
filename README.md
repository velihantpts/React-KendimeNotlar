# React-KendimeNotlar
Bu repo şimdiye kadar öğrendiklerim ve gelecekte öğrenirken kendime rehber olması için notlardan oluşmaktadır.

##  Virtual DOM ve Real DOM nedir ?

* React, Virtual DOM teknolojisi sayesinde performans ve verimlilik açısından büyük avantajlar sunuyor.
  DOM, HTML ve XML gibi bilgilerin programlama dilleri ile iletişim kurabilmesi için geliştirilmiş bir arabirimdir.
  HTML sayfasında bulunan tüm yapılar ve etiketler, birbirleriyle Object-Oriented mantığındaki çocuk-ebeveyn ilişkisi benzeri bir şekilde ilişkilendirilir.
  
  ![image](https://github.com/velihantpts/React-KendimeNotlar/assets/56006189/41bc2ef2-6ac3-4228-9a52-1e874d2cd62a)


  Örneğin, bir `<html>` elementine bağlı `<head>` etiketi altındaki `<title>` etiketi ve bu etiketin içeriği hiyerarşik olarak bağlıdır.
  Virtual DOM ise bu DOM yapısının bellekteki kopyasıdır. Virtual DOM'da nesneler key-value ilişkili olarak tutulur. Yani belleğimizde hem gerçek DOM hem de Virtual DOM beraber saklanır.
  Normal DOM'da sayfada bir güncelleme işlemi olduğunda, DOM nesnelerinin tamamı taranır, bu taramayı takiben tüm DOM yeniden render edilir. Yani, en ufak bir değişiklik bile
  tüm sistemi etkiler ve işlemi tetikler. Bu performans ve hız açısından oldukça verimsizdir. Virtual DOM ise tarama işlemini ortadan kaldırır. Bir güncelleme olduğunda, ilk olarak
  Virtual DOM üzerinde gerçekleşir ve daha sonra bu işlem Virtual DOM işlemi referans alınarak gerçek DOM'a aktarılır. Bu aktarım sırasında React'in kendi algoritmaları ile
  iki DOM arasındaki farklılık kontrol edilir. Eğer bir farklılık bulunursa, sadece değişen kısmı render eder. Bir farklılık yoksa herhangi bir işlem yapılmaz.
  Kısacası, Virtual DOM, performans, zaman ve hız açısından oldukça önemli bir yapıdır.
  
  ![image](https://github.com/velihantpts/React-KendimeNotlar/assets/56006189/d7c9a742-98a0-4cf7-a6b9-f7cd6d19e195)


