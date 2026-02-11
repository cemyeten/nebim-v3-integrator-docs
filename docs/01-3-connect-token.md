# Token ile Connect

Token yöntemi, IIS üzerinde **Oturum Durumu (Session State)** devre dışı bırakıldığında kullanılır.

Connect işlemi sonrasında response içerisinde dönen **token** bilgisi ile işlemler gerçekleştirilir.

Session mantığından farklı olarak URL içerisinde `(S(...))` yapısı bulunmaz.  
Token bilgisi sonraki isteklerde Header kısmında token key gönderilerek işlem yapılır.

---

## Teknik Bilgiler

- **Namespace:** IntegratorService  
- **Command:** Connect  
- **HTTP Method:** POST  

---

## Request

**URL:**

http://localhost:801/IntegratorService/Connect

**Body:**

```json
{
  "DatabaseName": "TESTV3",
  "UserGroupCode": "V3",
  "UserName": "INT",
  "Password": "1"
}
```

**Örnek Response**

```json
{
  "ModelType": 0,
  "Status": "Connection Created Successfully",
  "StatusCode": 200,
  "Token": "0AA56F27AF2940CFB10989DA44B57041"
}
