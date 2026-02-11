# 🚨 Hata Mesajları ve Çözüm Rehberi

Bu sayfa, **Nebim V3 Integrator** kullanımı sırasında alınabilecek yaygın hata mesajlarını ve çözüm yöntemlerini içermektedir.

---

## 📌 Hata : "The JSON request was too large to be deserialized"

### Çözüm

Model üzerinde bulunan  karakter sayısı çok fazla olduğu için hata alınmaktadır.
Web.config dosyasında <appSettings> </appSettings> etiketleri arasında aşağıdaki komut satırını ekleyiniz.

```xml
...
    <add key="ExceptionPath" value="" />
    <add key="UseAutoLogin" value="false" />
	
    <add key="aspnet:MaxJsonDeserializerMembers" value="150000" /> // bu satır eklenecek
  </appSettings>
```
Kod blogundaki value değeri json modelinizdeki karakter sayısını karşılayacak şekilde düzenlenirse hata çözümlenecektir.


---
