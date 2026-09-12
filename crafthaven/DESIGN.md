---
name: CraftHaven
colors:
  surface: '#fff8f6'
  surface-dim: '#e8d6d1'
  surface-bright: '#fff8f6'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#fff1ed'
  surface-container: '#fdeae5'
  surface-container-high: '#f7e4df'
  surface-container-highest: '#f1dfd9'
  on-surface: '#231917'
  on-surface-variant: '#424842'
  inverse-surface: '#392e2b'
  inverse-on-surface: '#ffede8'
  outline: '#727972'
  outline-variant: '#c2c8c0'
  surface-tint: '#45664e'
  primary: '#32533c'
  on-primary: '#ffffff'
  primary-container: '#4a6b53'
  on-primary-container: '#c5eacc'
  inverse-primary: '#abcfb2'
  secondary: '#97472e'
  on-secondary: '#ffffff'
  secondary-container: '#fe997a'
  on-secondary-container: '#772f18'
  tertiary: '#713e30'
  on-tertiary: '#ffffff'
  tertiary-container: '#8d5546'
  on-tertiary-container: '#ffd8cf'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#c7ecce'
  primary-fixed-dim: '#abcfb2'
  on-primary-fixed: '#01210f'
  on-primary-fixed-variant: '#2e4e37'
  secondary-fixed: '#ffdbd0'
  secondary-fixed-dim: '#ffb59f'
  on-secondary-fixed: '#3a0a00'
  on-secondary-fixed-variant: '#793019'
  tertiary-fixed: '#ffdbd1'
  tertiary-fixed-dim: '#fdb5a3'
  on-tertiary-fixed: '#350f06'
  on-tertiary-fixed-variant: '#6b392c'
  background: '#fff8f6'
  on-background: '#231917'
  surface-variant: '#f1dfd9'
typography:
  display-lg:
    fontFamily: Bricolage Grotesque
    fontSize: 44px
    fontWeight: '700'
    lineHeight: 52px
  display-lg-mobile:
    fontFamily: Bricolage Grotesque
    fontSize: 32px
    fontWeight: '700'
    lineHeight: 40px
  headline-lg:
    fontFamily: Bricolage Grotesque
    fontSize: 32px
    fontWeight: '600'
    lineHeight: 40px
  headline-lg-mobile:
    fontFamily: Bricolage Grotesque
    fontSize: 26px
    fontWeight: '600'
    lineHeight: 34px
  headline-md:
    fontFamily: Bricolage Grotesque
    fontSize: 22px
    fontWeight: '600'
    lineHeight: 28px
  headline-sm:
    fontFamily: Bricolage Grotesque
    fontSize: 18px
    fontWeight: '600'
    lineHeight: 24px
  body-lg:
    fontFamily: DM Sans
    fontSize: 16px
    fontWeight: '400'
    lineHeight: 24px
  body-md:
    fontFamily: DM Sans
    fontSize: 14px
    fontWeight: '400'
    lineHeight: 20px
  body-sm:
    fontFamily: DM Sans
    fontSize: 12px
    fontWeight: '400'
    lineHeight: 16px
  label-lg:
    fontFamily: DM Sans
    fontSize: 14px
    fontWeight: '600'
    lineHeight: 18px
  label-md:
    fontFamily: DM Sans
    fontSize: 12px
    fontWeight: '500'
    lineHeight: 16px
  label-sm:
    fontFamily: DM Sans
    fontSize: 11px
    fontWeight: '500'
    lineHeight: 14px
rounded:
  sm: 0.5rem
  DEFAULT: 1rem
  md: 1.5rem
  lg: 2rem
  xl: 3rem
  full: 9999px
spacing:
  gutter: 1rem
  margin: 1rem
  space-xs: 0.25rem
  space-sm: 0.5rem
  space-md: 1rem
  space-lg: 1.5rem
  space-xl: 2.5rem
---

## Brand & Style
The design system embodies an eccentric indie maker ethos rooted in deep craft traditions, designed for an artisan lifestyle and mobile commerce experience. It bridges natural, earthy textures with tactile, pill-shaped digital components to evoke warmth, handmade authenticity, and modern shopkeeper charm.

### Target Audience & Emotional Response
The experience speaks to craft enthusiasts, mindful consumers, and independent lifestyle shoppers who value thoughtful provenance over mass production. The UI evokes the sensation of thumbing through bespoke stationery, handmade ceramics, and studio wares: tactile, grounding, friendly, and delightfully curated.

### Design Movement & Aesthetic Direction
- **Tactile Neo-Organic:** High-curvature pill buttons, smooth clay-like card surfaces, and delicate warm-toned borders simulate physical labels and studio tags.
- **Eclectic Artisan Typography:** Anchored by the expressive, organic letterforms of Bricolage Grotesque paired with the understated legibility of DM Sans.
- **Warm Studio Canvas:** Avoids sterile stark whites in favor of soft linen and oatmeal tones, enriched with sage craft greens, earthen terracotta, and bespoke localized transactional accents.

## Colors
The palette balances grounding organic tones with utility accents designed specifically for localized Southeast Asian e-commerce workflows.

### Core Swatches
- **Primary (`#4A6B53` - Craft Sage):** The grounding studio hue. Used for primary call-to-action buttons, key navigation indicators, active filter states, and brand marks.
- **Secondary (`#C86D51` - Terracotta Clay):** Used for highlighting promotions, cart notifications, sale price tags, and primary action hover states.
- **Tertiary (`#E29E8C` - Clay Blush):** Soft accent for chip selections, product highlight backdrops, and active toggle fills.
- **Neutral (`#2B211E` - Espresso Noir):** Rich dark roast coffee brown used for headlines, high-contrast borders, and primary reading text. Never use pure `#000000`.

### Canvas & Surface Structure
- **Canvas Base:** `#FBF8F3` (Soft Linen Cream) provides a warm, paper-like background.
- **Surface Elevation:** `#FFFFFF` (Crisp Studio White) elevates cards and floating navigation sheets above the linen canvas.
- **Muted Surface:** `#F0EAE1` (Pressed Oatmeal) for subtle container fills, secondary input fields, and disabled states.

### Merchant & Payment Accents
- **GCash Accent:** `#007DFE` (Vibrant Cyan Blue) dedicated to GCash payment method pills, verification tags, and instant checkout CTAs.
- **Logistics Accent:** `#E02020` (J&T Express Red) dedicated to express courier badges, fast-delivery alerts, and delivery status milestones.
- **Cash on Delivery (COD) & Wallet:** `#2E7D32` (Deep Mint) for verified COD and guarantee tokens.

## Typography
Typographic rhythm sets the artisan tone through intentional contrast between expressive titling and clean, highly functional microcopy.

### Hierarchy & Usage
- **Bricolage Grotesque:** Applied to product names, promotional callouts, modal titles, and collection displays. Its handcrafted, eccentric curves express the artisan nature of the inventory.
- **DM Sans:** Carries all functional content including product descriptions, pricing strings, delivery tracking, form fields, and checkout receipts. Clean geometry ensures effortless legibility on high-density mobile screens.
- **Numeric Figures:** All pricing formats (`₱`, `$`) and inventory figures utilize tabular figures in `DM Sans` with medium-to-bold weights for rapid scanning in cart trays and payment breakdown summaries.

## Layout & Spacing
A 4px spatial baseline provides structural consistency across all viewport scales, optimized for single-thumb mobile interaction.

### Layout Model & Grid
- **Mobile Handheld (320px – 599px):** 4-column layout with `1rem` (16px) margins and `1rem` (16px) gutters. Product feeds arrange in 2-column masonry or card grids.
- **Tablet & Medium Displays (600px – 1023px):** 8-column layout with `1.5rem` (24px) gutters and margins, expanding category browses into 3-column rows.
- **Desktop Sheet (1024px+):** 12-column layout capped at a maximum width of `1140px` centered within a linen canvas backdrop.

### Layout Rhythm Rules
- Product lists use `space-md` between tiles; internal card content maintains `space-sm` separation.
- Checkout drawers and sticky bottom sheets enforce a minimum bottom clearance of `space-xl` to clear native operating system home indicators.

## Elevation & Depth
Depth mimics natural studio light falling over thick cotton stock, ceramic tiles, and embossed craft paper rather than synthetic digital blurs.

### Tiers & Elevation Style
- **Level 0 (Canvas Base):** Flat `#FBF8F3` linen floor.
- **Level 1 (Resting Cards & Components):** Subtle warm drop shadow: `0 2px 8px -2px rgba(43, 33, 30, 0.06), 0 1px 2px rgba(43, 33, 30, 0.04)`, bordered by a 1px ghost stroke of `#EADBCE`.
- **Level 2 (Active Product Cards & Floating Trays):** Soft, spread ambient shadow: `0 8px 24px -4px rgba(43, 33, 30, 0.08), 0 2px 6px -1px rgba(43, 33, 30, 0.04)`.
- **Level 3 (Modal Sheets & Mobile Bottom Drawers):** Pronounced elevation: `0 16px 40px -8px rgba(43, 33, 30, 0.16)` with a warm 40% `#2B211E` backdrop scrim.
- **Tactile Inset:** Selected chip filters and pressed states use an inner shadow (`inset 0 2px 4px rgba(43, 33, 30, 0.08)`) to mimic debossed studio paper seals.

## Shapes
The shape philosophy centers on hyper-tactile, pill-shaped aesthetics (Roundedness Level 3) that feel organic, approachable, and smooth to touch.

### Curvature Tokens
- **Pill Primitives (`9999px`):** All actionable buttons, badge tags, filter chips, category pills, and payment provider selectors use fully rounded pill silhouettes.
- **Containers & Product Cards (`rounded-lg` / `2rem`):** Standard product cards, modal sheets, and preview tiles adopt `2rem` corner radii for a friendly pebble-like silhouette.
- **Nested Inner Surfaces (`rounded-md` / `1rem`):** Embedded image frames within cards, input fields, and nested promotional banners use `1rem` corner radii to maintain concentric geometric balance.

## Components

### Buttons
- **Primary Action (Add to Cart / Buy Now):** Fully pill-shaped, `#4A6B53` (Craft Sage) fill with `#FFFFFF` text in `label-lg`. Pressed state depresses visually via a subtle downward translate (1px) and 10% darkening.
- **Secondary / Craft Outline:** White surface with 1.5px solid `#4A6B53` border, Espresso text, and clay hover wash.
- **Urgent Action (Checkout / Limited Drop):** `#C86D51` (Terracotta Clay) fill for primary conversion triggers.

### Chips & Payment Selectors
- **Category Filter Chips:** Fully pill-shaped, height 36px. Default: `#F0EAE1` background with Espresso text. Active: `#4A6B53` background with white text and a tiny botanical dot indicator.
- **Payment Badges & Gateway Chips:**
  - *GCash Option:* Crisp white pill container with GCash Cyan (`#007DFE`) badge mark, crisp 1px `#D9E6F2` stroke, and selected radio tick.
  - *J&T Delivery Tag:* Micro-pill with `#E02020` outline, soft 5% red tint fill, and bold J&T courier icon.
  - *COD Pill:* Soft Linen badge tagged with green check indicator (`#2E7D32`).

### Product Cards
- **Construction:** Crisp `#FFFFFF` surface with `2rem` rounded exterior corners, Level 1 shadow, and a 1px `#EADBCE` hairline boundary.
- **Media Frame:** Top container inset with `1rem` rounded corners, presenting photography on a warm studio backdrop.
- **Tag Overlay:** Floating pill badges at the top-left of the card (e.g., "Handmade", "Limited Run", "Eco Clay") set in `label-sm`.
- **Pricing & Quick-Add:** Dual column layout featuring Bricolage Grotesque pricing alongside a terracotta circular tap button (`+`) for single-touch cart addition.

### Form Inputs & Search
- **Search Bar:** Pill-shaped 48px height with `#FFFFFF` base, `#2B211E` placeholder at 50% opacity, prefix magnifying icon, and subtle linen stroke. Focus triggers a 1.5px `#4A6B53` outline without harsh browser glows.
- **Quantity Pickers:** Pill capsule containing decrement, counter text, and increment operators encased in smooth `#F0EAE1` pressed oatmeal fill.

### List & Line Items
- Checkout item rows use separated horizontal rounded cards with dashed 1px `#EADBCE` craft dividers, displaying miniature square rounded thumbnails alongside espresso item titles and payment method badges.