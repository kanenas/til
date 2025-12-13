## Professional OpenCart 3.x Upgrade Sequence

**CRITICAL: Backups First!**
1. Full file system backup
2. Complete database backup
3. Document all custom modifications

### Recommended Update Order:

**Phase 1: Foundation Preparation**
```
1. Disable all non-essential extensions
2. Clear all caches (OpenCart, Journal, browser)
3. Put store in maintenance mode
```

**Phase 2: Core OpenCart Update**
```
3.0.3.9 → 3.0.4.0 → 3.0.5.0
```
- Apply OpenCart patches sequentially
- NEVER skip versions in 3.x branch
- Test core functionality after each minor update

**Phase 3: Journal Theme Update**
```
3.1.13 → 3.2.0 → 3.2.8
```
**Critical Journal-Specific Notes:**
1. **DO NOT** overwrite your existing Journal installation directly
2. Journal 3.2.x has MAJOR architectural changes
3. Must check compatibility with your installed modules/extensions

**Phase 4: Post-Update Sequence**
1. Clear all caches again
2. Re-enable extensions one by one
3. Test each functionality
4. Update any module-specific settings

### Critical Warnings for Your Specific Upgrade:

⚠️ **Journal 3.1.13 → 3.2.8 DANGERS:**
- Database schema changes are substantial
- Template structure completely different
- Many old modules incompatible
- Custom CSS/JS will likely break

⚠️ **OpenCart 3.0.3.9 → 3.0.5.0 Notes:**
- Security patches are main difference
- Few breaking changes, but test payment/shipping modules

### Alternative Safer Approach (Recommended):

**Option A: Staged Migration**
1. Update OpenCart to 3.0.5.0 first
2. **STOP and TEST** for 24-48 hours
3. Then update Journal (schedule downtime)

**Option B: Fresh Installation (Safest)**
1. Fresh install of OpenCart 3.0.5.0
2. Fresh install of Journal 3.2.8
3. Migrate data incrementally
4. Test in staging environment first

### Must-Check Items:

**Before Starting:**
- Check Journal documentation for migration guide
- Verify all custom theme files are documented
- Ensure PHP version compatibility (7.4+ recommended)

**After Journal Update:**
- Rebuild Journal cache via admin panel
- Reconfigure theme settings (many reset to defaults)
- Check all custom template overrides

### Time Estimate:
- Core OpenCart update: 1-2 hours
- Journal update: 4-8 hours (with testing)
- **Total with proper testing: 8-16 hours**

**Pro Tip:** Create a staging environment first. The Journal 3.1→3.2 jump is significant - many shops hire professional help for this specific transition due to breaking changes in the theme engine.

## **Detailed Backup & Migration Guide for Journal 3.1.13 → 3.2.8**

### **PART 1: COMPREHENSIVE JOURNAL CUSTOMIZATION BACKUP**

#### **A. Database Customizations Backup**

**1. Journal-Specific Tables (Export these separately):**
```sql
-- These tables contain ALL Journal settings
journal3_setting          -- Theme settings database
journal3_style            -- CSS/LESS styles
journal3_variable         -- Template variables
journal3_module           -- Module instances
journal3_layout           -- Layout assignments
journal3_skin             -- Skin configurations
journal3_newsletter       -- Newsletter data (if used)

-- Quick export command via SSH:
mysqldump -u username -p database_name $(mysql -u username -p database_name -N -e "SHOW TABLES LIKE 'journal3%'") > journal3_backup.sql
```

**2. Custom Data Locations:**
```sql
-- Check for customizations in these OpenCart tables
SELECT * FROM oc_setting WHERE code LIKE '%journal3%' OR code LIKE '%journal%';
SELECT * FROM oc_layout_module WHERE code LIKE '%journal%';
SELECT * FROM oc_module WHERE code LIKE '%journal%';
```

#### **B. File System Customizations Backup**

**1. Critical Journal Custom Directories:**
```
catalog/view/theme/journal3/
├── template/              # Template overrides (MOST IMPORTANT!)
│   ├── common/           # Header, footer customizations
│   ├── product/          # Product page changes
│   ├── journal3/         # Journal-specific templates
│   └── custom/           # Your custom templates
├── scss/                 # Custom SCSS files
│   ├── custom.scss
│   └── variables.scss    # Color/typography variables
├── js/                   # Custom JavaScript
│   ├── custom.js
│   └── journal/          # Modified Journal JS
└── image/               # Custom theme images

admin/controller/journal3/    # Custom admin controllers
admin/view/template/journal3/ # Admin template mods
system/library/journal3/      # Library modifications
```

**2. Backup Command Script:**
```bash
#!/bin/bash
# Save as: backup_journal.sh
BACKUP_DIR="/path/to/backup/$(date +%Y%m%d_%H%M%S)"
mkdir -p $BACKUP_DIR

# Backup Journal theme files
cp -r /path/to/opencart/catalog/view/theme/journal3 $BACKUP_DIR/
cp -r /path/to/opencart/admin/controller/journal3 $BACKUP_DIR/
cp -r /path/to/opencart/admin/view/template/journal3 $BACKUP_DIR/
cp -r /path/to/opencart/system/library/journal3 $BACKUP_DIR/

# Backup specific OpenCart files that might be modified
cp /path/to/opencart/catalog/controller/common/header.php $BACKUP_DIR/
cp /path/to/opencart/catalog/controller/common/footer.php $BACKUP_DIR/
cp /path/to/opencart/catalog/language/en-gb/common/header.php $BACKUP_DIR/

echo "Backup completed to: $BACKUP_DIR"
```

#### **C. Settings & Configuration Backup**

**1. Export Journal Admin Settings:**
```php
// Create a quick PHP script to dump Journal settings
// Save as: backup_journal_settings.php in admin folder
if (isset($_GET['key']) && $_GET['key'] === 'YOUR_SECRET_KEY') {
    $store_id = 0;
    $query = $this->db->query("SELECT * FROM " . DB_PREFIX . "journal3_setting WHERE store_id = '" . (int)$store_id . "'");
    
    header('Content-Type: application/json');
    echo json_encode($query->rows, JSON_PRETTY_PRINT);
    exit;
}
```

**2. Document Current Settings Manually:**
- Go to **Journal Admin → Dashboard**
- Take screenshots of:
  - **Theme Settings** (all tabs)
  - **Skin Manager** (all skins)
  - **Style Editor** (all custom CSS)
  - **Layout Builder** (all layouts)
  - **Module Manager** (all modules)

### **PART 2: DATABASE CHANGE HANDLING STRATEGY**

#### **A. Pre-Migration Preparation**

**1. Create Migration Log Table:**
```sql
CREATE TABLE IF NOT EXISTS journal3_migration_log (
    id INT AUTO_INCREMENT PRIMARY KEY,
    action VARCHAR(100),
    old_value TEXT,
    new_value TEXT,
    status VARCHAR(20),
    timestamp TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

**2. Check Current Schema:**
```sql
-- Document current table structure
SHOW CREATE TABLE journal3_setting;
SHOW CREATE TABLE journal3_style;
SHOW CREATE TABLE journal3_variable;

-- Count records for reference
SELECT 
    'journal3_setting' as table_name, 
    COUNT(*) as record_count 
FROM journal3_setting
UNION ALL
SELECT 'journal3_style', COUNT(*) FROM journal3_style
UNION ALL
SELECT 'journal3_variable', COUNT(*) FROM journal3_variable;
```

#### **B. Safe Database Migration Approach**

**Option 1: Incremental Migration (Recommended)**
```sql
-- Step 1: Create backup of current data
CREATE TABLE journal3_setting_backup SELECT * FROM journal3_setting;
CREATE TABLE journal3_style_backup SELECT * FROM journal3_style;
CREATE TABLE journal3_variable_backup SELECT * FROM journal3_variable;

-- Step 2: Export settings to JSON for reference
SELECT 
    setting_name,
    setting_value,
    serialized 
INTO OUTFILE '/tmp/journal3_settings.csv'
FIELDS TERMINATED BY ',' 
ENCLOSED BY '"'
LINES TERMINATED BY '\n'
FROM journal3_setting;

-- Step 3: Compare schemas before/after update
-- Run this BEFORE and AFTER Journal update
SELECT 
    TABLE_NAME,
    COLUMN_NAME,
    DATA_TYPE,
    COLUMN_DEFAULT
FROM INFORMATION_SCHEMA.COLUMNS 
WHERE TABLE_NAME LIKE 'journal3_%' 
AND TABLE_SCHEMA = 'your_database'
ORDER BY TABLE_NAME, ORDINAL_POSITION;
```

**Option 2: Migration Script Template**
```php
<?php
// migration_check.php - Run this BEFORE updating
class JournalMigrationChecker {
    private $db;
    
    public function __construct($db) {
        $this->db = $db;
    }
    
    public function checkSettings() {
        $query = $this->db->query("SELECT * FROM " . DB_PREFIX . "journal3_setting");
        $settings = [];
        
        foreach ($query->rows as $row) {
            if ($row['serialized']) {
                $settings[$row['setting_name']] = unserialize($row['setting_value']);
            } else {
                $settings[$row['setting_name']] = $row['setting_value'];
            }
        }
        
        // Save to file for comparison
        file_put_contents('journal_settings_pre.json', 
            json_encode($settings, JSON_PRETTY_PRINT));
        
        return $settings;
    }
    
    public function findCustomizations() {
        // Look for non-standard settings
        $custom = [];
        
        // Example: Check for custom templates
        $query = $this->db->query("
            SELECT DISTINCT setting_value 
            FROM " . DB_PREFIX . "journal3_setting 
            WHERE setting_name LIKE '%template%' 
            AND setting_value NOT LIKE 'journal3/%'
        ");
        
        return $query->rows;
    }
}
?>
```

### **PART 3: SPECIFIC CUSTOMIZATION PRESERVATION**

#### **A. Template Customizations**

**1. Identify Modified Templates:**
```bash
# Compare with original Journal 3.1.13 files
diff -r /path/to/your/journal3/ /path/to/original/journal3-3.1.13/ > template_differences.txt

# Or use this PHP approach:
$original_dir = 'journal3-3.1.13/catalog/view/theme/journal3/template/';
$your_dir = 'catalog/view/theme/journal3/template/';

$iterator = new RecursiveIteratorIterator(new RecursiveDirectoryIterator($your_dir));
foreach ($iterator as $file) {
    if ($file->isFile()) {
        $relative_path = str_replace($your_dir, '', $file->getPathname());
        $original_file = $original_dir . $relative_path;
        
        if (!file_exists($original_file) || 
            md5_file($file->getPathname()) !== md5_file($original_file)) {
            echo "Customized: " . $relative_path . "\n";
            copy($file->getPathname(), 'backup/templates/' . $relative_path);
        }
    }
}
```

**2. Common Customization Locations to Backup:**
```
# These files often contain customizations:
catalog/view/theme/journal3/template/common/header.twig
catalog/view/theme/journal3/template/common/footer.twig
catalog/view/theme/journal3/template/product/product.twig
catalog/view/theme/journal3/template/journal3/module/blog.twig
catalog/view/theme/journal3/template/journal3/template/header/header_1.twig
```

#### **B. CSS/SCSS Customizations**

**1. Extract Custom Styles:**
```bash
# Find all custom SCSS/CSS
grep -r "custom-" catalog/view/theme/journal3/scss/ > custom_styles.txt
grep -r "// Custom" catalog/view/theme/journal3/scss/ >> custom_styles.txt

# Backup entire SCSS structure
cp -r catalog/view/theme/journal3/scss/ backup/scss_backup/
```

**2. Document Custom Variables:**
```scss
// Extract from variables.scss
$primary-color: #ff0000;      // Your custom primary
$secondary-color: #00ff00;    // Your custom secondary
$font-family: 'Custom Font';  // Custom fonts
```

### **PART 4: STEP-BY-STEP MIGRATION PROCEDURE**

**Phase 1: Pre-Migration (Do this FIRST)**
```
1. Run database backups (as above)
2. Document all customizations (use checklist)
3. Create staging environment
4. Disable Journal cache
5. Export current settings to JSON
```

**Phase 2: Safe Update Process**
```
1. Update OpenCart to 3.0.5.0 FIRST
2. TEST core functionality
3. Install fresh Journal 3.2.8 in NEW directory
4. Compare database structures
5. Migrate settings incrementally
```

**Phase 3: Post-Migration Verification**
```
1. Compare settings between old and new
2. Check template compatibility
3. Test responsive design
4. Verify all modules work
5. Clear ALL caches
```

### **PART 5: ROLLBACK PLAN**

Create this rollback script:
```php
<?php
// rollback_journal.php
class JournalRollback {
    public static function restoreDatabase() {
        // Restore from backup tables
        $db->query("DROP TABLE IF EXISTS journal3_setting");
        $db->query("CREATE TABLE journal3_setting SELECT * FROM journal3_setting_backup");
        
        // Repeat for other tables...
    }
    
    public static function restoreFiles() {
        // Copy backed up files back
        exec("cp -r /backup/journal3/ /catalog/view/theme/");
        exec("cp -r /backup/admin_journal3/ /admin/controller/journal3/");
    }
}
?>
```

### **CRITICAL CHECKLIST:**

✅ **Before Update:**
- [ ] Database backup with Journal tables isolated
- [ ] File system backup including all custom templates
- [ ] Settings exported to JSON
- [ ] Screenshots of current design
- [ ] List of all active Journal modules

✅ **During Update:**
- [ ] Update OpenCart first
- [ ] Install Journal 3.2.8 in separate directory
- [ ] Compare database schemas
- [ ] Migrate settings systematically

✅ **After Update:**
- [ ] Verify all custom templates still work
- [ ] Check mobile responsiveness
- [ ] Test all Journal modules
- [ ] Validate SEO URLs
- [ ] Confirm payment/shipping modules function

### **PRO TIPS:**

1. **Use Git:** Initialize git in your theme directory:
   ```bash
   cd catalog/view/theme/journal3
   git init
   git add .
   git commit -m "Pre-migration backup"
   ```

2. **Create Migration Map:** Document where each customization from 3.1.13 should go in 3.2.8

3. **Journal 3.2.8 Specific:** The new version uses different template syntax in some places. Be prepared to rewrite some custom template logic.

4. **Contact Journal Support:** They might have migration tools. Always check their documentation first.
