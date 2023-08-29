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


