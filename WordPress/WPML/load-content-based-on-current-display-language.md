# Get the current display language
WPML Hooks » wpml_current_language (https://wpml.org/wpml-hook/wpml_current_language/)
```
<?php
$current_language_code = apply_filters( 'wpml_current_language', null );
if($current_language_code == 'en' || $current_language_code == 'el') { //English or Greek
  //Load the content here...
}
```
