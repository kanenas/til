# Play Video from your Website
Όταν χρησιμοποιούμε το Opencart extension **Play Video from your Website** https://www.opencart.com/index.php?route=marketplace/extension/info&extension_id=36623, θα πρέπει η μορφή του `/catalog/view/theme/default/template/extension/module/video_player.twig` να είναι όπως στο παρακάτω παράδειγμα.  
**ΠΡΟΣΟΧΗ**: Για **iPhone** συσκευές χρειάζεται οπωσδήποτε το **attribute** `playsinline`.
```
<div class="video-player">
    <video playsinline autoplay loop muted width="{{video_width}}" height="{{video_height}}">
        <source src="{{video_path}}" type="{{file_type}}">
        Your browser does not support the video tag.
    </video>
</div>
```
