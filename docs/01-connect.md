# Connect

Nebim V3 Integrator’da işlemleri gerçekleştirebilmek için öncelikle **Connect** ile bağlantı kurulması gerekir.

Connect işlemi iki farklı çalışma modunda yapılabilir:

- **Session ile Login**
- **Token ile Login**

Integrator’de login işleminde session veya token seçenekleri kullanılabilir.  

IIS üzerindeki serviste **Oturum Durumu** altında **Oturum Durumu Modu Ayarları** kısmında:

- **İşlem İçi (InProc)** seçili ise → Session ile connect olunur.
- **Etkinleştirilmedi (Off / Disabled)** ise → Token ile connect olunur.

---

## Login Kullanıcı Bilgisi

Servis kurulumunda **Web.config** dosyası içerisinde Nebim V3 kullanıcı bilgileri tanımlı ise, Connect modelinde body içerisinde kullanıcı bilgileri gönderilmeden bağlantı kurulabilir.

Alternatif olarak kullanıcı bilgileri Connect modelinde gönderilerek login işlemi yapılabilir.

Login olunan kullanıcının tipi önemlidir:

- **Yetkili Ofis Kullanıcısı** → Birden fazla ofis için işlem yapılabilir.
- **Mağaza Kullanıcısı** → Sadece ilgili mağaza adına işlem yapılmalıdır.

---

## Detaylı Anlatım

- 👉 [Session ile Login ve Doğrulama](./01-1-session-login.md)
- 👉 [Token ile Login ve Doğrulama](./01-2-token-login.md)
