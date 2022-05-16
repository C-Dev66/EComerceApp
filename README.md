<img src="https://github.com/C-Dev66/EComerceApp/blob/main/screenshots/ECommerceReview.png" alt="ReviewPage"/>

# ECommerceApp
> This multi-platform application(Andoird, iOS, Web) hosts an online E-Commerece Store. The initial login screen prompts the user for a username & password. Once authenthicated the application is brought to the main page where all store products are displayed. Filter functionality is available on the top rigth corner with added animations.

---

### Table of Contents:

- [Description](#description)
- [Code Snippets](#code-snippets)
- [Summary](#summary)
- [Demo](#demo)




---

## Description

Application is built with Google's Flutter Framework. Sources for images and components are pulled from googles github. Purpose of this project is cover the basics of Material Design & Material Components in Flutter. 

**Material Design** is a system for building bold and beautiful digital products. By uniting style, branding, interaction, and motion under a consistent set of principles and components, product teams can realize their greatest design potential.

**Material Components for Flutter (MDC-Flutter)** unite design and engineering with a library of components that create a consistent user experience across apps and platforms. As the Material Design system evolves, these components are updated to ensure consistent pixel-perfect implementation, adhering to Google's front-end development standards. MDC is also available for Android, iOS, and the web.

1. **Material Components (MDC) Basics**
	- Create Login Screen - added text fields and buttons
2. **Material Structure & Layout**
	- Create Basic Flow Login Screen to Home Screen - Product view, top app bar w/ tittle & 3 buttons
3. **Material Theming with Color, Shape, Elevation, & Type**
	- Express a vibrant modern brand with styling
4. **Material Advanced Compomenets**
	- Create custom components using the MDC library to achieve a specefic look


---

## Code Snippets

> Setting up the application
```
// Make sure Flutter is set up

flutter doctor

// Clone from Github - Check out first Branch

git clone https://github.com/material-components/material-components-flutter-codelabs.git
cd material-components-flutter-codelabs/mdc_100_series

git checkout 101-starter
```


> Create Login Screen
```dart
class _LoginPageState extends State<LoginPage> {
  final _usernameController = TextEditingController();
  final _passwordController = TextEditingController();
  final _unfocusedColor = Colors.grey[600];
  final _usernameFocusNode = FocusNode();
  final _passwordFocusNode = FocusNode();
...
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: SafeArea(
        child: ListView(

...
            TextField(
              controller: _usernameController,
              decoration: InputDecoration(
                labelText: 'Username',
...
            ButtonBar(
              children: <Widget>[
                TextButton(
                    child: const Text('Cancel'),
                    style: ButtonStyle(
```

> Build grid/products & menu bar 
``` dart
class AsymmetricView extends StatelessWidget {
  final List<Product> products;

  const AsymmetricView({Key? key, required this.products}) : super(key: key);

  List<Widget> _buildColumns(BuildContext context) {
    if (products.isEmpty) {
      return <Container>[];
    }
...

    return List.generate(_listItemCount(products.length), (int index) {
      double width = .59 * MediaQuery.of(context).size.width;
      Widget column;
      if (index % 2 == 0) {
        /// Even cases
        int bottom = _evenCasesIndex(index);
        column = TwoProductCardColumn(
            bottom: products[bottom],
            top: products.length - 1 >= bottom + 1
                ? products[bottom + 1]
                : null);
        width += 32.0;
...
enum Category { all, accessories, clothing, home, }

class Product {
  const Product({
    required this.category,
    required this.id,
    required this.isFeatured,
    required this.name,
    required this.price,
  });

  final Category category;
  final int id;
  final bool isFeatured;
  final String name;
  final int price;

  String get assetName => '$id-0.jpg';
  String get assetPackage => 'shrine_images';

  @override
  String toString() => "$name (id=$id)";
}
...
```

> Apply theme to the application
```dart
import 'package:flutter/material.dart';

const KShrinePink50 = Color(0xFFFEEAE6);
const KShrinePink100 = Color.fromARGB(255, 251, 163, 41);
const KShrinePink300 = Color(0xFFFBB8AC);
const KShrinePink400 = Color(0xFFEAA4A4);

const KShrineBrown900 = Color.fromARGB(255, 0, 0, 0);

const KShrineErrorRed = Color(0xFFC5032B);

const KShrineSurfaceWhite = Color(0xFFFFFBFA);
const KShrineBackgroundWhite = Colors.white;

...
class CutCornersBorder extends OutlineInputBorder {
  const CutCornersBorder({
    BorderSide borderSide = const BorderSide(),
    BorderRadius borderRadius = const BorderRadius.all(Radius.circular(2.0)),
    this.cut = 7.0,
    double gapPadding = 2.0,
  }) : super(
            borderSide: borderSide,
            borderRadius: borderRadius,
            gapPadding: gapPadding);
...
```

> Apply animation to the menu
```dart
class _BackdropTitle extends AnimatedWidget {
  final void Function() onPress;
  final Widget frontTitle;
  final Widget backTitle;

  const _BackdropTitle({
    Key? key,
    required Animation<double> listenable,
    required this.onPress,
    required this.frontTitle,
    required this.backTitle,
  })  : _listenable = listenable,
        super(key: key, listenable: listenable);

  final Animation<double> _listenable;
...
        Stack(
          children: <Widget>[
            Opacity(
              opacity: CurvedAnimation(
                parent: ReverseAnimation(animation),
                curve: const Interval(0.5, 1.0),
              ).value,
              child: FractionalTranslation(
                translation: Tween<Offset>(
                  begin: Offset.zero,
                  end: const Offset(0.5, 0.0),
                ).evaluate(animation),
                child: Semantics(
                    label: 'hide categories menu',
                    child: ExcludeSemantics(child: backTitle)),
...
```

---

## Summary

Awesome introduction to Firebase, Cloud Firestore, & Security Rules. Really enjoyed this project and will seek to build more applications with their native database service. All around great experience, the future is bright for Flutter. Glad to be able to partaken in this revolutinary stack. 🤩🫶

For more information refer to the official documentation.

- [Firebase Documentation](https://firebase.google.com/docs)
- [Flutterfire](https://firebase.google.com/docs/flutter/setup?platform=ios)
- [Google's awesome Flutter Youtube channel, Lots of great content here](https://www.youtube.com/channel/UCwXdFgeE9KYzlDdR7TG9cMw)

---

## Demo
![HomePage Gif](https://github.com/C-Dev66/EComerceApp/blob/main/screenshots/ECommerceDemo.gif)

