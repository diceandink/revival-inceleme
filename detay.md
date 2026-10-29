# Detay

Ana anlatı [`README.md`](README.md) içinde. Bu dosya, iddiaları kendisi
doğrulamak isteyenler için.

İncelenen iki build:

| Build | Yöntem | Not |
|---|---|---|
| `launcher-1.0.35` | IDA Pro | fonksiyon adresleri sanal adres (VA), imagebase `0x140000000` |
| `launcher-1.0.38` | statik PE + literal tarama | string offset'leri **dosya offset'i** |

Offset'ler build'e bağlıdır.

---

## 1. Binary kimliği

```text
manifest  : https://api.playrevival.co/api/v1/patch/launcher
sürüm     : launcher-1.0.38 (build 254)
boyut     : 40236032
sha256    : f0477745e6a1786b1164bcbb85d74910e05a875a683ff8b13edde25c78355049
```
---

## 2. Gömülü sorgular

Encoding: **UTF-16LE** (ASCII kopyası yok).

| Dosya offset | İçerik |
|---|---|
| `0x22789DE` | `SELECT Index,SerialNumber FROM Win32_DiskDrive` |
| `0x227A042` | `SELECT SerialNumber FROM Win32_BaseBoard` |
| `0x2270BB0` | `SELECT UUID FROM Win32_ComputerSystemProduct` |
| `0x22703B0` | `SOFTWARE\Microsoft\Cryptography` |

Son satır, `HKLM\SOFTWARE\Microsoft\Cryptography\MachineGuid` yolunu
işaret eder.

---

## 3. İlgili import'lar

```text
iphlpapi.dll
  GetAdaptersAddresses
  GetIfEntry2

setupapi.dll
  SetupDiGetClassDevsW
  SetupDiEnumDeviceInfo
  SetupDiGetDeviceInstanceIdW
  SetupDiGetDeviceInterfaceDetailW
  SetupDiGetDeviceRegistryPropertyW

advapi32.dll
  RegQueryValueExW
  RegQueryInfoKeyW
```

Toplam: 37 modül, 662 import.

---

## 4. Alan eşlemesi

| Alan | Kaynak |
|---|---|
| `baseboard_serial` | `Win32_BaseBoard.SerialNumber` |
| `system_disk_serial` | `Win32_DiskDrive.SerialNumber` |
| `system_uuid` | `Win32_ComputerSystemProduct.UUID` |
| `machine_guid` | registry `SOFTWARE\Microsoft\Cryptography` |
| `primary_adapter_mac` | `GetAdaptersAddresses` / `GetIfEntry2` |
| `gpu_*`, adaptör GUID'leri | SetupAPI cihaz numaralandırma |

---

## 5. Sınırlar

- Sunucu kodu incelenmedi. Verilerin sunucuda nasıl saklandığı bilinmiyor.
- İstek gövdesindeki değerlerin ham mı hash'li mi gittiği doğrulanmadı.
- 1.0.38'de yalnızca string/import seviyesinde bakıldı; decompile yok.
  Fonksiyon adları 1.0.35'e aittir.
- Oyun kanalı ayrı bir konu: TLS yok, çerçevelerin bir kısmı düz metin.
  Bu belge onu kapsamıyor.

---

## 6. Not

Bu dosyadaki her değer, herkese açık bir binary'den veya herkese açık bir
HTTP yanıtından geliyor. Gizli bir bilgi sızdırılmıyor: 3DES anahtarı ve
Ed25519 public key zaten binary'nin içinde düz metin olarak duruyor.
