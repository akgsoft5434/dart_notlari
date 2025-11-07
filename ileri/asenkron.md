# ⚙️ Dart'ta Asenkron Programlama

Dart dilinde **asenkron programlama**, uzun süren işlemleri (örneğin dosya okuma, API isteği, veritabanı erişimi gibi) **uygulamayı dondurmadan** gerçekleştirmek için kullanılır.

---

## 🔹 1. Neden Asenkron Programlama?

Normalde Dart kodu **tek iş parçacığında (single-threaded)** çalışır.  
Eğer uzun sürecek bir işlem (örneğin 5 saniyelik bekleme) yaparsan, bu süre boyunca uygulama **kilitlenir**.

```dart
void main() {
  print("İşlem başlıyor...");
  uzunIslem(); // 5 saniye süren işlem
  print("İşlem bitti!"); // Bu satır hemen çalışır ama işlem bitmeden olabilir
}

void uzunIslem() {
  Future.delayed(Duration(seconds: 5), () {
    print("Uzun işlem tamamlandı!");
  });
}
```

🟢 Çıktı:
```
İşlem başlıyor...
İşlem bitti!
Uzun işlem tamamlandı!
```
