# Blahatí CrArtsland - Flutter Web Architecture & Migration Guide

## 1. Executive Summary & Suitability
Transitioning **Blahatí CrArtsland** to **Flutter Web** allows you to maintain a **single unified codebase (Dart)** that deploys seamlessly across:
- **Web** (Desktop browsers, tablets, mobile browsers with responsive layout)
- **Mobile Apps** (Native iOS & Android apps for App Store & Google Play with zero code rewrite)
- **Admin Desktop App** (Optional native Windows/macOS builds for studio operations)

---

## 2. Flutter Project Architecture & Directory Structure

Recommended Clean Feature-First Architecture:

```
blahati_crartsland/
├── lib/
│   ├── main.dart                          # App entry point, MaterialApp.router, theme setup
│   ├── core/
│   │   ├── theme/                         # AppTheme, Colors, Typography (Plus Jakarta Sans)
│   │   │   ├── app_colors.dart            # #4A6B53 (Forest Green), #D4AF37 (Gold), #FFF8F6 (Cream)
│   │   │   └── app_typography.dart        # GoogleFonts.plusJakartaSans()
│   │   ├── routing/                       # GoRouter configuration (Web URLs & deep links)
│   │   │   └── app_router.dart
│   │   ├── constants/                     # Currency (₱), Asset paths, API endpoints
│   │   └── utils/                         # ResponsiveBreakpoints (Mobile < 600, Tablet < 1024, Desktop >= 1024)
│   ├── features/
│   │   ├── auth/                          # Login, Register, PH mobile auth (+63)
│   │   │   ├── presentation/
│   │   │   └── data/
│   │   ├── storefront/                    # Catalog, Banner carousel, Categories, Supply grid
│   │   │   ├── presentation/
│   │   │   │   ├── screens/storefront_screen.dart
│   │   │   │   └── widgets/product_card.dart, banner_slider.dart
│   │   │   └── data/
│   │   ├── cart_checkout/                 # Cart list, Philippine address form, GCash / J&T COD
│   │   │   ├── presentation/
│   │   │   │   ├── screens/cart_checkout_screen.dart
│   │   │   │   └── widgets/order_summary_card.dart, payment_method_selector.dart
│   │   │   └── state/cart_provider.dart
│   │   └── admin/                         # Studio Inventory & J&T Fulfillment
│   │       ├── inventory/
│   │       │   └── screens/admin_inventory_screen.dart # Inline price edit, stock steppers
│   │       └── fulfillment/
│   │           └── screens/admin_fulfillment_screen.dart # Dispatch health, Kuya Arnel pickup, waybills
│   └── shared/
│       ├── widgets/                       # ResponsiveScaffold, CustomAppBar, BadgeIcon
│       └── models/                        # Product, Order, Address, Courier
```

---

## 3. Flutter Design System & Theme Configuration (`AppTheme`)

```dart
import 'package:flutter/material.dart';
import 'package:google_fonts/google_fonts.dart';

class BlahatiTheme {
  // Brand Color Palette
  static const Color primaryGreen = Color(0xFF4A6B53);
  static const Color brandGold = Color(0xFFD4AF37);
  static const Color surfaceCream = Color(0xFFFFF8F6);
  static const Color surfaceContainerLow = Color(0xFFFFF1ED);
  static const Color charcoalDark = Color(0xFF1C1B1F);
  static const Color jntRed = Color(0xFFE31B23);
  static const Color gcashBlue = Color(0xFF007DFE);

  static ThemeData lightTheme = ThemeData(
    useMaterial3: true,
    scaffoldBackgroundColor: surfaceCream,
    colorScheme: ColorScheme.fromSeed(
      seedColor: primaryGreen,
      primary: primaryGreen,
      secondary: brandGold,
      surface: surfaceCream,
      onSurface: charcoalDark,
    ),
    // Universal Clean Sans-Serif Typography
    textTheme: GoogleFonts.plusJakartaSansTextTheme().copyWith(
      displayLarge: GoogleFonts.plusJakartaSans(
        fontWeight: FontWeight.bold,
        color: charcoalDark,
      ),
      titleLarge: GoogleFonts.plusJakartaSans(
        fontWeight: FontWeight.w640,
        color: charcoalDark,
      ),
      bodyLarge: GoogleFonts.plusJakartaSans(
        color: charcoalDark,
      ),
    ),
    appBarTheme: const AppBarTheme(
      backgroundColor: surfaceCream,
      elevation: 0,
      centerTitle: false,
    ),
  );
}
```

---

## 4. Responsive Layout Strategy for Flutter Web

Use Flutter's `LayoutBuilder` or package `responsive_framework` to achieve identical responsiveness to the Tailwind `md:` and `lg:` breakpoints:

```dart
class ResponsiveLayout extends StatelessWidget {
  final Widget mobile;
  final Widget? tablet;
  final Widget desktop;

  const ResponsiveLayout({
    super.key,
    required this.mobile,
    this.tablet,
    required this.desktop,
  });

  static bool isMobile(BuildContext context) =>
      MediaQuery.of(context).size.width < 768;

  static bool isTablet(BuildContext context) =>
      MediaQuery.of(context).size.width >= 768 &&
      MediaQuery.of(context).size.width < 1100;

  static bool isDesktop(BuildContext context) =>
      MediaQuery.of(context).size.width >= 1100;

  @override
  Widget build(BuildContext context) {
    final width = MediaQuery.of(context).size.width;
    if (width >= 1100) return desktop;
    if (width >= 768) return tablet ?? desktop;
    return mobile;
  }
}
```

### Grid Scaling (Products Supply Grid):
- **Mobile:** `SliverGridDelegateWithFixedCrossAxisCount(crossAxisCount: 2, childAspectRatio: 0.75)`
- **Tablet:** `crossAxisCount: 3`
- **Desktop:** `crossAxisCount: 4` (with constrained max width container `Center(child: ConstrainedBox(constraints: BoxConstraints(maxWidth: 1280), child: ...))`)

---

## 5. Screen-by-Screen Flutter Widget Mapping

| Web Screen (Current HTML/Tailwind) | Flutter Widget Architecture |
|---|---|
| **Storefront & Catalog** | `CustomScrollView` + `SliverAppBar` (Desktop nav bar vs Mobile drawer) + `SliverToBoxAdapter` (Promotional Hero Banner) + `SliverGrid` (Products) |
| **Cart & Checkout** | `ResponsiveLayout`: Desktop split `Row([Expanded(flex: 7, child: CartItemsAndAddress()), Expanded(flex: 4, child: StickySummary())])` vs Mobile `Column` + bottom docked checkout sheet |
| **Admin Product Management** | `GridView.builder` with `TextFormField` (price with direct onChanged debounce), `IconButton` stepper for stock quantity, and `Switch` for live storefront visibility |
| **Admin Orders & J&T Fulfillment** | `Wrap` / `Row` for KPIs + J&T Dispatch Banner (`Card` with `Kuya Arnel` contact button via `url_launcher`) + `ListView.builder` of expandable fulfillment order cards |

---

## 6. Recommended Flutter Web Packages & Integrations

1. **State Management:**
   - `flutter_riverpod` or `bloc` (clean state isolation for Cart, Orders, Admin inventory)
2. **Web Routing & SEO URLs:**
   - `go_router` (enables clean URLs like `/store`, `/cart`, `/checkout`, `/admin/inventory`, `/admin/orders`)
3. **Typography & Icons:**
   - `google_fonts` (Plus Jakarta Sans)
   - `material_symbols_icons` (Google Material Symbols matching current design)
4. **Backend & Database:**
   - `supabase_flutter` or `firebase_core` (Real-time DB, Auth, and Storage for craft images)
5. **Philippine Payments Integration (GCash, Cards):**
   - **PayMongo / Xendit Webhooks**: Trigger payment intent via REST API, launch GCash payment redirect or QR modal using `url_launcher` on Web or in-app webview on mobile.
6. **Logistics & Printing (J&T Express):**
   - J&T Express Open API (REST client using `dio`)
   - `printing` / `pdf` package for direct browser printing of J&T Waybills (`JT90412849PH`) and Manifest sheets.
7. **Image Caching & Delivery:**
   - `cached_network_image` with Web canvas renderer / HTML renderer optimization.

---

## 7. Flutter Web Production Optimization Tips
- **Renderer Selection:** Use `flutter build web --web-renderer canvaskit` for smooth animations and graphics rendering, or `auto` for fast mobile browser fallback.
- **Fast First Paint:** Add a clean HTML/CSS splash loading screen matching `#FFF8F6` with your gold emblem monogram while Dart WebAssembly/JS initializes.
- **PWA Capabilities:** Enable `manifest.json` so craft studio staff can install the Admin Panel as a desktop/mobile Progressive Web App directly from Chrome/Safari.
