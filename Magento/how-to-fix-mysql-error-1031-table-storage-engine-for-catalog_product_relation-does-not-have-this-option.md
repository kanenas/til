# How to fix mysql error 1031 - Table storage engine for 'catalog_product_relation' doesn't have this option?

This is due to the table option that you have in your CREATE TABLE DDL: `ROW_FORMAT=FIXED`

**Read more**: https://magento.stackexchange.com/a/139741/37289
