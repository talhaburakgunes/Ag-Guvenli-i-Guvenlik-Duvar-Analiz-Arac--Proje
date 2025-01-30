# Ağ Güvenliği ve Güvenlik Duvarı Analiz Aracı API

Bu proje, bir güvenlik duvarının yapılandırmasını analiz etmek, kural setini incelemek, bypass tekniklerini tespit etmek ve güvenlik duvarı yapılandırma hatalarını kontrol etmek amacıyla geliştirilmiş bir API sunmaktadır. Kullanıcılar, belirli bir güvenlik duvarı yapılandırmasını API’ye gönderip analiz sonuçlarını alabilir.

## Ana Özellikler
- **Kural Seti Analizi**: Güvenlik duvarı kural setini analiz eder, açık veya yanlış yapılandırılmış kuralları tespit eder.
- **Bypass Teknik Tespiti**: Güvenlik duvarının bypass edilip edilemeyeceğini test eder.
- **Yapılandırma Kontrolü**: Yapılandırma hatalarını tespit eder ve en iyi güvenlik uygulamalarıyla uyumlu olup olmadığını kontrol eder.

## Kurulum ve Çalıştırma

1. **Python Yüklemesi**: Python 3.6+ sürümü gereklidir.
   
2. **Gerekli Kütüphanelerin Yüklenmesi**:
   Proje dosyasını indirip bir dizine kaydettikten sonra, gerekli kütüphaneleri yüklemek için terminalde şu komutu çalıştırabilirsiniz:
   ```bash
   pip install -r requirements.txt
