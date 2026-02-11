# Token ile Connect

Token yöntemi, IIS üzerinde **Oturum Durumu (Session State)** devre dışı bırakıldığında kullanılır.

Connect işlemi sonrasında response içerisinde dönen **Token** bilgisi ile işlemler gerçekleştirilir.

Session mantığından farklı olarak URL içerisinde `(S(...))` yapısı bulunmaz.  
Token bilgisi, sonraki isteklerde **Header** kısmında gönderilerek işlem yapılır.

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
```

### Kullanıcı Doğrulama (GetUserInfo)

Kullanıcı bilgileri yanlış olsa bile Connect işlemi sonrasında response olarak her zaman:

"Status": "Connection Created Successfully"

döner.

Bu nedenle kullanıcı validasyonu için alınan **Token** ile `GetUserInfo` çağrısı yapılarak bağlantı doğrulanmalıdır.

---

### GetUserInfo – Request

- **HTTP Method:** POST  
- **Body:** Yok  

**Header:**
```
Token: 0AA56F27AF2940CFB10989DA44B57041
```

**URL:**
http://localhost:801/IntegratorService/GetUserInfo


---

### GetUserInfo – Response (Örnek)

```json
{
  "UserGroupCode": "V3",
  "UserName": "INT",
  "DatabaseName": "TESTV3",
  "LangCode": "TR",
  "DataLangCode": "TR",
  "RecordInfo": "V3   INT",
  "IsOfficeUser": false,
  "IsStoreUser": false,
  "IsWarehouseUser": false,
  "CompanyCode": 1,
  "OfficeCode": "M",
  "StoreCode": "",
  "WarehouseCode": ""
}
```
