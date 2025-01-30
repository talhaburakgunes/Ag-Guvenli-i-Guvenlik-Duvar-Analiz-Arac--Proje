# Güvenlik Duvarı Analiz Aracı API

## Projenin Amacı

Bu proje, güvenlik duvarı analizi yapmak ve ağ güvenliğini sağlamak için geliştirilmiş bir API sunmaktadır. Kullanıcılar, belirli bir hedef IP adresine karşı güvenlik duvarı kurallarını inceleyebilir, bypass tekniklerini tespit edebilir ve yapılandırma hatalarını analiz edebilir.

### Ana Özellikler

- **Kural Seti Analizi**: Verilen IP adresindeki güvenlik duvarı kurallarını tarar ve riskli kısımlarını belirler.
- **Bypass Teknik Tespiti**: Hedef ağda olası bypass tekniklerini analiz eder ve potansiyel güvenlik açıklarını tespit eder.
- **Yapılandırma Kontrolü**: Güvenlik duvarı yapılandırmalarını kontrol eder ve önerilen güvenlik iyileştirmeleri hakkında geri bildirim sağlar.

## Gereksinimler

- Python 3.6+
- Flask (Web framework)
- POSTMAN (API istemcisi, test için)

## Kurulum

1. **Python Yükleme**: Python 3.6+ sürümünü yüklediğinizden emin olun.
   
2. **Gerekli Kütüphaneleri Yükleyin**:

```bash
pip install flask requests
Projeyi İndirin: Projeyi GitHub'dan indirin ve uygun bir dizine kaydedin.

Flask Sunucusunu Başlatın: Flask uygulamasını başlatmak için aşağıdaki komutu çalıştırın:

bash
Kopyala
Düzenle
python app.py
POSTMAN Yükleyin: Postman uygulamasını indirip API'yi test edin.
API Kullanımı
Zorunlu Parametreler
API'yi kullanabilmek için gerekli parametreler şunlardır:

hedef_ip (str): Tarama yapılacak IP adresi.
port_araligi (str): Tarama yapılacak port aralığı (örn. 80-443).
Örnek JSON İsteği
json
Kopyala
Düzenle
{
    "hedef_ip": "192.168.1.100",
    "port_araligi": "80-443"
}
Opsiyonel Parametreler
kural_seti_veritabani (str, opsiyonel): Kullanılacak kural seti veritabanı. Varsayılan: "IETF".
ozelleştirilmis_modul (bool, opsiyonel): Özelleştirilmiş bir modül kullanılıp kullanılmayacağını belirtir. Varsayılan: false.
detay_seviyesi (str, opsiyonel): Taramanın detay seviyesini belirtir. Varsayılan: "orta". Değerler: "düşük", "orta", "yüksek".
Örnek JSON İsteği (Opsiyonel Parametrelerle)
json
Kopyala
Düzenle
{
    "hedef_ip": "192.168.1.100",
    "port_araligi": "80-443",
    "kural_seti_veritabani": "IETF",
    "ozelleştirilmis_modul": false,
    "detay_seviyesi": "yüksek"
}
API Sonuçları
API isteği başarılı olduğunda, JSON formatında aşağıdaki gibi bir sonuç dönecektir:

json
Kopyala
Düzenle
{
    "sonuç": {
        "durum": "başarılı",
        "veri": {
            "portlar": [
                {
                    "port": 80,
                    "durum": "açık"
                },
                {
                    "port": 443,
                    "durum": "kapalı"
                }
            ],
            "güvenlik_bypass_tespitleri": [
                {
                    "bypass_teknigi": "TCP FIN Scan",
                    "risk_seviyesi": "yüksek",
                    "açıklama": "Bu teknik, güvenlik duvarının bypass edilmesine yol açabilir."
                }
            ],
            "yapılandırma_uyarilari": [
                {
                    "uyari": "Açık portlar tespit edildi, güvenlik önlemleri alınmalı.",
                    "seviye": "yüksek"
                }
            ]
        }
    }
}
API Endpoints
POST /tarama: Güvenlik duvarı taramasını başlatır.
Test Etme
API'yi test etmek için Postman veya benzer bir araç kullanabilirsiniz.

API'yi şu URL'ye POST isteği göndererek test edebilirsiniz:

arduino
Kopyala
Düzenle
http://127.0.0.1:5000/tarama
Katkı Sağlama
Bu projeye katkı sağlamak için pull request gönderebilirsiniz.

Talha Burak Güneş-2320191066
