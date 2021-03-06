# flutter_route
 
```dart
environment:
  sdk: ">=2.12.0 <3.0.0"
```

- config/app_router.dart
```dart
import 'package:flutter/cupertino.dart';
import 'package:flutter/material.dart';
import 'package:flutter_ecommerce_v1/ui/screen.dart';

class AppRouter {
  static Route onGenerateRoute(RouteSettings settings) {
    switch (settings.name) {
      case "/":
        return HomeScreen.route();
      case HomeScreen.routeName:
        return HomeScreen.route();
      default:
        return _errorRoute();
    }
  }

  static Route _errorRoute() {
    return MaterialPageRoute(
      settings: RouteSettings(name: "/error"),
      builder: (_) => Scaffold(
        appBar: AppBar(
          title: Text("Error"),
        ),
      ),
    );
  }
}
```

- ui/screen.dart
```dart
export 'home/home_screen.dart';
export 'cart/cart_screen.dart';
```

- main.dart
```dart
import 'ui/screen.dart';

void main() {
  runApp(MyApp());
}

class MyApp extends StatelessWidget {
  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
        visualDensity: VisualDensity.adaptivePlatformDensity,
      ),
      onGenerateRoute: AppRouter.onGenerateRoute,
      initialRoute: HomeScreen.routeName,
    );
  }
}
```

- ui/home/home_screen.dart
```dart
import 'package:flutter/material.dart';
import 'package:flutter_ecommerce_v1/widget/witgets.dart';

class HomeScreen extends StatelessWidget {
  HomeScreen({Key? key, required this.title}) : super(key: key);

  final String title;
  static const String routeName = "/";

  static Route route() {
    return MaterialPageRoute(
      settings: RouteSettings(name: routeName),
      builder: (_) => HomeScreen(title: "Flutter Demo Home Page"),
    );
  }

  ...
}
```

---

- PutExtra
```dart
Navigator.pushNamed(context, ProductScreen.routeName, arguments: product);
```
```dart
static Route onGenerateRoute(RouteSettings settings) {
  switch (settings.name) {
    ...
    case ProductScreen.routeName:
      return ProductScreen.route(data: settings.arguments as Product);
     ...
  }
}
```
```dart
class ProductScreen extends StatelessWidget {
  final Product data;
  static const String routeName = "/product";

  const ProductScreen({required this.data});

  static Route route({required Product data}) {
    return MaterialPageRoute(
      settings: RouteSettings(name: routeName),
      builder: (_) => ProductScreen(data: data),
    );
  }
 
  ...
}
```

---

```
Copyright 2021 M. Fadli Zein
```
