# Connect

Nebim V3 Integrator’da işlemleri yapabilmek için önce **Connect** ile bağlantı kurulması gerekir. Connect işlemi için iki farklı çalışma modu vardır: **Session** veya **Token**.

Integrator’de login işleminde session veya token seçenekleri kullanılabilir.  
IIS üzerindeki serviste **Oturum Durumu** altında **Oturum Durumu Modu Ayarları** kısmında:

- **İşlem İçi (InProc)** seçili ise: **Session** ile connect
- **Etkinleştirilmedi (Off / Disabled)** ise: **Token** ile connect olunabilir

---

## Session ile Connect

Connect olduktan sonra oluşan session’ın süresi dolana kadar bağlı kalınacaktır.  
Session kill olduktan sonra tekrar connect olmak gerekir.

---

## Token ile Connect

Connect olduktan sonra response içerisinde dönen token bilgisi ile işlemler yapılabilir.  
Connect olunan V3 kullanıcısının bilgileri değişmediği sürece token geçerlidir.
