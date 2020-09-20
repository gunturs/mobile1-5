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




You can use the [editor on GitHub](https://github.com/gunturs/mobile1-5/edit/gh-pages/index.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/gunturs/mobile1-5/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
