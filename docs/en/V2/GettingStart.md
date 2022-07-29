# Getting Started

Please make sure the React-Native version is higher than 0.50.0

Install command：
```
yarn add react-native-spring-scrollview
react-native link react-native-spring-scrollview
```

It is completed if you do not get an error. But for some reason, you should check your native installation

### Check native installation

##### iOS
* Make sure `ProjectPath ==> Libraries ==> RNSpringScrollView.xcodeproj` is in your project.
* Make sure `ProjectPath ==> TARGETS ==> BuildPhases ==> Link Binary With Libraries ==> libRNSpringScrollView.a` is linked to your project.

##### Android
* Make sure `YourProject/android/settings.gradle` contains the information below
```
include ':react-native-spring-scrollview'
project(':react-native-spring-scrollview').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-spring-scrollview/android')
```

* Make sure `YourProject/android/app/build.gradle` contains the information below
```
dependencies {
    compile project(':react-native-spring-scrollview')
    compile fileTree(include: ['*.jar'], dir: 'libs')
    compile 'com.android.support:appcompat-v7:26.0.0'
    compile 'com.facebook.react:react-native:+'
    // From node_modules
}
```

* Make sure `new SpringScrollViewPackage()` is in your `MainApplication.java`
```
@Override
protected List<ReactPackage> getPackages() {
    return Arrays.<ReactPackage>asList(
        new MainReactPackage(),
        new SpringScrollViewPackage()
    );
}
```

### iOS common installation problems
1. Can not find files `RCTXXXX.h`：

   [Click here to find a solution](https://github.com/facebook/react-native/issues/22000#issuecomment-438201084)

### Android common installation problems

1. Can not find files `android/drawable/XXXXXX`, '`android/res/XXXXXX`' ...

Check the compile SDK version is over API 26, or you can modify the version in react-native-spring-scrollview

Make sure `YourProject/android/app/build.gradle` contains google maven:
```
allprojects {
    repositories {
        mavenLocal()
        jcenter()
        maven {
            url 'https://maven.google.com'
        }
        maven {
            // All of React Native (JS, Obj-C sources, Android binaries) is installed from npm
            url "$rootDir/../node_modules/react-native/android"
        }
    }
}
```

