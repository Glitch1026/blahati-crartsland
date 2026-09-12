# Blahatí CrArtsland - Developer Handover & Production Export Specification

## 1. Project Overview & Brand Assets
- **Business Name:** Blahatí CrArtsland (Arts & Crafts Accessories E-Commerce)
- **Target Market:** Philippines (PHP currency ₱, GCash, Cards, J&T Cash-on-Delivery)
- **Official Brand Logo:**
  - Golden Cursive Floral/Butterfly Monogram: `{{DATA:IMAGE:IMAGE_5}}`
- **Typography:**
  - Headings & UI Body: Modern Sans-Serif (`Plus Jakarta Sans`, `Inter`, system fallback `sans-serif`)
  - Icons: Google Material Symbols Outlined
- **Core Color Palette:**
  - Primary / Accent: Warm Artisan Forest Green (`#4A6B53` / `rgb(74, 107, 83)`)
  - Brand Gold: `#D4AF37` / `#C5A059`
  - Surface Background: Warm Cream Linen (`#FFF8F6` / `#FAF7F2`)
  - Text: High contrast charcoal / on-surface dark

---

## 2. Screen Inventory & Architecture
All screens are built with mobile-first responsive design (`Tailwind CSS`, responsive breakpoints `md:`, `lg:`):

1. **Storefront & Catalog** (`{{DATA:SCREEN:SCREEN_10}}`)
   - Adaptive top navigation bar (desktop horizontal links vs mobile drawer)
   - Hero banner with craft promotions & flash drops
   - Category filtering pills (Resin & Molds, Polymer Clay, Pottery Glaze, Tools)
   - Product supply grid (2 cols on mobile, 4 cols on desktop)
   - Quick Add-to-Cart with badge counters

2. **Cart & Checkout** (`{{DATA:SCREEN:SCREEN_7}}`)
   - Order items list with quantity steppers and subtotal calculations
   - Philippine delivery address block (Barangay, City, Province, ZIP)
   - Courier selection: **J&T Express** (Standard & Same-day dispatch)
   - Localized Payment Gateways:
     - **GCash** (Mobile wallet QR / redirect)
     - **J&T Cash on Delivery (COD)**
     - Credit / Debit Card (Visa, Mastercard)
   - Responsive two-column desktop summary layout & sticky mobile bottom action bar

3. **Sign In & Registration** (`{{DATA:SCREEN:SCREEN_9}}`)
   - Customer authentication with email/password and social login options
   - Philippine mobile number (+63) input validation

4. **Customer Profile & Delivery Addresses** (`{{DATA:SCREEN:SCREEN_8}}`)
   - Saved shipping destinations (Default home/studio address)
   - Order history status tracking

5. **Admin Panel - Product & Inventory Management** (`{{DATA:SCREEN:SCREEN_4}}`)
   - Real-time studio stats (Active Listings, Low Stock Alerts, Daily Sales)
   - Quick-edit product cards (inline price updates in ₱, stock level steppers, instant live toggle)
   - Filterable catalog by category and stock condition
   - "+ Add New Craft Item" drawer action

6. **Admin Orders & J&T Fulfillment** (`{{DATA:SCREEN:SCREEN_2}}`)
   - Dispatch health dashboard (To Ship/Pack, In Transit, Delivered & Remitted, RTS)
   - Scheduled J&T Express pickup card with rider contact info (`Kuya Arnel`)
   - Manifest generation and waybill batch printing
   - Detailed fulfillment item cards with J&T waybill codes (`JT90412849PH`) and GCash transaction reference numbers

---

## 3. Recommended Tech Stack for Production
- **Frontend:** Next.js (App Router), React, Tailwind CSS, Lucide-React / Material Symbols
- **Backend & Database:** Node.js / Next.js API routes with Supabase (PostgreSQL) or Prisma ORM
- **Payment Processing (Philippines):**
  - **PayMongo** or **Xendit Philippines** (handles GCash, Maya, GrabPay, Credit/Debit cards with webhooks)
- **Courier Logistics API:**
  - **J&T Express Philippines Open API** (Automated waybill creation, tracking webhooks, pickup dispatch requests)
- **Storage:** Supabase Storage / AWS S3 (for product photos and media)

---

## 4. Database Schema (Key Entities)

### `users`
- `id`: UUID (Primary Key)
- `email`: string
- `phone`: string (PH format `+639...`)
- `role`: enum (`customer`, `admin`)
- `created_at`: timestamp

### `addresses`
- `id`: UUID
- `user_id`: UUID (FK)
- `recipient_name`: string
- `phone`: string
- `street_barangay`: string
- `city`: string
- `province`: string
- `postal_code`: string
- `is_default`: boolean

### `products`
- `id`: UUID
- `title`: string
- `slug`: string
- `category`: string
- `description`: text
- `price`: decimal
- `stock_quantity`: integer
- `low_stock_threshold`: integer
- `is_active`: boolean
- `image_urls`: string[]

### `orders`
- `id`: UUID
- `order_number`: string (e.g. `BLH-8942`)
- `user_id`: UUID (FK)
- `shipping_address_id`: UUID (FK)
- `status`: enum (`pending_payment`, `to_pack`, `ready_for_handover`, `in_transit`, `delivered`, `cancelled`)
- `payment_method`: enum (`gcash`, `cod_jt`, `card`)
- `payment_reference`: string
- `shipping_carrier`: string (`J&T Express`)
- `waybill_number`: string (e.g. `JT90412849PH`)
- `subtotal`: decimal
- `shipping_fee`: decimal
- `total_amount`: decimal
- `created_at`: timestamp

---

## 5. How to Extract Source Code
Each screen contains clean, self-contained semantic HTML and responsive Tailwind CSS utility classes. You can copy the code directly from each screen for your Next.js/React components.
