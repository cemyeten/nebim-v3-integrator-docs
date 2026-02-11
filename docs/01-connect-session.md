
## Session ile Connect

Connect işlemi sonrasında oluşan session, süresi dolana kadar aktif kalır.  
Session sonlandırıldığında (kill edildiğinde) tekrar Connect işlemi yapılması gerekir.

### Teknik Bilgiler

- **Namespace:** IntegratorService  
- **Command:** Connect  
- **HTTP Method:** GET  

### Request

**URL:**

http://localhost:801/(S(uzr4v2hsttmweooenvsqq5je))/IntegratorService/Connect

**Body:**

```json
{
  "DatabaseName": "TESTV3",
  "UserGroupCode": "V3",
  "UserName": "INT",
  "Password": "1"
}
```

**Örnek response:**
```json
{
  "ModelType": 0,
  "Status": "Connection Created Successfully",
  "StatusCode": 200,
  "SessionID": "uzr4v2hsttmweooenvsqq5je"
}
```

### Kullanıcı Doğrulama (GetUserInfo)

Kullanıcı bilgileri yanlış olsa bile Connect işlemi sonrasında response olarak her zaman:

"Status": "Connection Created Successfully"

döner.

Bu nedenle kullanıcı validasyonu için alınan **SessionID** ile `GetUserInfo` çağrısı yapılarak bağlantı doğrulanmalıdır.

---

### GetUserInfo – Request

- **HTTP Method:** GET  
- **Body:** Yok  

**URL:**
http://localhost:801/(S(uzr4v2hsttmweooenvsqq5je))/IntegratorService/GetUserInfo


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
