### Bir endpointten veri çekme

* Biz genellikle backend'te işlenen ve ön yüze döndürülen verileri endpointler aracılığı ile alırız. Endpointler aslında kapılarımız gibi düşünebiliriz. Bu kapılara istek atıp karşılığında bize dönen cevabı-veriyi 
ön yüzümüzde istediğimiz gibi kullanabiliriz.

*Biz genellikle fetch ve axios kütüphanesi ile verilerimizi işleriz. 

*Aşagıda örnekte `/getQuestions` ve `getQuestions/${selectedOption.value}` endpointlerimizle hem soruları hem de istenilen tekil soruyu alabiliyoruz. Öncellikle
kullanıcıya bir dropdown altında sorular gösterilmekte. Burada kullanıcının seçtiği soru selectedQuestion state'imizde tutulup bu onChange özelliği ile değer değiştikçe güncellenmekte ve useState hookumuzla bu state'de güncellenmekte. 
Bu sayede seçilen soruyu dinamik olarak görüntüleyebiliyoruz.


```
import React, { useState, useEffect } from 'react';
import Select from 'react-select';

function App() {
  const [questions, setQuestions] = useState([]);
  const [selectedQuestion, setSelectedQuestion] = useState(null);
  const [selectedQuestionData, setSelectedQuestionData] = useState({});

  useEffect(() => {
    fetch('/getQuestions')
      .then(response => response.json())
      .then(data => setQuestions(data))
      .catch(error => {
        console.error('API isteği sırasında bir hata oluştu:', error);
      });
  }, []);

  const handleQuestionChange = selectedOption => {
    setSelectedQuestion(selectedOption);
    fetch(`getQuestions/${selectedOption.value}`)
      .then(response => response.json())
      .then(data => setSelectedQuestionData(data))
      .catch(error => {
        console.error('API isteği sırasında bir hata oluştu:', error);
      });
  };

  return (
    <div>
      <h1>Question Verileri</h1>
      <Select
        options={questions.map(question => ({ value: question.id, label: question.text }))}
        onChange={handleQuestionChange}
        value={selectedQuestion}
      />
      {selectedQuestionData.id && (
        <div>
          <h2>Seçilen Soru: {selectedQuestionData.text}</h2>
          <p>Cevap: {selectedQuestionData.answer}</p>
        </div>
      )}
    </div>
  );
}

export default App;


```
