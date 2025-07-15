To create an Administrator user in OpenCart without dashboard access, you need to directly modify the database. Follow these steps carefully:

### **Step 1: Get Database Credentials**
1. Locate OpenCart's configuration files:
   - **Root `config.php`**: `/path/to/opencart/config.php`
   - **Admin `config.php`**: `/path/to/opencart/admin/config.php`
2. Note these values:
   ```php
   // In both files:
   define('DB_DRIVER', 'mysqli');
   define('DB_HOSTNAME', 'localhost');      // Database host
   define('DB_USERNAME', 'your_db_user');   // Database username
   define('DB_PASSWORD', 'your_db_pass');   // Database password
   define('DB_DATABASE', 'your_db_name');   // Database name
   define('DB_PREFIX', 'oc_');              // Table prefix (e.g., oc_)
   ```

### **Step 2: Connect to the Database**
Use a tool like **phpMyAdmin**, **MySQL Workbench**, or the **command line** to connect to your database using the credentials above.

### **Step 3: Insert the Administrator User**
Run an SQL query to create the user. Adjust `[PREFIX]`, username, password, and email as needed.

#### **For OpenCart 2.x & 3.x (SHA1 Hashing)**:
```sql
INSERT INTO `[PREFIX]user` (
  `user_group_id`, 
  `username`, 
  `password`, 
  `salt`, 
  `firstname`, 
  `lastname`, 
  `email`, 
  `status`, 
  `date_added`
) 
SELECT 
  1, 
  'new_admin', 
  SHA1(CONCAT(SHA1(salt), SHA1('YourStrongPassword'))), 
  salt, 
  'Admin', 
  'User', 
  'admin@example.com', 
  1, 
  NOW()
FROM (SELECT SUBSTRING(MD5(RAND()) FROM 1 FOR 9) AS salt) AS s;
```
- Replace `[PREFIX]` with your actual table prefix (e.g., `oc_`).
- Change `'new_admin'`, `'YourStrongPassword'`, `'Admin'`, `'User'`, and `'admin@example.com'`.

#### **For OpenCart 4.x (bcrypt Hashing)**:
1. Generate a bcrypt hash using PHP:
   ```php
   <?php
   echo password_hash('YourStrongPassword', PASSWORD_DEFAULT);
   ?>
   ```
   Run this script on your server (e.g., via temporary PHP file) to get the hash (starts with `$2y$`).

2. Insert the user (no `salt` field):
```sql
INSERT INTO `[PREFIX]user` (
  `user_group_id`, 
  `username`, 
  `password`, 
  `firstname`, 
  `lastname`, 
  `email`, 
  `status`, 
  `date_added`
) VALUES (
  1, 
  'new_admin', 
  '$2y$10$GeneratedBcryptHash...', 
  'Admin', 
  'User', 
  'admin@example.com', 
  1, 
  NOW()
);
```

### **Step 4: Verify and Cleanup**
1. **Log in** to OpenCart admin with your new credentials.
2. **Remove temporary files** (e.g., PHP password generator script).
3. **Delete the SQL query history** from your database tool for security.

### **Troubleshooting**:
- **Table prefix mismatch**: Ensure `[PREFIX]` matches `DB_PREFIX`.
- **Password issues**: Regenerate the hash (for 4.x) or re-run the query (for 2.x/3.x).
- **User group**: Verify `user_group_id = 1` exists in `[PREFIX]user_group` (default for admins).
- **Version check**: Confirm your OpenCart version by checking file structure or database settings.

### **Important Notes**:
- **Security**: Use a strong password and delete temporary scripts/queries immediately.
- **Backup**: Always backup your database before making changes.
- **OpenCart 1.5**: Use MD5 hashing instead (not covered here; upgrade if possible).

By following these steps, you’ll create a new admin user directly in the database.
