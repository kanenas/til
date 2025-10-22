Here's a comprehensive list of available routes organized by functionality:

## 📋 CORE Opencart 3.X ROUTES

### 🛒 CATALOG ROUTES (Front-end)

**Common Routes:**
- `common/home` - Homepage
- `common/header` - Header section
- `common/footer` - Footer section
- `common/currency` - Currency switcher
- `common/language` - Language switcher
- `common/maintenance` - Maintenance mode
- `common/seo_url` - SEO URL handling

**Account Routes:**
- `account/account` - Account dashboard
- `account/login` - Login page
- `account/logout` - Logout
- `account/register` - Registration
- `account/edit` - Edit account
- `account/password` - Change password
- `account/address` - Address book
- `account/wishlist` - Wishlist
- `account/order` - Order history
- `account/download` - Downloads
- `account/reward` - Reward points
- `account/return` - Returns
- `account/transaction` - Transactions
- `account/newsletter` - Newsletter subscription
- `account/forgotten` - Password reset
- `account/voucher` - Gift vouchers

**Product Routes:**
- `product/product` - Product page
- `product/category` - Category page
- `product/manufacturer` - Manufacturers
- `product/manufacturer/info` - Manufacturer info
- `product/search` - Search results
- `product/special` - Special offers
- `product/compare` - Product comparison
- `product/review` - Product reviews

**Checkout Routes:**
- `checkout/cart` - Shopping cart
- `checkout/checkout` - Checkout process
- `checkout/success` - Order success
- `checkout/guest` - Guest checkout
- `checkout/guest_shipping` - Guest shipping
- `checkout/register` - Checkout registration

**Information Routes:**
- `information/contact` - Contact page
- `information/sitemap` - Sitemap
- `information/information` - Information pages

**Affiliate Routes:**
- `affiliate/login` - Affiliate login
- `affiliate/register` - Affiliate registration
- `affiliate/account` - Affiliate account
- `affiliate/edit` - Edit affiliate info
- `affiliate/password` - Affiliate password
- `affiliate/payment` - Affiliate payment
- `affiliate/tracking` - Affiliate tracking
- `affiliate/transaction` - Affiliate transactions
- `affiliate/logout` - Affiliate logout
- `affiliate/forgotten` - Affiliate password reset

### 🔧 ADMIN ROUTES (Back-end)

**Common Admin Routes:**
- `common/dashboard` - Admin dashboard
- `common/filemanager` - File manager
- `common/security` - Security settings

**Catalog Management:**
- `catalog/category` - Category management
- `catalog/product` - Product management
- `catalog/filter` - Filter management
- `catalog/attribute` - Attribute management
- `catalog/attribute_group` - Attribute groups
- `catalog/option` - Product options
- `catalog/manufacturer` - Manufacturer management
- `catalog/download` - Download management
- `catalog/review` - Review management
- `catalog/information` - Information pages

**Extension Routes:**
- `extension/extension` - Extensions overview
- `extension/module` - Module management
- `extension/shipping` - Shipping methods
- `extension/payment` - Payment methods
- `extension/total` - Order totals
- `extension/feed` - Data feeds
- `extension/analytics` - Analytics
- `extension/captcha` - Captcha methods
- `extension/dashboard` - Dashboard modules

**Sales Routes:**
- `sale/order` - Order management
- `sale/return` - Return management
- `sale/voucher` - Gift voucher management
- `sale/voucher_theme` - Voucher themes
- `sale/recurring` - Recurring profiles

**Customer Routes:**
- `customer/customer` - Customer management
- `customer/customer_group` - Customer groups
- `customer/custom_field` - Custom fields

**Marketing Routes:**
- `marketing/marketing` - Marketing campaigns
- `marketing/coupon` - Coupon management
- `marketing/contact` - Email marketing

**System Routes:**
- `setting/setting` - Store settings
- `setting/store` - Multi-store management
- `localisation/location` - Store locations
- `localisation/language` - Language management
- `localisation/currency` - Currency management
- `localisation/stock_status` - Stock statuses
- `localisation/order_status` - Order statuses
- `localisation/return_status` - Return statuses
- `localisation/return_action` - Return actions
- `localisation/return_reason` - Return reasons
- `localisation/country` - Country management
- `localisation/zone` - Zone/Region management
- `localisation/geo_zone` - Geo zones
- `localisation/tax_class` - Tax classes
- `localisation/tax_rate` - Tax rates
- `localisation/length_class` - Length classes
- `localisation/weight_class` - Weight classes

**Design Routes:**
- `design/layout` - Layout management
- `design/banner` - Banner management
- `design/theme` - Theme editor
- `design/translation` - Language translations
- `design/seo_url` - SEO URL management

**Tools Routes:**
- `tool/upload` - Upload management
- `tool/backup` - Backup/Restore
- `tool/error_log` - Error logs

### 🔄 EXTENSION-SPECIFIC ROUTES

**Payment Method Routes:**
- `extension/payment/pp_standard` - PayPal Standard
- `extension/payment/cod` - Cash on Delivery
- `extension/payment/bank_transfer` - Bank Transfer
- `extension/payment/cheque` - Cheque Payment

**Shipping Method Routes:**
- `extension/shipping/flat` - Flat Rate
- `extension/shipping/free` - Free Shipping
- `extension/shipping/item` - Per Item
- `extension/shipping/weight` - Weight Based

### 🎯 KEY POINTS ABOUT OPEN CART 3.X ROUTES:

1. **Route Structure**: `folder/file/method`
2. **Dynamic Routes**: Many routes accept parameters (e.g., product_id, category_id)
3. **SEO URLs**: Routes can be mapped to SEO-friendly URLs
4. **Extension Routes**: Third-party extensions add their own routes
5. **Event System**: Routes can be modified via OpenCart's event system

This list covers the majority of core OpenCart 3.x routes. Third-party extensions will add their own specific routes following the same naming convention.
