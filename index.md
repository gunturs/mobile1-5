# STATELESSWIDGET dan STATEFULLWIDGET

Sebelumnya kita harus memahami bahwa dalam membuat interface dengan Flutter, semua komponen yang kita pakai disebut dengan Widget, Widget memiliki dua tipe yaitu Stateful dan Stateless.

>## Stateless Widget

Merupakan widget yang di-build hanya dengan konfigurasi yang telah diinisiasi sejak awal. Jadi Stateless Widget adalah Widget yang tidak akan pernah berubah. Contoh dan tugas yang sudah kita gunakan pada pertemuan 1-4 merupakan penereapan dari Stateless Widget 

```dart
class MyApp extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            appBar: AppBar(
                title: Text('ExampleApp'),
            ),
            body: Center(
                child: Text(
                    '10',
                    style: TextStyle(
                        fontSize: 30
                    ),
                ),
            )
        );
    }
}
```
Pada program diatas hasilnya menampilkan angka 10,  dan nilai 10 itu tidak akan bisa dirubah karena menggunkan stateless Widget

>## Stateful Widget

Stateful Widget merupakan widget yang dinamis atau dapat berubah. Berbanding terbalik dengan stateless, stateful widget dapat mengupdate tampilan, merubah warna, menambah jumlah baris dll. 
Perhatikan contoh berikut, kita akan membuat program pada contoh diatas menjadi dinamis sehingga dapat meribah nilai angka ketika kita klick sesuatu dalam contoh ini sebuah tombol floating.

```dart
class MyApp extends StatelessWidget {
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: Text('Contoh Statefull Widget'),
        ),
        body: Angka(),
      ),
    );
  }
}

class Angka extends StatefulWidget {
  _Angka createState() => _Angka();
}

class _Angka extends State<Angka> {
  int _number = 10;
  
  //Hitung Tambah
  
  void _tambah(){
    setState((){
      _number++;
    });
  }
  
  //Hitung kurang
  
  void _kurang(){
    setState((){
      _number--;
    });
  }
    

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(
        child: new Stack(
          children: <Widget>[
            new Center(
              child: new Text(
                '$_number',
                style: TextStyle(fontSize: 30),
              ),
            ),
            
            //Program untuk tombol tembah
            new Positioned(
              bottom:100,
              right: 10,
              child: new FloatingActionButton(
                child: Icon(Icons.add),
                backgroundColor: Colors.green,
                onPressed: _tambah,
              ),
            ),
            //Program untuk Tombol Kurang
            new Positioned(
              bottom:40,
              right: 10,
              child: new FloatingActionButton(
                child: Icon(Icons.remove),
                backgroundColor: Colors.red,
                onPressed: _kurang,
              ),
            ),
            
          ],
        ),
      ),
    );
  }
}


```
menuliskan class StatefulWidget diawai dengan Underscor ( _ ) Contoh:  _Angka
fungsi setState() yang akan bertugas untuk memberitahu widget bahwa ada object yang berubah pada State, sehingga akan melakukan build ulang pada Widget tersebut.
fungsi setState() tidak berlaku pada StetelessWidget
