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
    @override
    Widget build(BuildContext context) {
        return Scaffold(
            appBar: AppBar(
                title: Text('ExampleApp'),
            ),
            body: Container(
                child: NumberScreen(),
            )
        );
    }
}

class NumberScreen extends StatefulWidget {
  @override
  _NumberScreenState createState() => _NumberScreenState();
}

class _NumberScreenState extends State<NumberScreen> {
    int number = 10;

    @override
    Widget build(BuildContext context) {
        return Stack(
            children: <Widget>[
                Center(
                    child: Text(
                        this.number.toString(),
                        style: TextStyle(
                            fontSize: 30
                        ),
                    ),
                ),
                Positioned(
                    bottom: 50,
                    right: 50,
                    child: FloatingActionButton(
                        child: Icon(Icons.plus_one),
                        onPressed: () {
                            setState(() {
                                this.number += 1;
                            });
                        },
                    ),
                )
            ],
        );
    }
}

```
menuliskan class StatefulWidget diawai dengan Underscor ( _ ) Contoh:  _NumberScreenState
fungsi setState() yang akan bertugas untuk memberitahu widget bahwa ada object yang berubah pada State, sehingga akan melakukan build ulang pada Widget tersebut.
fungsi setState() tidak berlaku pada StetelessWidget
