
# [authenticator-test page](https://github.com/lordmikefin/authenticator-test)


<div id="totp-time-code">code test</div>

<div id="qr"></div>

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

<script src='https://cdn.jsdelivr.net/gh/jquery/jquery@3.6.0/dist/jquery.min.js'></script>

<script src='https://cdn.jsdelivr.net/gh/jiangts/JS-OTP/dist/jsOTP.js'></script>
<script>
// hotp
//var hotp = new jsOTP.hotp();
//var hmacCode = hotp.getOtp(OTPkey, counter);

// totp
var totp = new jsOTP.totp();
//var timeCode = totp.getOtp("f22cf12943336d8fe16335bb0cbc3f0d748aabb2");

//console.log("hotp: " + hotp);
//console.log("totp timeCode: " + timeCode);


function updateTimeCode() {
    let secret_hex = "f22cf12943336d8fe16335bb0cbc3f0d748aabb2";
    let secret_base32 = "7gbk755ey5kqdzowzhjso66mwznxdsfc";
    
    // Update the time code
    var timeCode = totp.getOtp(secret_base32);
    console.log("totp timeCode: " + timeCode);
    
    // Show time code in the div element
    $( "#totp-time-code" ).text(timeCode);
};

function repeatUpdateTimeCode() {
    updateTimeCode();
    
    setTimeout(function() {
        repeatUpdateTimeCode();
    }, 1000); // 1 sec
};
repeatUpdateTimeCode()

// Run code after page load
$(window).on('load', function() {
    // code here
});
</script>


<!--
TODO: generate 2fa qrcode

https://github.com/stefansundin/2fa-qr/blob/gh-pages/index.html

https://jwessel.github.io/totp-gauth-token/QR_generator.html
https://www.xanxys.net/totp/
-->

<script src="https://cdn.jsdelivr.net/gh/lrsjng/jquery-qrcode@v0.18.0/dist/jquery-qrcode.min.js"></script>
<script>

function generate_uri() {
  let secret_hex = "f22cf12943336d8fe16335bb0cbc3f0d748aabb2";
  let secret_base32 = "7gbk755ey5kqdzowzhjso66mwznxdsfc";
  
  //let s = `otpauth://totp/Label?secret=${secret_hex}&issuer=Issuer&algorithm=SHA1&digits=6&period=30`;
  let s = `otpauth://totp/Label?secret=${secret_base32}&issuer=Issuer&algorithm=SHA1&digits=6&period=30`;
  /*
  let s = `otpauth://${type.value}/${encodeURIComponent(label.value)}?secret=${secret.value.replace(/ /g, '')}`;
  if (issuer.value !== "") {
    s += `&issuer=${encodeURIComponent(issuer.value)}`;
  }
  if (type.value === "hotp") {
    s += `&counter=${counter.value || "0"}`;
  }
  if (advanced_options.checked) {
    s += `&algorithm=${algorithm.value}&digits=${digits.value}`;
    if (type.value === "totp") {
      s += `&period=${period.value || "30"}`;
    }
  }
  */
  return s;
}

function update_qr() {
  $("#qr").empty().qrcode({
    text: generate_uri(),
    size: 300,
  });
  /*
  $("#qr").empty().qrcode({
    text: uri.value,
    size: size.value,
  });

  if (label.value === "" && issuer.value === "") {
    app_label.textContent = "Issuer (label)";
  }
  else {
    app_label.textContent = issuer.value === "" ? label.value : `${issuer.value} (${label.value})`;
  }
  */
}

update_qr();
</script>







