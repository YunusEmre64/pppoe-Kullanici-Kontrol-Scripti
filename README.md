# MikroTik PPP Aktif Kullanıcı Takibi ve Telegram Uyarı Sistemi

Bu script, MikroTik RouterOS üzerinde ether1 arayüzünden bağlanan PPP kullanıcılarının aktifliğini kontrol eder. Eğer ether1 üzerinden hiçbir aktif PPP kullanıcısı yoksa, sistem yöneticisini Telegram üzerinden anında uyarır.

# Ne Yapar?

Aktif PPP kullanıcılarını kontrol eder.

Bağlantı ether1 arayüzü üzerinden yapılmamışsa, uyarı üretir.

Belirtilen Telegram bot aracılığıyla tanımlı bir kullanıcıya mesaj gönderir.

# Nasıl Kurulur

RouterOS arayüzüne giriş yapın (Winbox veya WebFig ile).

Sol menüden System > Scripts kısmına girin.

+ (Add New) butonuna tıklayarak yeni bir script oluşturun.

Script özelliklerini şu şekilde doldurun:

Name: pppoeMonitor

Source: pppoeMonitor deki kodları girin

Policy: read, write, policy, test (Telegram gönderimi için read ve test genellikle yeterlidir, hata alırsanız write ve policy de ekleyin)

Script’i kaydedin.

# Script'in otomatik çalışmasını istiyorsanız:

System > Scheduler bölümüne gidin

Yeni bir zamanlayıcı (+) ekleyin:

Name: pppoeCheck

Interval: 00:05:00 (istediğiniz sıklığa göre ayarlayın)

On Event:
/system script run pppoeMonitor
