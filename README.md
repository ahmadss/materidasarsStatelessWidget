# materidasarsStatelessWidget

Stateless Widget
Jika kita melihat sebuah tampilan antar muka pengguna (user interface), tampilan tersebut terdiri dari berbagai jenis widget-widget, tetapi tidak semua tampilan harus bisa berinteraksi dengan user, misalnya sebuah Text, tampilan tersebut hanya menampilkan informasi, tetapi tidak untuk berinteraksi seperti user melakukan tap terhadap text tersebut. Pada saat kita membuat aplikasi flutter, maka kita akan mendapatkan kode bawaan (default) yang dihasilkan oleh flutter tersebut, ada beberapa widget pada aplikasi tersebut, tetapi hanya satu saja widget yang berinteraksi dengan user, yaitu tombol counter dimana user bisa melakukan click (tap) pada tombol tersebut, jadi dapat kita pahami widget yang lainnya hanya digunakan untuk menampilkan sesuatu, bukan untuk berinteraksi dengan user, widget yang tidak berinteraksi dengan user disebut Stateless Widget. Berikut ini adalah kode minimal yang diperlukan untuk membuat Stateless Widget:

<p>
class ExampleWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return "kode beberapa widget disini";
  }
}
</p>

Stateless widget diciptakan oleh parent widget didalam metode "build"nya. Stateless Widget diberikan informasi yang diperlukan pada saat diciptakan. Stateless widget menerima informasi berupa argumen dari parent widget didalam metode "build"nya, dimana informasi tersebut disimpan didalam variabel bersifat yang final.

Stateless widget menghasilkan (generate) UI didalam metode "build"nya, yang mana hasilnya dirender oleh Flutter. Stateless widget juga dapat membuat UI menggunakan nilai dari variabel anggotanya (member variable), atau dari sumber lainnya. Stateless widget tidak bisa memaksa dirinya sendiri untuk melakukan rendering ulang.

Ketika Stateless widget diminta untuk membuat (build) UI-nya, stateless widget dapat menggunakan nilai dari variabel membernya untuk merender UI, nilai ini tidak berubah, nilai tersebut di berikan melalui konstruktor. Perhatikan contoh berikut:

class Car extends StatelessWidget {
  final String make;
  final String model;
  
  Car(this.make, this.model);
  
  @override
  Widget build(BuildContext context) {
    return Center(
      child: Column(children: <Widget>[
        Text(make),
        Text(model),
      ],
    );
  }
}

Sewaktu membuat UI, Stateless Widget bisa juga mengambil dari sumber lainnya, perhatikan contoh berikut:
class Car extends StatelessWidget {
  final String make;
  final String model;
  
  Car(this.make, this.model);
  
  @override
  Widget build(BuildContext context) {
    return Center(
      child: Column(children: <Widget>[
        Text(make, style: Theme.of(context).textTheme.display1),
        Text(model, style: Theme.of(context).textTheme.display1),
      ],
    );
  }
}
  
  Pada contoh program diatas, nilai pada style kita ambil dari Theme, ini adalah kelas yang telah disediakan oleh flutter untuk menangani Tema pada aplikasi kita, hal yang perlu kita ingat adalah kapan metode "build" dieksekusi? metode "build" dieksekusi pada saat pertama kali widget di masukkan kedalam widget tree, kemudian pada saat parent widget berubah, kemudian pada saat nilai dari sumber lainnya berubah. Berikut adalah contoh aplikasi Stateless Widget.

Langkah 1
Buat project baru, lihat disini

Langkah 2
Buka file main.dart di folder lib/, dan hapus seluruh isinya, gantilah dengan kode berikut:
import 'package:flutter/material.dart';

void main() => runApp(AppStateless());

class AppStateless extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(primarySwatch: Colors.blue),
      home: AppHome(title: 'Sateless App'),
    );
  }
}

class AppHome extends StatelessWidget {
  AppHome({Key key, this.title}) : super(key: key);

  final String title;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(this.title),
      ),
      body: Column(
        children: <Widget>[
          Text('Belajar Stateless App'),
          Text('Ini adalah widget Text')
        ],
      ),
    );
  }
}


Langkah 3
Jalankan emulator & programmnya, maka tampilannya adalah sebagai berikut:
![alt tag](https://1.bp.blogspot.com/-nlSHiS1kmss/XSRRgsph4XI/AAAAAAAAA7g/JanZvHLzvNAOWYFuJO3IdWejyg7FsFx0ACLcBGAs/s1600/run-appstateless.png)
