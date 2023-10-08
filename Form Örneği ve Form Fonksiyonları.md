### Form Örneği ve Form Fonksiyonları
Aşagıda bulunan kodda  Form verilerini yönetmek için bir custom hook tanımlıyoruz. Custom hook, bir fonksiyonun içinde useState hook’unu kullanarak form verilerini state’de tutar ve bunları değiştirmek veya sıfırlamak için fonksiyonlar döndürür. 
Bu custom hook’u CustomForm bileşeninde çağırarak form verilerine erişiyoruz. Kodun aşağasında fonksiyonları açıklamaya çalıştım.
```
import React, { useState } from 'react';
import { Form, Input, Button, Spin, Alert } from 'antd';
import axios from 'axios';

// Form verilerini yönetmek için bir custom hook tanımlıyoruz
const useForm = (initialValues) => {
  const [inputs, setInputs] = useState(initialValues);

  const handleChange = (event) => {
    // Form alanlarının değerlerini state'de günceller
    const { name, value } = event.target;
    setInputs((prev) => ({ ...prev, [name]: value }));
  };

  const handleReset = () => {
    // Form verilerini boşaltır
    setInputs(initialValues);
  };

  return [inputs, handleChange, handleReset];
};

const CustomForm = () => {
  // Custom hook'u kullanarak form verilerini alıyoruz
  const [inputs, handleChange, handleReset] = useForm({
    name: '',
    email: '',
    message: '',
  });

  // Formun loading ve error durumlarını tutmak için state tanımlıyoruz
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState(null);

  const handleSubmit = async (event) => {
    event.preventDefault();
    setLoading(true);
    setError(null);
    try {
      // Form verilerini sunucuya gönderir
      const response = await axios.post('/api/form', inputs);
      setLoading(false);
      alert(response.data.message);
      handleReset();
    } catch (err) {
      setLoading(false);
      // Error durumunu hata mesajı yapar
      setError(err.response.data.message);
    }
  };

  return (
    <Form onSubmit={handleSubmit} layout="vertical">
      <Form.Item label="Adınız">
        <Input
          type="text"
          name="name"
          value={inputs.name}
          onChange={handleChange}
          required
        />
      </Form.Item>
      <Form.Item label="E-posta Adresiniz">
        <Input
          type="email"
          name="email"
          value={inputs.email}
          onChange={handleChange}
          required
        />
      </Form.Item>
      <Form.Item label="Mesajınız">
        <Input.TextArea
          name="message"
          value={inputs.message}
          onChange={handleChange}
          required
        />
      </Form.Item>
      <Form.Item>
        <Button type="primary" htmlType="submit" disabled={loading}>
          Gönder
        </Button>
        <Button type="default" onClick={handleReset} disabled={loading}>
          Sıfırla
        </Button>
        {loading && <Spin />}
        {error && <Alert message={error} type="error" />}
      </Form.Item>
    </Form>
  );
};

export default CustomForm;
```
1. handleChange methodunun ana çalışma mantığı input'un değerleri değiştikçe state'imizi güncellemek olarak düşünebiliriz. Prev ise state'nin önceki değerini tutan bir parametredir. Örneğin
   * name: “Ali”, value: “25”
   * name: “Burak”, value: “30”
   * name: “Cem”, value: “35”
   Bu inputlara sırasıyla girildiğinde, oluşan nesneler şöyle olur:
   * İlk input girildiğinde, state’in önceki değeri boş bir nesnedir. Yani, prev = {}. Bu durumda, setInputs fonksiyonu şöyle çalışır:
   setInputs((prev) => ({ …prev, [name]: value }));
   Bu fonksiyon, prev nesnesinin tüm özelliklerini yeni bir nesneye kopyalar. Ancak, prev nesnesinin hiç özelliği yoktur. Bu yüzden, yeni nesne boştur. Sonra, yeni nesneye name ve value ile belirtilen bir özellik ekler. Bu durumda, name = “Ali” ve value = “25” dir. Bu yüzden, yeni nesne şöyle olur:
   { Ali: “25” }
   Bu nesne, state’in yeni değeri olur.
   * İkinci input girildiğinde, state’in önceki değeri { Ali: “25” } dir. Yani, prev = { Ali: “25” }. Bu durumda, setInputs fonksiyonu şöyle çalışır:
   setInputs((prev) => ({ …prev, [name]: value }));
   Bu fonksiyon, prev nesnesinin tüm özelliklerini yeni bir nesneye kopyalar. Bu durumda, yeni nesne { Ali: “25” } olur. Sonra, yeni nesneye name ve value ile belirtilen bir özellik ekler. Bu durumda, name = “Burak” ve value = “30” dir. Bu yüzden, yeni nesne şöyle olur:
   { Ali: “25”, Burak: “30” }
   Bu nesne, state’in yeni değeri olur.
   * Üçüncü input girildiğinde, state’in önceki değeri { Ali: “25”, Burak: “30” } dir. Yani, prev = { Ali: “25”, Burak: “30” }. Bu durumda, setInputs fonksiyonu şöyle çalışır:
   setInputs((prev) => ({ …prev, [name]: value }));
   Bu fonksiyon, prev nesnesinin tüm özelliklerini yeni bir nesneye kopyalar. Bu durumda, yeni nesne { Ali: “25”, Burak: “30” } olur. Sonra, yeni nesneye name ve value ile belirtilen bir özellik ekler. Bu durumda, name = “Cem” ve value = “35” dir. Bu yüzden, yeni nesne şöyle olur:
   { Ali: “25”, Burak: “30”, Cem: “35” }
   Bu nesne, state’in yeni değeri olur.

2. handleReset fonksiyonu, form verilerini sıfırlamak için kullanıyoruz. Bu fonksiyon useState hook'u ile tuttuğumuz statei değiştirmek için setInputs fonksiyonunu çağırarak state'i initialValues parametresine eşitler. InitialValues parametresi de custom hook'u çağırdığımızda verdiğimiz başlangıç değeridir.
   Dolasıyla kod başlangıç değerine dönmüş olur.
   * handleReset fonksiyonumuzu iki yerde kullanıyoruz. İlki submit butonunda bu sayede verilerimizi server'a gönderdikten sonra formumuzu yeniliyoruz, diğeri de Sıfırla butonumuzda.
     
3. handleSubmit fonksiyonun temel amacı formu, form bilgileini sunucuya göndermektir. Formun onSubmit prop'u olarak veilir, yani formu submit ettiğimiz zaman çalışır.
   * Öncellikle event.preventDefault() fonksiyonu ile formun varsayılan davranışını engelliyoruz. Peki bunun nedeni nedir? Varsayılan davranış sayfanın yenilenmesidir, eğer bu olursa veileri kaybedeceğimiz için bunu engelliyoruz.
   * setLoading(true) fonksiyonunu çağırarak loading durumunu true yapıyoruz, formu göndeilrme süreçinde olduğunu belirtir. Loading durumu true olduğunda Gönder ve Sıfırla butonları disabeled olur.
   * setError(null) ile error durumuunu nullyaparak form gönderiminde bir hata olmadığı gösterilir. Eğer null olmaz ise alert ile hata alındığı bildirilir.
   * axios kütphanesi /api/form/ endpointine input objesini gönderiyoruz. 
