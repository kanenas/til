# SEO Mega KIT PLUS
### static public function _clear( $str, $clearOn )
`/catalog/controller/common/seo_mega_pack_pro_url.php`  

### 500 Error in `/admin`  
`/admin/controller/extension/module/ocm.php`  
**Lines**: 24-34 (comment)
```
        // hide ocm modules
        if (!empty($data['extensions']) && is_array($data['extensions']) && count($data['extensions']) > 0) {
            foreach ($data['extensions'] as $index => $extension) {
                if (!empty($extension['install'])
                    && (strpos($extension['install'], 'code=ocm') !== false 
                        || strpos($extension['install'], 'extension=ocm') !== false
                        || preg_match('/extension=xpayment\d/m', $extension['install'], $matches, PREG_OFFSET_CAPTURE, 0)))  {
                    unset($data['extensions'][$index]);
                }
            }
        }
```
### Banners
`/system/_seo_mega_pack_seo_image.ocmod.xml`  
**Lines**: 28-37 (comment)
