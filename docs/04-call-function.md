# Query Çağırma (RunQuery)

Nebim V3 datasında tanımlı olan ve **bsReportQuery** tablosunda kayıtlı özel SQL sorgularını çalıştırmak için kullanılan modeldir.
Procedure dışında function ile yapılmak istenirse bu yötem de kullanılabilir.

---

## Teknik Bilgiler

- **Namespace:** `IntegratorService`
- **Command:** `RunQuery`
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
http://localhost:801/IntegratorService/RunQuery
```

---

### Session Yöntemi

**URL**

```
http://localhost:801/(S(uzr4v2hsttmweooenvsqq5je))/IntegratorService/RunQuery
```

---

## JSON Request Örneği

```json
{
  "ModelType": 32,
  "QueryName": "GetProductPriceAndInventory",
  "Criteria": "",
  "Skip": 0,
  "Take": 0
}
```

---

## Parametre Açıklamaları

| Alan | Tip | Zorunlu | Açıklama |
|---|---|---:|---|
| ModelType | integer | ✅ | Model Tip Kodu (32) |
| QueryName | string | ✅ | Çalıştırılacak sorgu adı |
| Criteria | string | ❌ | Sorguya gönderilecek filtre/kriter |
| Skip | integer | ❌ | İlk X kaydı atla |
| Take | integer | ❌ | İlk X kaydı getir |

---

## Önemli Kurallar

- `QueryName` alanına yazılan değer, **NebimV3Master** veritabanındaki `bsReportQuery` tablosunda kayıtlı olmalıdır.
- Eğer sorgu bu tabloda kayıtlı değilse servis `"Kayıt bulunamadı"` hatası döner.
- `Criteria` alanı opsiyoneldir. Sorgu içerisinde dinamik filtre kullanılacaksa buradan gönderilir.
- `Skip` ve `Take` alanları sayfalama (pagination) amacıyla kullanılır.
- Büyük veri listelerinde performans için `Skip` ve `Take` kullanılması önerilir.

---

### Örnek JSON

```json
{
  "ModelType": 32,
  "QueryName": "GetProductPriceAndInventory",
  "Criteria": "ItemCode = 'KML001'",
  "Skip": 0,
  "Take": 10
}
```

---

