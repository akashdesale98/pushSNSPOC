# Adding (FCM) Push Notifications to React Native Project

## Configuring Firebase Console 

1. Go to https://console.firebase.google.com/
2. Create Project 
3. Create App
4. Adding SHA key to your app - 
   1. Fire the command **gradlew signingReport** in your android folder of RN project
   2. Get the SHA key under debugtest point and use it while creating the app on the firebase console
5. Download google-services.json and add it into **android/app/google-services.json**
6. Follow the following sdk instructions
   * Project-level build.gradle (<project>/build.gradle):
        ```js
        buildscript {
          repositories {
            // Check that you have the following line (if not, add it):
            google()  // Google's Maven repository
          }
          dependencies {
            ...
            // Add this line
            classpath 'com.google.gms:google-services:4.3.4'
          }
        }

        allprojects {
          ...
          repositories {
            // Check that you have the following line (if not, add it):
            google()  // Google's Maven repository
            ...
          }
        }
        ```
    * App-level build.gradle (<project>/<app-module>/build.gradle):
        ```js
            apply plugin: 'com.android.application'
            // Add this line
            apply plugin: 'com.google.gms.google-services'

            dependencies {
              // Import the Firebase BoM
              implementation platform('com.google.firebase:firebase-bom:26.2.0')

              // Add the dependency for the Firebase SDK for Google Analytics
              // When using the BoM, don't specify versions in Firebase dependencies
              implementation 'com.google.firebase:firebase-analytics'

              // Add the dependencies for any other desired Firebase products
              // https://firebase.google.com/docs/android/setup#available-libraries
            }
        ```
7. Add the following RN dependecies - 
   1. @react-native-firebase/app
   2. @react-native-firebase/messaging
   3. react-native-push-notification 
