# Android Development Standarization with Kotlin 
Selamat datang di dokumentasi standard pemrograman Kotlin untuk Android! Dokumentasi ini akan memberikan panduan tentang cara mengembangkan aplikasi Android dengan bahasa Kotlin.
## Pendahuluan
### Tujuan 
Dokumentasi ini dibuat untuk menghadirkan pedoman dan panduan standar dalam mengembangkan aplikasi Android dengan Kotlin. Tujuan utamanya adalah meningkatkan konsistensi, kualitas, dan efisiensi pengembangan perangkat lunak.
### Ruang Lingkup
Dokumentasi ini mencakup praktik terbaik dalam penggunaan bahasa Kotlin untuk Android, struktur proyek, panduan penulisan kode, pengujian, serta alur kerja kolaborasi.

### Referensi
- [Dokumentasi Resmi Kotlin](https://kotlinlang.org/docs/home.html)
- [Android Kotlin Style Guide](https://developer.android.com/kotlin/style-guide)
- [Android Development Guide](https://developer.android.com/kotlin)
- [Struktur Project Kotlin Android](https://kotlinlang.org/docs/multiplatform-mobile-understand-project-structure.html#root-project)

### Arsitektur & Struktur Project
- Menggunakan arsitektur MVVM (Model View ViewModel) untuk memisahkan logic, view dan data
```
NamaAplikasi
  ├──.gradle
  ├──app
  │ ├──src
  │ │ ├──main
  │ │ │ ├──java
  │ │ │ │  ├── model
  │ │ │ │  ├── view
  │ │ │ │  ├── viewModel
  │ │ ├──androidTest
  │ ├──build.gradle
  ├──README.md
```


## Pedoman Penulisan Kode
### Penamaan
- Gunakan camelCase untuk nama variabel dan fungsi.
```kotlin
fun read(
    b: ByteArray,
    off: Int = 0,
    len: Int = b.size,
) { /*...*/ }
```
- Gunakan PascalCase untuk nama kelas dan interface.
```kotlin
class UserDetailActivity : AppCompatActivity() { }
```
- Nama harus deskriptif dan jelas
```kotlin
companion object{
    const val MAX_COUNT = 100
}
```
### Komentar Kode
- Komentar harus informatif dan membantu, bukan hanya mengulang kode.
- Gunakan // untuk komentar satu baris dan /* ... */ untuk komentar multi-baris.

## Panduan Pengujian
### Unit Testing
- Unit testing harus dilakukan untuk setiap fungsi atau metode yang ditulis.
- Gunakan library [JUnit](https://junit.org/junit5/) untuk unit test dan [Espresso](https://developer.android.com/training/testing/espresso) untuk UI testing

## Alur Kerja Kolaborasi
### Version Control
- Gunakan Git sebagai sistem kontrol versi utama.

## Dependensi & Manajemen Pustaka
### Gradle
- Gunakan [Gradle](https://gradle.org/) sebagai alat manajemen dependensi utama.
- Pastikan untuk selalu memperbarui semua dependensi ke versi stabil terbaru.
- Hindari penggunaan pustaka yang sudah tidak didukung atau jarang diperbarui.

## Keselamatan & Keamanan
### Penyimpanan Data Lokal
- Gunakan `SharedPreferences` dengan mode `MODE_PRIVATE` untuk menyimpan data sederhana.
```kotlin
val sharedPref = context.getSharedPreferences("myPrefs", Context.MODE_PRIVATE)
val editor = sharedPref.edit()
editor.putString("key", "value")
editor.apply()
```

### Enkripsi Data
- Gunakan `EncryptedSharedPreferences` untuk menyimpan data sensitif.
```kotlin
val masterKeyAlias = MasterKeys.getOrCreate(MasterKeys.AES256_GCM_SPEC)
val sharedPreferences = EncryptedSharedPreferences.create(
    "secret_shared_prefs",
    masterKeyAlias,
    context,
    EncryptedSharedPreferences.PrefKeyEncryptionScheme.AES256_SIV,
    EncryptedSharedPreferences.PrefValueEncryptionScheme.AES256_GCM
)
```

## Responsif & Adaptabilitas
### Mendukung Multi Bahasa
- Gunakan `strings.xml` untuk mendefinisikan string dan buat variasi berdasarkan bahasa.
```xml
<!-- dalam res/values/strings.xml -->
<string name="welcome_message">Welcome</string>

<!-- dalam res/values-id/strings.xml -->
<string name="welcome_message">Selamat datang</string>
```

## Aksesibilitas
### Content Descriptions
- Tambahkan `contentDescription` untuk elemen UI yang interaktif.
```kotlin
val button = findViewById<Button>(R.id.my_button)
button.contentDescription = "Tombol untuk melakukan sesuatu"
```

## Optimalisasi Kinerja
### Menggunakan View Binding
- Hindari `findViewById` dengan menggunakan View Binding.
```kotlin
val binding = ActivityMainBinding.inflate(layoutInflater)
setContentView(binding.root)
binding.myButton.text = "Tekan Saya"
```

## Proses Review
### Menggunakan Linter
- Gunakan `ktlint` atau `detekt` untuk memeriksa kualitas kode Kotlin.
```bash
$ ./gradlew ktlintCheck
```

## Integrasi & Pengiriman Terus Menerus (CI/CD)
### Otomatisasi Build dengan Gradle
- Gunakan task Gradle untuk otomatisasi build.
```bash
$ ./gradlew assembleDebug
```

---
