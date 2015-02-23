# streamfast

I just want to play a YouTube video using HTML5 in Android so that I can change the speed !! It's not working though.

##my process of making this app

Code was generated by following this tutorial for a simple hello world app
http://www.raywenderlich.com/56107/make-first-android-app-part-1

and adding a webview using code from here
http://developer.android.com/reference/android/webkit/WebView.html

and using the youtube iframe API example code from here in the test.html file in assets
https://developers.google.com/youtube/iframe_api_reference

To fix errors:
turned on hardware acceleration on the application level
http://developer.android.com/guide/topics/graphics/hardware-accel.html

set webchromeclient
http://developer.android.com/reference/android/webkit/WebView.html




###Notes to self
this error is failure to load the debugger or something. i don't think it's important.
```
E/SELinux﹕ Function: selinux_android_load_priority [0], There is no sepolicy file
E/SELinux﹕ Function: selinux_android_load_priority [1], There is no sepolicy version file
E/SELinux﹕ selinux_android_seapp_context_reload: seapp_contexts file is loaded from /seapp_contexts
```
based on info from: http://stackoverflow.com/questions/23020389/function-selinux-android-load-priority-0-there-is-no-sepolicy-file

This error occurs in Genymotion only and can be fixed by uninstalling the app before running it again.
```
W/EGL_genymotion﹕ eglSurfaceAttrib not implemented
E/OpenGLRenderer﹕ Getting MAX_TEXTURE_SIZE from GradienCache
E/OpenGLRenderer﹕ Getting MAX_TEXTURE_SIZE from Caches::initConstraints()
```

this error might be a meaningful security error that's stopping me from opening a youtube video from an iframe within a non youtube URL. it seems insurmountable.
```
E/Web Console﹕ Unsafe JavaScript attempt to access frame with URL file:///android_asset/test.html from frame with URL https://www.youtube.com/embed/5GBT37_yyzY?enablejsapi=1. Domains, protocols and ports must match.
            at null:1
```

###debugging notes

I've tried using a test.html local file on the Android device that is basically the same code as the example code from the YouTube iFrame API reference https://developers.google.com/youtube/iframe_api_reference but with different video URL and playing the whole video (not just the first 6 seconds)

I've tried a simpler iframe embed in an html file that looks like this
```
<!DOCTYPE html>
<html>
<iframe class="youtube-player" type="text/html" width="640" height="385" src="https://www.youtube.com/embed/5GBT37_yyzY?html5=1" frameborder="0"/>
</html>
```

I've tried using an external website (not on the android machine) to load the test.html (renamed index.html) at http://104.131.76.201:5000/
this works fine on Desktop but not on the mobile browser (iphone or android) and not in the mobile app i made.
The HTML file hosted on this server is [index.html](index.html)
HELP!