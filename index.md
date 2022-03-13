
# [authenticator-test page](https://github.com/lordmikefin/authenticator-test)


<!--
https://github.com/jiangts/JS-OTP
https://github.com/jiangts/JS-OTP/raw/master/dist/jsOTP.js
-->
<!--
https://stackoverflow.com/questions/19285686/how-to-load-javascript-files-from-github-externally
Github is not a CDN  !!!

Using cdn.jsdelivr.net 
https://cdn.jsdelivr.net/gh/-username-/-repository-/-file-

For example pasing from 
  https://raw.github.com/myusername/myrepo/master/style.css
to
  https://cdn.jsdelivr.net/gh/myusername/myrepo/style.css
-->

<script src='https://cdn.jsdelivr.net/gh/jiangts/JS-OTP/dist/jsOTP.js'></script>
<script>
// hotp
//var hotp = new jsOTP.hotp();
//var hmacCode = hotp.getOtp(OTPkey, counter);

// totp
var totp = new jsOTP.totp();
var timeCode = totp.getOtp("f22cf12943336d8fe16335bb0cbc3f0d748aabb2");

//console.log("hotp: " + hotp);
console.log("totp: " + totp);
</script>


