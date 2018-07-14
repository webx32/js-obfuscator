# js-obfuscator

# Here is simple example how to used it:

	<?php
	include_once 'packer.php';
	if(!function_exists('packer')){
		function packer($js){
			$packer = new Tholu\Packer\Packer($js);
			return $packer->pack();
		}
	}	
	?>
	<script type="text/javascript">
	<?php
	ob_start();
	?>

	function setCookie(cname, cvalue, expired) {
	    var d = new Date();
	    d.setTime(d.getTime() + (expired*1000));
	    var expires = "expires="+ d.toUTCString();
	    document.cookie = cname + "=" + cvalue + ";" + expires + ";path=/";
	} 
	function getCookie(cname) {
	    var name = cname + "=";
	    var decodedCookie = decodeURIComponent(document.cookie);
	    var ca = decodedCookie.split(';');
	    for(var i = 0; i <ca.length; i++) {
		var c = ca[i];
		while (c.charAt(0) == ' ') {
		    c = c.substring(1);
		}
		if (c.indexOf(name) == 0) {
		    return c.substring(name.length, c.length);
		}
	    }
	    return "";
	}
	<?php
		$script = ob_get_contents();
		ob_clean();
		echo packer($script);
	?>
	</script>
