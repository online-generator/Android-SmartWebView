<!--
 * Smart WebView is an Open Source project that integrates native features into webview to help create advanced hybrid applications. Available on GitHub (https://github.com/mgks/Android-SmartWebView).
 * Initially developed by Ghazi Khan (https://github.com/mgks) under MIT Open Source License.
 * This program is free to use for private and commercial purposes under MIT License (https://opensource.org/licenses/MIT).
 * Please mention project source or developer credits in your Application's License(s) Wiki.
 * Contribute to the project (https://github.com/mgks/Android-SmartWebView/discussions)
 * Sponsor the project (https://github.com/sponsors/mgks)
 * Giving right credits to developers encourages them to keep improving their projects :)
-->
<textarea></textarea>
<span align="center" style="text-align:center">

<a href="https://github.com/mgks/Android-SmartWebView/"><img src="https://raw.githubusercontent.com/mgks/Android-SmartWebView/master/app/src/main/res/mipmap-xxxhdpi/ic_launcher.png" width="100"></a>

<h1>Android Smart WebView</h1>

[![alt text](https://img.shields.io/badge/variant-java-red.svg)](#config-variables) [![alt text](https://img.shields.io/badge/version-0.3-green.svg)](https://github.com/mgks/Android-SmartWebView/releases) [![MIT Licence](https://img.shields.io/badge/license-MIT-blue.svg)](https://github.com/mgks/Android-SmartWebView/blob/master/LICENSE)

</span><span align="center" style="text-align:center">

**[GETTING STARTED](#getting-started) &middot; [PLUGINS](https://mgks.dev/blog/smart-webview#plugins) &middot; [DOCUMENTATION](https://mgks.dev/blog/smart-webview-documentation#index) &middot; [ISSUES](https://github.com/mgks/Android-SmartWebView/issues)**

</span>

SWV is a framework built on Java to develop advanced hybrid webview applications with ease.

A small build with features working out of the box: Live GPS Location, Notifications with FCM, AdMob, Chrome Tabs, Process Camera Input, Upload/Download Files, Custom Rating System, Multiple User Interfaces and more.


## Table of Contents

* [Getting Started](#getting-started)
  * *[YouTube Playlist](https://www.youtube.com/watch?v=vE_GsHwspH4&list=PLUvke9lIV6YMGU5XdQ5zOtDOWxslsg6mT&pp=gAQBiAQB) (external link)*
  * [Prerequisites](#prerequisites)
  * [Setup](#setup)
* [Configurations](#configurations)
  * [Device Permissions](#device-permissions)
  * [Config Variables](#config-variables)
  * [Permission Variables](#permission-variables)
  * [Security Variables](#security-variables)
  * [Other Variables](#other-variables)
* [Features](#features)
  * [GPS Location](#gps-location)
  * [Camera Input](#camera-input)
  * [Firebase Messaging](#firebase-messaging)
  * [Google AdMob](#google-admob)
  * [Chrome Tab](#chrome-tab)
  * [Content Sharing](#content-sharing)
  * [User Interfaces](#user-interfaces)
  * [Rating System](#rating-system)
* [Contributing](#contributing)
* [License](#license)
* [Acknowledgements](#acknowledgements)
* [Contact](#closing-note)

## Getting Started

These instructions will help you get your Smart WebView copy up and running on your local machine for development and testing purposes.

**YouTube Playlist - [Getting Started with Smart WebView](https://www.youtube.com/watch?v=vE_GsHwspH4&list=PLUvke9lIV6YMGU5XdQ5zOtDOWxslsg6mT&pp=gAQBiAQB)**

### Prerequisites

Project was built on Android Studio and requires minimum Android API 21+ (5.0 Lollipop) SDK to test run.

### Setup

1. Download repo or clone the project

    `git clone https://github.com/mgks/Android-SmartWebView`

2. Download `google-services.json` file from Firebase ([instructions](https://github.com/mgks/Android-SmartWebView#firebase-messaging))

3. Load project in Android Studio

    `File > Open > Browse to Project and Select`

4. Let Android Studio process the project and download support libraries and dependencies

5. Just to make sure, try cleaning and rebuilding project before run

    `Build > Clean Project` then `Build > Rebuild Project`

6. Got any error? You better fasten you seatbelt. It's going be a bumpy night.

## Configurations

For detailed configuration, check project [Documentation](https://mgks.dev/blog/smart-webview-documentation#config).

### Device Permissions

You can remove any of the following requests if you do not need them, you can also disable features with permission variables. For default setup, following permissions are required.

```xml
INTERNET
ACCESS_NETWORK_STATE
ACCESS_WIFI_STATE
WRITE_EXTERNAL_STORAGE
READ_EXTERNAL_STORAGE
CAMERA
ACCESS_FINE_LOCATION
VIBRATE
```
```xml
c2dm.permission.RECEIVE
```
```xml
hardware.location.gps
hardware.touchscreen
```

`INTERNET` permission is required for any webview to work.

`WRITE_EXTERNAL_STORAGE` is required for camera file processing: if you have `ASWP_FUPLOAD` and `ASWP_CAMUPLOAD` enabled to upload image/video files.

### Config Variables

Complete webpage URL or load local file as `file:///android_res/dir/file.html`

```kotlin
ASWV_URL   = "https://github.com/mgks"   // domain or directory or address to any root file
```

### Permission Variables

```kotlin
ASWP_JSCRIPT     = true     // enable JavaScript for webview
ASWP_FUPLOAD     = true     // upload files from local device
ASWP_MULFILE     = true     // upload multiple files
ASWP_CAMUPLOAD   = true     // enable camera file upload
ASWP_ONLYCAM     = false    // incase you want only camera for input files

ASWP_LOCATION    = true     // track GPS locations

ASWP_RATINGS     = true     // show ratings dialog; auto configured, edit method get_rating() for customizations
ASWP_PULLFRESH   = true     // pull to refresh feature
ASWP_PBAR        = true     // show progress bar
ASWP_ZOOM        = false    // zoom control for webpages
ASWP_SFORM       = false    // save form data and auto-fill information
ASWP_OFFLINE     = false    // whether the loading webpages are offline or online
ASWP_EXTURL      = true     // open external url with default browser instead of app webview

ASWP_TAB         = true;    // instead of default browser, open external URLs in chrome tab
ASWP_ADMOB       = false;   // enabled Google AdMob
```

### Security Variables

```kotlin
ASWP_CERT_VERIFICATION   = true   // verify whether HTTPS port needs certificate verification
```

### Other Variables

```kotlin
ASWV_ORIENTATION = 0;   // change device orientation to portrait (1)(default) or landscape (2) or unspecified (0)

ASWV_LAYOUT      = 0;   // default=0; for clear fullscreen layout and 1 to add drawer and navigation bar

// custom settings if layout `1` with search bar is set.
ASWV_SEARCH      = "https://www.google.com/search?q=";   // search query will start by the end of the present string

ASWV_SHARE_URL   = ASWV_URL+"?share=";   // URL where you process external content shared with the app
ASWV_EXC_LIST    = "";                   // domains allowed to be opened inside webview, separate domains with a comma (,)

ASWV_ADMOB       = "ca-app-pub-9276682923792397~7957851075";   // your unique publishers ID; this one is temporary

ASWV_F_TYPE      = "*/*"   // use `image/*` for image files only; check file type references for custom file type

POSTFIX_USER_AGENT      = true;     // set to true to append USER_AGENT_POSTFIX to user agent
OVERRIDE_USER_AGENT     = false;    // set to true to use USER_AGENT instead of default one
USER_AGENT_POSTFIX      = "SWVAndroid";    // useful for identifying traffic, e.g. in Google Analytics
CUSTOM_USER_AGENT       = "Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/59.0.3071.115 Mobile Safari/537.36";    // custom user-agent
```

## Features

### GPS Location

If `ASWP_LOCATION = true` then the app will start requesting GPS locations of the device on regular basis and all of the recorded data will be sent to the webpage in form of cookies, with updated live GPS locations.
```kotlin
COOKIE "lat" for latitude
COOKIE "long" for longitude
```

### Camera Input

You can either select to get input from both file manager and camera or can just choose camera to get image/video input. To get video input, add file type condition in your html input `video/*` and `image/*` for camera photos. By default `ASWV_F_TYPE` is set to `*/*` and suggested not to change instead file type should be provided on web pages end.

### Firebase Messaging

You need a firebase account to get started then download `google-services.json` and put it in the app level directory. Then you can create a POST request as below.
[See detailed steps](https://support.google.com/firebase/answer/7015592?hl=en) to download firebase config file.

**To URL:** `https://fcm.googleapis.com/fcm/send`

**Header:**
```
content-type:application/json
authorization:key=____server_key_here___ (Firebase > Settings > Cloud Messaging)
```

**Data:**
```
{ "notification": {
    "title": "___title_string___",
    "text": "___text_string___",
     "click_action": "Open_URI"
  },
    "data": {
    "uri": "___the_URL_where_you_want_users_to_send__"
    },
  "to" : "___user_token___"
}
```

You can get `___user_token___` from COOKIE `fcm_token`.

### Google AdMob

Enable `ASWP_ADMOB` to show ads, and get your App ID from AdMob to replace `ASWV_ADMOB`.

### Chrome Tab

With `ASWP_TAB` you handle external links to be opened in the chrome tab or external browser. More chrome tab customizations are available inside `MainActivity`.

### Content Sharing

User can share external content with your app like text, link or image. You can received data on your end by proving `ASWV_SHARE_URL`, an endpoint that can handle such requests. You can disable it by removing `.ShareActivity` from `Manifest`.

### User Interfaces

You can switch between clean and native interface with `ASWV_LAYOUT` where `0` represents full screen interface and `1` as a complete drawer layout with search option and navigation bar.

To customize drawer bar, you can look into `onNavigationItemSelected()` method in `MainActivity` and `activity_main_drawer.xml` for menu items.

### Rating System

Rating dialogue is enabled by default and can be handled by `ASWP_RATINGS`.

```
ASWR_DAYS            = 3;           // after how many days of usage would you like to show the dialog
ASWR_TIMES           = 10;          // overall request launch times being ignored
ASWR_INTERVAL        = 2;           // reminding users to rate after days interval
```

## Contributing

If you want to contribute to the project, you're most welcome to do so. Just:

- Fork it
- Create your feature branch `git checkout -b my-new-feature`
- Commit your changes `git commit -am 'Added some feature'`
- Push to the branch `git push origin my-new-feature`
- Create new Pull Request

## Support the Project

<!-- <img src="https://raw.githubusercontent.com/mgks/Android-SmartWebView/beta/res/swv_banner.jpg">-->

#### There are few ways to support this project -

**[GitHub Sponsors](https://github.com/sponsors/mgks):** Support this project and my other works by becoming a GitHub sponsor. Means a lot :)

**[Get Smart WebView Pro](https://mgks.dev/blog/smart-webview-pro):** You can support this project by getting a Pro variant of SWV also with additional features and plugins, some of the features/plugins include - PQL, Google Login, Vision API, and QR/Barcode Reader.

**[Join Discussions](https://github.com/mgks/Android-SmartWebView/discussions):** Feedbacks have helped this project become what it is today, share your honest feedback via [Discussion Board](https://github.com/mgks/Android-SmartWebView/discussions), [Email](mailto:hello@mgks.dev) or report your project [Issues](https://github.com/mgks/Android-SmartWebView/issues) here.

**[Follow Me](https://github.com/mgks) on GitHub** | **Add Project to Watchlist** | **Star the Project**

### Known Bugs
```
...
```
*Check [Issues](https://github.com/mgks/Android-SmartWebView/issues) tab for more.*

## License

This project is published under the MIT License - see [LICENSE](LICENSE) file for details or read [MIT license](https://opensource.org/licenses/MIT).


## Acknowledgements

- Rating method [Android-Rate](https://github.com/hotchemi/Android-Rate) is developed by [hotchemi](https://github.com/hotchemi)

Thanks to other [contributers](https://github.com/mgks/Android-SmartWebView/graphs/contributors) who helped make this project amazing.

## Closing Note

This project was initially developed by **[Ghazi Khan](https://mgks.dev)**, but coming this far wouldn't be possible without the people who contributed to this project.

For development consulting or other support. [Contact me!](mailto:hello@mgks.dev)

**A personal suggestion:** `You all must keep up with programming. It's sometimes difficult and sometimes easy but fun afterall, you can create your own world with programming and that's the beauty of it. So, all the best for your next creation.`

[![Profile](https://forthebadge.com/images/badges/built-with-love.svg)](https://mgks.dev)
