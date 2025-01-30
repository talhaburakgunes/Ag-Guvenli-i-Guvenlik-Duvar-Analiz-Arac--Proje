# Güvenlik Duvarı Analiz Aracı API

Bu API, hedef IP adresi üzerinden port tarama, güvenlik bypass tekniklerinin tespiti ve yapılandırma kontrolü sağlamak amacıyla geliştirilmiştir. Kullanıcılar, belirli port aralıklarında taramalar yaparak güvenlik duvarı zafiyetlerini tespit edebilirler.

## Projenin Amacı

Güvenlik duvarı analiz aracı, ağ güvenliğini test etmek için kullanılabilir. Bu API, beyaz şapka hacker'lar ve güvenlik uzmanları tarafından, ağdaki potansiyel zafiyetlerin belirlenmesi amacıyla kullanılmak üzere tasarlanmıştır.

---

## Kullanım

### API Endpoint
- **POST /analiz**: Bu endpoint, verilen hedef IP adresi üzerinde port taraması ve güvenlik duvarı bypass tekniklerinin tespiti işlemini gerçekleştirir.

### Gerekli Parametreler

#### Zorunlu Parametreler
Aşağıdaki parametreler isteğin içinde zorunlu olarak gönderilmelidir.

```json
{
    "hedef_ip": "192.168.1.100",
    "port_araligi": "80-443"
}
hedef_ip (str): Tarama yapılacak hedef IP adresi.
port_araligi (str): Tarama yapılacak port aralığı. Örneğin: "80-443".
Opsiyonel Parametreler
Aşağıdaki parametreler opsiyoneldir. Varsayılan değerler kullanılarak işlem yapılabilir.

json
Kopyala
Düzenle
{
    "kural_veritabani": "IETF",
    "ozelleştirilmis_modul": false,
    "detay_seviyesi": "orta"
}
kural_veritabani (str, opsiyonel): Kullanılacak kural seti veritabanı. Varsayılan: "IETF".
Örnek değerler: "IETF", "RFC", vb.
ozelleştirilmis_modul (bool, opsiyonel): Özelleştirilmiş bir modül kullanılıp kullanılmayacağını belirtir. Varsayılan: false.
detay_seviyesi (str, opsiyonel): Tarama detay seviyesi. Varsayılan: "orta".
Seçenekler: "düşük", "orta", "yüksek".
Örnek İstek
API'yi kullanmak için, aşağıdaki gibi bir POST isteği gönderebilirsiniz.

json
Kopyala
Düzenle
POST /analiz
{
    "hedef_ip": "192.168.1.100",
    "port_araligi": "80-443",
    "kural_veritabani": "IETF",
    "ozelleştirilmis_modul": false,
    "detay_seviyesi": "yüksek"
}
Cevap
API başarılı bir şekilde çalıştıktan sonra aşağıdaki gibi bir cevap döndürür:

json
Kopyala
Düzenle
{
    "sonuç": {
        "durum": "başarılı",
        "veri": {
            "ip_adresi": "192.168.1.100",
            "portlar": [
                {"port_numarasi": 80, "port_durumu": "açık"},
                {"port_numarasi": 443, "port_durumu": "kapalı"}
            ],
            "bypass_teknikleri": [
                {
                    "teknik_adi": "TCP FIN Scan",
                    "risk_puanı": "yüksek",
                    "detaylar": "Bu teknik, firewall güvenlik önlemlerini atlatabilir."
                }
            ],
            "yapilandirma_uyarilari": [
                {
                    "uyari_mesaji": "Açık portlar tespit edildi. Güvenlik riski oluşturabilir.",
                    "kritik_seviye": "yüksek"
                }
            ]
        },
        "hata_mesajı": ""
    }
}
Gereksinimler
Bu API'yi kullanmak için aşağıdaki araçlara ihtiyacınız olacak:

Python 3.6+
Flask (Web framework)
Gerekli Python kütüphanelerini yüklemek için şu komutu çalıştırın:

bash
Kopyala
Düzenle
pip install flask
Uygulama Başlatma
Uygulamayı başlatmak için, proje dosyasını indirip, app.py dosyasını çalıştırarak Flask sunucusunu başlatabilirsiniz.

bash
Kopyala
Düzenle
python app.py
Uygulama başlatıldıktan sonra şu URL üzerinden API'yi test edebilirsiniz:

arduino
Kopyala
Düzenle
http://127.0.0.1:5000/analiz
API başarılı bir şekilde çalıştığında, yukarıda verilen JSON formatında sonuç alacaksınız.

Önemli Not: Bu API yalnızca izinli testler ve etik hacker'lar tarafından kullanılmalıdır. Gerçek sistemlere zarar vermemek için yalnızca sahip olduğunuz ağlarda testler yapınız.
