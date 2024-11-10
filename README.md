# Proje4
## Bu GitHub'daki dördüncü projem.
#
Bu proje, AC şarj istasyon için RFID kart okuyucu sisteminin geliştirilmesine yöneliktir. Proje, bir RFID kart okuyucu ile AC şarj istasyonuna erişim kontrolü yapmayı amaçlar. MFRC522 RFID modülü ve STM32 mikrodenetleyici kullanılarak kart UID'si okunur ve belirli bloklara veri yazılır veya okunur.

Özellikler
RFID Kart Okuma: RFID kartlarının UID bilgileri okunur.
Güvenlik: Kartın güvenliğini sağlamak için sektör anahtarları (sector key) kullanılır.
SPI İletişimi: MFRC522 modülü ile SPI protokolü üzerinden haberleşme yapılır. (I2C ye çevrildi sonra, kütüphane güncellenerek.)
Veri Okuma ve Yazma: Karttan veri okuma ve kart üzerinde veri yazma işlemleri yapılır.
Kullanılan Donanım
STM32 Mikrodenetleyici: Ana işlemci olarak STM32 serisi kullanılır.
MFRC522 RFID Modülü: RFID kartların UID'sini okumak için MFRC522 modülü kullanılır.
SPI Arayüzü: MFRC522 ile mikrodenetleyici arasındaki iletişim SPI protokolü ile sağlanır.
UART İletişimi: Okunan kart bilgileri UART üzerinden seri port ile ekrana yazdırılır.
Donanım Bağlantıları
MFRC522 Kart Okuyucu:

SDA (SS): STM32 mikrodenetleyicisinin SPI SS pinine bağlanır.
SCK: SPI saat pinine bağlanır.
MISO: SPI MISO pinine bağlanır.
MOSI: SPI MOSI pinine bağlanır.
RST: Mikrodenetleyicinin GPIO pinlerinden birine bağlanır.
GND: GND'ye bağlanır.
VCC: 3.3V veya 5V'a bağlanır.
LED ve Buton:

LD2: LED ışığı çıkışı.
B1: Kart okutma butonu (isteğe bağlı).
Kullanım
Kart Okuma:
Proje çalışmaya başladığında, kartın UID'si okunduğunda, kartın ID'si UART üzerinden ekrana yazdırılır. Kartı okutmak için kart okuyucunun önüne yerleştirmeniz yeterlidir.

Kart Seçimi ve Yetkilendirme:
Kart başarıyla okunduğunda, belirli sektörler için yetkilendirme yapılır (sektor anahtarı kullanılır). Kartın verilerine erişim sağlanır.

Veri Okuma ve Yazma:
Kartın verileri okuyabilir veya yazabilirsiniz. Bu işlem, kartın seçilen bloğuna (block address) veri yazmayı ve okumayı içerir.

Yazılım
Projede kullanılan yazılım, STM32 için HAL kütüphanelerine dayanmaktadır ve MFRC522 RFID modülünün kullanımına yönelik özel fonksiyonlar içerir. Aşağıda kullanılan ana fonksiyonlar bulunmaktadır:

MFRC522_Init: RFID okuyucuyu başlatan fonksiyon.
MFRC522_Request: Kart varlığını kontrol eden fonksiyon.
MFRC522_Anticoll: Kartın UID'sini okuyan fonksiyon.
MFRC522_SelectTag: Okunan kartı seçen fonksiyon.
MFRC522_Auth: Kart için güvenlik yetkilendirmesini yapan fonksiyon.
MFRC522_Read: Karttan veri okuyan fonksiyon.
MFRC522_Write: Kart üzerine veri yazan fonksiyon.
Bağlantılar ve Donanım Kütüphaneleri
MFRC522 Kütüphanesi
STM32 HAL Kütüphanesi: STM32 mikrodenetleyicisi için donanım kütüphaneleri.
Kurulum
STM32 mikrodenetleyiciye uygun yazılım geliştirme ortamını (STM32CubeMX ve STM32CubeIDE) kurun.
Projeyi STM32CubeIDE veya uygun bir IDE ile açın.
Gerekli bağlantıları yapın ve MFRC522 modülünü SPI üzerinden mikrodenetleyiciye bağlayın.
Kodu mikrodenetleyiciye yükleyin.
Seri port üzerinden çıkışı izleyerek kart okuma ve veri yazma işlemlerini test edin.
Test
Kart okutma testi: Proje çalışırken bir RFID kartı okutun ve UID bilgilerini ekranda görmelisiniz.
Veri okuma ve yazma testi: Seçilen bloklardan veri okuma ve yazma işlemlerini doğrulayın.
