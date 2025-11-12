# Greek character search and export the results
Use the following command to run the Greek character search and export the results to the specified log file:  
`grep -r -n -P '[\x{0370}-\x{03FF}\x{1F00}-\x{1FFF}]' /home/USERNAME/public_html/catalog/view/theme/digital4u/template/ > /home/USERNAME/public_html/greek-texts.log`

Example:  
**/home/USERNAME/public_html/catalog/view/theme/digital4u/template/product/product.twig:109:** `<div class="stock_section available"><strong>1 τελευταίο τεμάχιο</strong></div>`  
**/home/USERNAME/public_html/catalog/view/theme/digital4u/template/product/product.twig:111:** `<div class="stock_section available"><strong>Άμεσα Διαθέσιμο</strong></div>`
