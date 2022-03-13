# authenticator-test

https://lordmikefin.github.io/authenticator-test/

<!--
https://github.com/jiangts/JS-OTP
https://github.com/jiangts/JS-OTP/raw/master/dist/jsOTP.js
-->

<script src='https://github.com/jiangts/JS-OTP/raw/master/dist/jsOTP.js'></script>
<script>
// hotp
var hotp = new jsOTP.hotp();
var hmacCode = hotp.getOtp(<your OTP key>, <counter>);

// totp
var totp = new jsOTP.totp();
var timeCode = totp.getOtp(<your OTP key>);

console.log("hotp: " + hotp);
console.log("totp: " + totp);
</script>

