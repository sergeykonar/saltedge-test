![SDK Version](https://img.shields.io/badge/SDK%20version-3.5.0-orange)

<p align="center">
  <a href="https://www.saltedge.com/products/spectre">
    <img src="https://raw.githubusercontent.com/saltedge/sca-identity-service-example/master/docs/images/saltedge_logo.png" alt="Salt Egde Logo" width="96" height="96">
  </a>
</p>

# Salt Edge Android SDK & Sample application

Salt Edge Android SDK provides [a handful of classes](SDK_GUIDE.MD) to help you interact with the Salt Edge API from your Android app.  
  
### Current SDK supports access only to [Salt Edge API v5](https://docs.saltedge.com/account_information/v5/).  
### [Salt Edge Partner API](https://docs.saltedge.com/partners/v1/) is not supported.  
### When you migrating to the new version of Salt Edge Android SDK, please read carefully [CHANGELOG](CHANGELOG.MD) since many changes have been made.

## Requirements

* JDK 8
* Android SDK (minimal sdk version - Android 4.0.2 (15))
* Play Services installed
* `App ID` and `App Secret`

**Warning!** The Salt Edge SDK doesn't work without `App ID` and `App Secret`!
*Note*: You can find your `App ID` and `App Secret` on your [profile](https://www.saltedge.com/keys_and_secrets) page.

## Source

Clone this repository
```shell
$ git clone git@github.com:saltedge/saltedge-android.git
```

## How to build sample

1. Fork this repository
1. Import project as Gradle project in Android Studio
1. Replace the `clientAppId`, `clientAppSecret` constants in `SampleApplication.java` with your `App ID` and `App Secret`.

1. Build and run application on target device or emulator

*Note*: You can find your `App ID` and `App Secret` on your [profile](https://www.saltedge.com/keys_and_secrets) page.

## How to add SDK to your project

### Add Java 8 support to application `build.gradle`
   
```groovy
android {
    compileOptions {
        sourceCompatibility JavaVersion.VERSION_1_8
        targetCompatibility JavaVersion.VERSION_1_8
    }
}
```
  
### Add maven repository to application `build.gradle`
   
```groovy
repositories {
    maven {
        url 'https://raw.github.com/saltedge/saltedge-android/master/repo/'
    }
}
```

### Add SDK dependency to application `build.gradle`
  
```groovy
implementation ('com.saltedge.sdk:saltedge-library:X.X.X@aar') {
    transitive = true
}
```

## [SDK Guide](SDK_GUIDE.MD)

## [How To](HOW_TO.MD) 

## [SDK Changelog](CHANGELOG.MD)

## Useful references
1. [Salt Edge API](https://docs.saltedge.com/account_information/v5/)
1. [Salt Edge Connect Guide](https://docs.saltedge.com/account_information/v5/#salt_edge_connect)

## Contacts 
For more information, feel free to [contact us](https://www.saltedge.com/pages/contact)
  
## [LICENSE](LICENSE)

---
Copyright © 2014 Salt Edge Inc. https://www.saltedge.com
