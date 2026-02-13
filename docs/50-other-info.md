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
