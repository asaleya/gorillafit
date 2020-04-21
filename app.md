<div id="text">detecting device..</div>

<script src="./js-file-downloader.min.js"></script>
<script>
 /**
 * Determine the mobile operating system.
 * This function returns one of 'iOS', 'Android', 'Windows Phone', or 'unknown'.
 *
 * @returns {String}
 */
function getMobileOperatingSystem() {
  var userAgent = navigator.userAgent || navigator.vendor || window.opera;

      // Windows Phone must come first because its UA also contains "Android"
    if (/windows phone/i.test(userAgent)) {
        return "Windows Phone";
    }

    if (/android/i.test(userAgent)) {
        return "Android";
    }

    // iOS detection from: http://stackoverflow.com/a/9039885/177710
    if (/iPad|iPhone|iPod/.test(userAgent) && !window.MSStream) {
        return "iOS";
    }

    return "unknown";
}  

var platform = getMobileOperatingSystem()
if(platform == "Windows Phone") document.getElementById("text").innerHTML = "sorry, diet challenge app currently doesn't support windows phones"
if(platform == "Android" || platform == "iOS" || platform == "unknown") {
  //window.location = "https://play.google.com/store/apps/details?id=com.dietchallenge"
    // Then somewhere in your code
  new jsFileDownloader({ url: 'http://gorilla.fitness/gorillaFit.apk' })
    .then(function () {
      // Called when download ended
    })
    .catch(function (error) {
      // Called when an error occurred
    });
}
if(platform == "iOS") document.getElementById("text").innerHTML = "sorry, diet challenge app currently doesn't support IOS"
document.getElementById("text").innerHTML = 'page has been loaded successfully'
</script>
