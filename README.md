# Flutter MDC-101 to MDC-104 Project

## Overview
This project is based on Google's Material Design Codelabs (MDC-101 to MDC-104) and follows Flutter best practices to create a **user-friendly shopping application**. The app implements a **clean UI**, **structured navigation**, and **modern design elements**.

## Features
- **Bottom Navigation Bar** for easy access to key sections.
- **Home, Categories, and Profile pages** with structured layout.
- **Material Design Components** for an improved user experience.
- **Custom UI elements**, including a backdrop, product cards, and category views.

## Installation
To run this project locally:

1. Clone the repository:
   ```sh
   git clone https://github.com/sterbenmzrt/mdc101-104-vispro.git
   ```
2. Navigate to the project directory:
   ```sh
   cd path project
   ```
3. Install dependencies:
   ```sh
   flutter pub get
   ```
4. Run the application:
   ```sh
   flutter run
   ```

> **Note:** This repository only contains the `lib/` directory of the Flutter project. If you want to use this project, copy and paste the `lib/` folder into an existing Flutter project or create a new one and replace its `lib/` directory with these files.

## File Structure
```
lib/
│── main.dart                 # Entry point of the application
│── app.dart                  # Manages bottom navigation and main layout
│── backdrop.dart             # UI component for backdrop functionality
│── category_menu_page.dart   # UI for category selection
│── colors.dart               # Centralized color theme
│── home.dart                 # Home screen implementation
│── login.dart                # Login screen UI
│
├── model/
│   ├── product.dart          # Product model definition
│   ├── products_repository.dart # Manages product data
│
├── supplemental/
│   ├── asymmetric_view.dart  # Custom view implementation
│   ├── cut_corners_border.dart # Custom border styling
│   ├── product_card.dart     # UI widget for product cards
│   ├── product_columns.dart  # Layout structure for products
```

## Code Explanation

### `main.dart` - Application Entry Point
The application starts execution from `main.dart`, which initializes the app and sets `HomePage` as the default screen.
```dart
void main() {
  runApp(const MyApp());
}
```

### `app.dart` - Navigation and Main Structure
Defines **BottomNavigationBar** for smooth user navigation across Home, Categories, and Profile pages.
```dart
BottomNavigationBar(
  items: const [
    BottomNavigationBarItem(icon: Icon(Icons.home), label: 'Home'),
    BottomNavigationBarItem(icon: Icon(Icons.category), label: 'Categories'),
    BottomNavigationBarItem(icon: Icon(Icons.person), label: 'Profile'),
  ],
  currentIndex: _selectedIndex,
  onTap: _onItemTapped,
)
```

### `home.dart`, `category_menu_page.dart`, `login.dart`
These files define the UI of various screens using `StatelessWidget`.
```dart
class HomeScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Center(
      child: Text('Welcome to the Home Page', style: TextStyle(fontSize: 18)),
    );
  }
}
```

### `backdrop.dart` - Backdrop Widget
Implements a **backdrop UI component**, allowing users to toggle between different views smoothly.
```dart
class Backdrop extends StatelessWidget {
  final Widget frontLayer;
  final Widget backLayer;
  const Backdrop({required this.frontLayer, required this.backLayer});

  @override
  Widget build(BuildContext context) {
    return Stack(
      children: [backLayer, frontLayer],
    );
  }
}
```

### `colors.dart` - Centralized Theme Management
Defines reusable color constants to maintain consistent theming.
```dart
const Color primaryColor = Colors.blue;
const Color accentColor = Colors.orange;
```

### `model/product.dart` - Product Model
Defines the **Product** class with `name`, `price`, and `imagePath`.
```dart
class Product {
  final String name;
  final double price;
  final String imagePath;

  Product({required this.name, required this.price, required this.imagePath});
}
```

### `model/products_repository.dart` - Product Repository
Stores and provides mock product data.
```dart
class ProductsRepository {
  static List<Product> loadProducts() {
    return [
      Product(name: 'Product 1', price: 29.99, imagePath: 'assets/images/product1.png'),
      Product(name: 'Product 2', price: 49.99, imagePath: 'assets/images/product2.png'),
    ];
  }
}
```

### `supplemental/*` - UI Components
- **`product_card.dart`**: Custom widget to display product details.
- **`asymmetric_view.dart`**: Implements an asymmetric grid layout.
- **`cut_corners_border.dart`**: Custom border styling for widgets.

Example from `product_card.dart`:
```dart
class ProductCard extends StatelessWidget {
  final Product product;
  const ProductCard({required this.product});

  @override
  Widget build(BuildContext context) {
    return Card(
      child: Column(
        children: [
          Image.asset(product.imagePath),
          Text(product.name),
          Text('\$${product.price.toString()}'),
        ],
      ),
    );
  }
}
```
## Contributing
Contributions are welcome! Please follow the standard GitHub workflow for submitting pull requests.

