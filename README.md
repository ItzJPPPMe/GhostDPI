<p align="center">
  <img src="program_icon.png" alt="program_icon" width="680" height="240" style="background-color: #0d1117; border-radius: 12px; padding: 10px;">
</p>

# GhostDPI — Derin Paket İnceleme (DPI) atlatma aracı

**Yapımcı:** ItzJPPPMe

GhostDPI, Türkiye'de bazı internet servis sağlayıcılarında bulunan Derin Paket İnceleme (DPI) sistemlerini atlatmak için tasarlanmış açık kaynak bir araçtır.

- Pasif DPI'yi (optik ayırıcı / port yansıtma) ve sıralı bağlanan Aktif DPI'yi işler
- VPN değildir; oyun ve genel internet kullanımında hız değişikliği yapmaz
- Windows 7 / 8 / 8.1 / 10 / 11 — **yönetici olarak çalıştırmanız** gerekir

> [!NOTE]
> Kaynak kod `src/` altında açıkça paylaşılır.

# Kullanım

İki yöntem vardır: **hizmet kurarak** veya **batch dosyası ile**.

## Hizmet kurarak (Windows açılışında otomatik)

1. [`GhostDPI-0.2.3rc3.zip`](../../releases) dosyasını indirin
2. ZIP'i sabit bir konuma çıkarın (örn. `C:\GhostDPI\`) — taşımayın
3. `service_install_dnsredir_turkey.cmd` dosyasına sağ tıklayın → **Yönetici olarak çalıştır**
4. Açılan pencerede bir tuşa basın; hizmet kurulur ve başlar
5. Kaldırmak için: `service_remove.cmd` → yönetici olarak çalıştır

Alternatif metodlar (SuperOnline vb.): `service_install_dnsredir_turkey_alternative*.cmd`

## Batch dosyası ile (tek seferlik)

1. ZIP'i indirip çıkarın
2. `turkey_dnsredir.cmd` → sağ tık → **Yönetici olarak çalıştır**
3. Pencere kapatılınca GhostDPI durur

Alternatifler: `turkey_dnsredir_alternative*_superonline.cmd`

> Pencere kapandığında program kapanır; yeniden başlatmak gerekir.

# Derleme

Gereksinimler: MinGW-w64 (veya LLVM-MinGW), [WinDivert 2.2.0](https://reqrypt.org/download/WinDivert-2.2.0-D.zip)

```bash
# WinDivert include + lib yollarını vererek
cd src
make clean
make WINDIVERTHEADERS=/path/to/WinDivert/include \
     WINDIVERTLIBS=/path/to/WinDivert/x64 \
     BIT64=1
# 32-bit: BIT64 olmadan, WINDIVERTLIBS=.../x86
```

Çıktı: `src/ghostdpi.exe`

# Depo yapısı

```
GhostDPI/
├── src/
│   ├── ghostdpi.c          # ana program
│   ├── service.c/h         # Windows servisi
│   ├── fakepackets.c/h     # sahte paket üretimi
│   ├── dnsredir.c/h        # DNS yönlendirme
│   ├── ttltrack.c/h        # TTL izleme
│   ├── blackwhitelist.c/h  # siyah/beyaz liste
│   └── Makefile
├── LICENSE
└── README.md
```

# Lisans

Apache License 2.0 — bkz. [`LICENSE`](LICENSE). WinDivert, uthash ve getline bileşenlerinin kendi lisansları `licenses/` altındadır (release paketinde).

# Yasal Uyarı

> [!IMPORTANT]
> Bu uygulamanın kullanımından doğan her türlü yasal sorumluluk kullanan kişiye aittir. Uygulama yalnızca bilgi paylaşımı ve kodlama amaçlarıyla düzenlenmiştir; kullanmak veya kullanmamak kullanıcının kendi seçimidir.
