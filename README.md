# SplashScreen
 SplashScreen demo
 Demo App for implementing multiple splash screens using different approaches
 
 # First Approach
As we all know splash screen is the user’s first experience of your application. It normally used to display some kind of progress before the application setup completely. As per Google material design spec, Splash Screen follows a pattern known called Launch Screen. You can find the specification here.
# Common Mistake
In most of the application developers use splash screen to showcase brand icon or picture for couple of seconds. This is common practice which most of the developers are following. It is not a good idea to use a splash screen that wastes a user’s time. This should be strictly avoided.
With the common approach you may also lead the problem of blank white page appears during splash launching.
# Right Way
The right way of implementing a splash screen is a little different. In the new approach specify your splash screen’s background as the activity’s theme background.
Also the root cause of blank white page problem is that your layout file is visible only after app has been initialized completely.
Do not create a layout file for splash activity. Instead, specify activity’s theme background as splash layout

# Second Approcah 
Adding animations to your android app makes it more fun and interesting as compared to static text or pictures. The easiest way to do that is using a 3rd party library  [LottieFiles](https://lottiefiles.com/blog/working-with-lottie/getting-started-with-lottie-animations-in-android-app) by airbnb.

# Third Approach
# Liquid Swipe

[![GitHub license](https://img.shields.io/badge/license-MIT-lightgrey.svg)](https://raw.githubusercontent.com/Cuberto/flashy-tabbar-android/master/LICENSE)

![Animation](https://raw.githubusercontent.com/Cuberto/liquid-swipe/master/Screenshots/animation.gif)

## Requirements

- Android 5.0+

## Example

To run the example project, clone the repo, and run `app`

### As library

#### GitHub Packages

Step 1 : Generate a Personal Access Token for GitHub
- Inside you GitHub account:
- Settings -> Developer Settings -> Personal Access Tokens -> Generate new token
- Make sure you select the following scopes (“ read:packages”) and Generate a token
- After Generating make sure to copy your new personal access token. You cannot see it again! The only option is to generate a new key.

Step 2: Store your GitHub — Personal Access Token details
- Create a github.properties file within your root Android project
- In case of a public repository make sure you add this file to .gitignore for keep the token private
- Add properties gpr.usr=GITHUB_USERID and gpr.key=PERSONAL_ACCESS_TOKEN
- Replace GITHUB_USERID with personal / organisation Github User ID and PERSONAL_ACCESS_TOKEN with the token generated in #Step 1

Step 3 : Update build.gradle inside the application module
- Add the following code to build.gradle inside the app module that will be using the library
```
    def githubProperties = new Properties()
    githubProperties.load(new FileInputStream(rootProject.file("github.properties")))
    repositories {
        maven {
            name = "GitHubPackages"

            url = uri("https://maven.pkg.github.com/Cuberto/liquid-swipe-android")
            credentials {
                /** Create github.properties in root project folder file with     
                ** gpr.usr=GITHUB_USER_ID & gpr.key=PERSONAL_ACCESS_TOKEN 
                ** Or set env variable GPR_USER & GPR_API_KEY if not adding a properties file**/
                username = githubProperties['gpr.usr'] ?: System.getenv("GPR_USER")
                password = githubProperties['gpr.key'] ?: System.getenv("GPR_API_KEY")
            }
        }
    }
```
- inside dependencies of the build.gradle of app module, use the following code
```
    dependencies {
        //consume library
        implementation 'com.cuberto:liquid-swipe:1.0.0'
        ....
    }
```
Sync project and now you can use flashytabbar library

## Usage

Add LiquidPager to your xml and use it like you would ViewPager

```

    <com.cuberto.liquid_swipe.LiquidPager
        android:id="@+id/pager"
        android:layout_width="match_parent"
        android:layout_height="match_parent" />
        
```

## iOS

Similar library [LiquidSwipe](https://github.com/Cuberto/liquid-swipe) by [Cuberto](https://github.com/Cuberto)

## Author

Cuberto Design, info@cuberto.com

## License

Liquid Swipe is available under the MIT license. See the LICENSE file for more info.

 <H4>Some helpful resources</H4>  
 https://stackoverflow.com/questions/61783132/lottie-animation-in-native-android-splash-screen
 https://www.youtube.com/watch?v=lyIbdU93vGU




