# Procedure Çağırma (RunProc)

Nebim V3 datası üzerinde özel yazılmış SQL Stored Procedure’leri çalıştırmak için kullanılan modeldir.

---

## Teknik Bilgiler

- **Namespace:** `IntegratorService`
- **Command:** `RunProc`
- **HTTP Method:** `POST`

---

## Erişim Yöntemleri

### Token Yöntemi

**Header**

```
Token: 0AA56F27AF2940CFB10989DA44B57041
```

**URL**

```
http://localhost:801/IntegratorService/RunProc
```

---

### Session Yöntemi

**URL**

```
http://localhost:801/(S(uzr4v2hsttmweooenvsqq5je))/IntegratorService/RunProc
```

---

## JSON Request Örneği

```json
{
  "ProcName": "sp_GetRetailCustomer",
  "Parameters": [
    {
      "Name": "CommAddress",
      "Value": "05555555555"
    },
    {
      "Name": "CommunicationTypeCode",
      "Value": "7"
    }
  ]
}
```

---

## Önemli Kurallar

- `ProcName` alanına, V3 veritabanında mevcut olan ve çalıştırılabilir bir Stored Procedure adı yazılmalıdır.
- Procedure veritabanında gerçekten çalışabilir durumda olmalıdır.
- Gönderilen parametre isimleri, procedure içindeki parametre isimleri ile **birebir aynı** olmalıdır.
- Procedure kaç parametre alıyorsa, o kadar parametre gönderilmelidir.
- Parametre sırası önemli değildir ancak isimler doğru olmalıdır.
- Tüm parametre değerleri **string** olarak gönderilir.

---
