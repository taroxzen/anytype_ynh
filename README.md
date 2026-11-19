# 🧩 anytype_ynh 🚀

**Unofficial YunoHost package for a self-hosted [any-sync](https://github.com/anyproto/any-sync-dockercompose) network — Anytype's sync backend.**  
**Anytype için kendi sunucunu kur: uçtan uca şifreli, yerel öncelikli, eşler arası senkron.**

| 🏷️ | Bilgi / Info |
|---|---|
| 📦 | YunoHost app (packaging v2) |
| 🔐 | End-to-end encrypted / Uçtan uca şifreli |
| 🌍 | P2P sync via any-sync / Eşler arası senkron |
| 🧱 | Docker Compose v2 required / Docker Compose v2 gerekli |
| 🧑‍💻 | Maintainer: [@taroxzen](https://github.com/taroxzen) |
| 🤖 | AI-assisted build / AI destekli hazırlık |
| ⚠️ | Unofficial / Resmi değil |

## 🌐 Diller / Languages

- [🇬🇧 English](#-english)
- [🇹🇷 Türkçe](#-türkçe)

---

<a id="english"></a>

## 🇬🇧 English

Anytype accounts are created inside the client and stay end-to-end encrypted. The server stores and relays encrypted data only — it never sees private keys.

> 🤖 **AI notice:** This package was written and assembled with AI assistance. Review the scripts before trusting them on a production server.

### ✅ Requirements

| Item | Minimum |
|---|---|
| YunoHost | 12.1.17+ |
| Docker | Compose plugin v2 |
| RAM | ~1 GiB available |
| Ports | TCP 1001-1006, UDP 1011-1016 reachable |

### 🚀 Install

```bash
sudo yunohost app install https://github.com/taroxzen/anytype_ynh
```

Or in the webadmin: **Applications → Install → custom app URL** and paste the repository URL.

The installer clones the official compose stack into `/opt/any-sync`, generates random S3/Garage secrets, writes `.env`, and starts the containers.

⚠️ Enter the **origin IP** when asked for the public host. A Cloudflare-proxied hostname will not forward these raw TCP/QUIC ports.

### 🔗 Client setup

Copy `/opt/any-sync/etc/client.yml` from the server and import it in Anytype: **Settings → Network → Self-hosted → Import configuration**. Create your account in the app and save the recovery phrase. There is no server-side registration.

### 🛠️ Management

| Action | Command |
|---|---|
| Upgrade | `sudo yunohost app upgrade anytype -u https://github.com/taroxzen/anytype_ynh` |
| Backup | `sudo yunohost backup create --apps anytype` |
| Containers | `cd /opt/any-sync && sudo docker compose ps` |

> ⚠️ **License:** This packaging is AGPL-3.0. The upstream any-sync compose stack stays MIT, and the Anytype client has its own terms.

---

<a id="türkçe"></a>

## 🇹🇷 Türkçe

Anytype hesabı **istemcide** oluşur. 12 kelimelik kurtarma cümlesi ve şifreleme anahtarı cihazında kalır. Sunucu sadece şifreli veri bloklarını saklar ve eşler arasında aktarır — içeriği okuyamaz.

> 🤖 **AI notu:** Bu paket AI yardımıyla yazıldı ve derlendi. Üretim sunucusunda kullanmadan önce script'leri gözden geçir.

### 🎯 Ne yapar?

| Özellik | Açıklama |
|---|---|
| 🔐 **Şifreleme** | Uçtan uca şifreleme varsayılan; ek ayar gerekmez |
| 🔄 **Eşler arası** | 3 sync node + consensus + coordinator ile space'ler eşler arasında senkron olur |
| 📝 **Kayıt** | Sunucuda kayıt ekranı yok; hesap Anytype uygulamasında oluşturulur |
| 📁 **Veri** | Dosyalar Garage (S3) üzerinde şifreli tutulur |
| 🧩 **Entegrasyon** | YunoHost app olarak listelenir, yedeklenebilir ve güncellenebilir |

### ✅ Gereksinimler

| Gereksinim | Minimum |
|---|---|
| 🖥️ YunoHost | 12.1.17 veya üzeri |
| 🐳 Docker | Compose eklentisi v2 |
| 🧠 RAM | ~1 GiB boş |
| 🔌 Portlar | TCP 1001-1006, UDP 1011-1016 erişilebilir olmalı |

### 🚀 Kurulum

```bash
sudo yunohost app install https://github.com/taroxzen/anytype_ynh
```

Ya da YunoHost arayüzünden: **Uygulamalar → Yükle → özel uygulama URL'si** → repo adresini yapıştır.

Kurulum script'i şunları yapar:

| Adım | İşlem |
|---|---|
| 1️⃣ | Resmi compose deposunu `/opt/any-sync` içine klonlar |
| 2️⃣ | S3 ve Garage secret'larını rastgele üretir |
| 3️⃣ | `EXTERNAL_LISTEN_HOSTS` değerini sorar ve `.env` yazar |
| 4️⃣ | Konteynerları başlatır |

> ⚠️ **Dikkat:** Cloudflare arkasındaki bir domain adresi ham TCP/QUIC portlarını iletmez. "Public host" sorusuna **sunucunun gerçek IP'sini** yaz.

### 🔗 İstemciyi bağlama

1. 📥 `/opt/any-sync/etc/client.yml` dosyasını sunucudan al.
2. ⚙️ Anytype → **Ayarlar → Ağ değiştir → Self-hosted → İçe aktar**.
3. 🔑 Uygulamada hesabını oluştur ve kurtarma cümlesini güvenli yere kaydet.

> 💡 Sunucu tarafında kullanıcı kaydı yoktur. "Kayıt" işlemi tamamen cihazında gerçekleşir.

### 🛠️ Yönetim

| İşlem | Komut |
|---|---|
| ⬆️ Güncelleme | `sudo yunohost app upgrade anytype -u https://github.com/taroxzen/anytype_ynh` |
| 💾 Yedek alma | `sudo yunohost backup create --apps anytype` |
| 📊 Konteyner durumu | `cd /opt/any-sync && sudo docker compose ps` |
| 🔄 Yeniden başlat | `cd /opt/any-sync && sudo docker compose restart` |

### ⚠️ Uyarılar

| Konu | Not |
|---|---|
| 📜 Lisans | Bu paket **AGPL-3.0**; upstream any-sync compose MIT; Anytype istemcisinin ayrı lisansı var |
| 🏷️ Resmiyet | Bu resmi bir YunoHost veya Anytype paketi **değildir** |
| 🌐 URL | `tbtek.site/anytype` gibi kayıtlı adres sadece panel girdisidir; orada web arayüzü yoktur |
| 🔒 client.yml | Bu dosyaya erişen herkes ağa katılabilir; herkese açık yayınlama |

---

Made with ❤️ and 🤖 by [@taroxzen](https://github.com/taroxzen) · 📄 AGPL-3.0 (this package) · upstream any-sync: MIT
