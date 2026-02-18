# 💡 Servislerde İhtiyaç Olabilecek Önemli Bilgiler

Bu sayfa, **Nebim V3 Integrator** kullanımı sırasında ihtiyaç olunabilecek taleplere çözüm yöntemlerini içermektedir.

---

## 📌 "ApplyCampaign" bilgisi

### Açıklama

Integrator üzerinden modelle sipariş ya da fatura oluştururken , kampanyaların da devreye girmesi isteniyorsa 
kullanılan modelde;

```json
...
 "ApplyCampaign": true,
...
    
```
olarak gönderilmelidir. Bu şekilde tpInvoiceDiscountOffer, tpOrderDiscountOffer tablolarında kayıtlar oluşacaktır.

---

## 📌 Sipariş/Fatura aktarımında 3. Şahıs Firma, EFatura bilgisi

### Açıklama

Integrator üzerinden modelle sipariş ya da fatura oluştururken, 3. Şahıs firma bilgileri **"PostalAddress"** bloğunda ayrıca aşağıdaki gibi gönderilmelidir. Aynı zamanda E-Fatura olarak oluşması da bu şekilde sağlanmaktadır. Burada gönderilen Vergi No E-Faturaya tabi ise fatura e-Fatura olarak oluşur

```json
...
"Lines": [
  {
    "ItemTypeCode": 1,
    "ItemCode": "001",
    ...
  }
],
"PostalAddress": {
  "CompanyName": "Demo Tekstil A.Ş.",
  "FirstName": "",
  "LastName": "",
  "TaxNumber": "123456789",
  "TaxOfficeCode": "034231",
  "IdentityNum": ""
}
}
...
    
```

---
