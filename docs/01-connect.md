# Connect

Nebim V3 Integrator’da işlemleri gerçekleştirebilmek için öncelikle **Connect** ile bağlantı kurulması gerekir. Connect işlemi iki farklı çalışma modunda yapılabilir: **Session** veya **Token**.

Integrator’de login işleminde session veya token seçenekleri kullanılabilir.  
IIS üzerindeki serviste **Oturum Durumu** altında **Oturum Durumu Modu Ayarları** kısmında:

- **İşlem İçi (InProc)** seçili ise: **Session** ile connect olunur.
- **Etkinleştirilmedi (Off / Disabled)** ise: **Token** ile connect olunur.

---

## Login Kullanıcı Bilgisi

Servis kurulumunda **Web.config** dosyası içerisinde Nebim V3 kullanıcı bilgileri tanımlı ise, Connect modelinde body içerisinde kullanıcı bilgileri gönderilmeden bağlantı kurulabilir. Bu durumda Web.config içerisinde tanımlı varsayılan kullanıcı ile login olunur.

Alternatif olarak, Web.config dosyasında kullanıcı bilgileri boş bırakılabilir ve Connect modelinde kullanıcı bilgileri gönderilerek login işlemi yapılabilir. Aynı servisi birden fazla entegrasyon kullanacaksa, farklı kullanıcılar ile işlem yapılması bu yöntemle sağlanabilir.

Login olunan kullanıcının tipi önemlidir:

- **Yetkili Ofis Kullanıcısı** tipindeki kullanıcı ile birden fazla ofise ait işlemler gerçekleştirilebilir.
- Sadece belirli bir mağaza adına işlem yapılacaksa **Mağaza Kullanıcısı** tipinde bir kullanıcı tercih edilmelidir.

---

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
  "DatabaseName": "DEMOTEKS",
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
  "DatabaseName": "DEMOTEKS",
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

## Token ile Connect

Connect işlemi sonrasında response içerisinde dönen **token** bilgisi ile işlemler gerçekleştirilir.  
Connect olunan V3 kullanıcısının bilgileri değişmediği sürece token geçerliliğini korur.
