---
title: "Firebase + Kotlin + Android"
date: 2019-01-25T11:58:37+05:30
tags: [firebase, kotlin, android, project, issues]
featured_image: '/images/kotlin_firebase.jpg'
description: "An overview of my first time connecting to Firebase Realtime Database"
draft: false
---

## Side Project 

While on vacation in India, I was given the opportunity to work on an Android app for my brother-in-law. The app would be for registering employees and would have time reporting functionality. His staff is less than 20 at the moment so I thought that Firebase would be a great utility for this project. 

## Firebase Overview

I learned about Firebase recently from a Udemy course that I am taking on Android Development. It is a Google product that has many features. In my project I will be primarily using the Realtime Database, Authentication, Analytics, and Cloud Storage.

## Let's try it with Kotlin!

At my job many teams use Kotlin. Funny enough, the Android team only codes in Java. Kotlin is very popular for Android development and I only knew the very basics of Kotlin coming into this project. I thought what better way to learn a language than to debug and google my way through it. 

## Butterknife + Kotlin = Don't need it

Butterknife is an Android library that allows the developer to bind the xml views to the Java/Kotlin code.

Without it you would do something like this:
```
val title : TextView = findViewbyId(R.id.title)
```
With it:
```
@BindView(R.id.title)
val title : TextView
```

So I began this project with all of the intentions of using Butterknife, but quickly found out that Kotlin is way too cool for that. As long as you have a plugin called kotlin-extensions then you are good to go.

In your app build.gradle add the plugin:
```
apply plugin: 'kotlin-android-extensions'
```

In any Activity or Fragment that has a corresponding xml you just need to add one import statement.

For example, in the class LoginActivity you would add:
```
import kotlinx.android.synthetic.main.activity_login.*
```

Now you have access to any elements in your xml by using their android:id.

So to add an onClickListener to a button with an id of "signIn_button" you would call the following:
```
signIn_button.setOnClickListener {
    // That's it!
}
```

## Firebase Connection Issues

[Please refer to the amazing Firebase documentation for clarity on the start up process](https://firebase.google.com/docs/android/setup)

So here are some facts about my situation which could lead to some issues:

* I am from the US and I am developing this app in India
* My laptop thinks it's still in the US (time not synced properly)
* I am staying in a house without Wifi (just hotspot)

So I went about using the Firebase Assistant in Android Studio. My application was not connecting properly to the Firebase instance I set up on the console. After much googling and debugging I found the root cause. My Mac laptop had the location locked in the United States. After turning on the location services it realized my local time was different. 

To properly debug in times of crisis like this make use of the Logcat tag "Firebase App". That definitely clued me into some problems. Also tailing the idea.log can be helpful to spot errors as well. My log file was located at ~/Library/Logs/AndroidStudio3.2 . Just enter the command
```
tail -f idea.log
```
and continue debugging the connection issue.

## Common Firebase Problems

After 3-4 days of researching and troubleshooting I now know how to correctly connect to Firebase. Here are a couple of things to make sure you do so you don't have the same trouble.

Please make sure before you start the connection your app has the following permission:
```
    <uses-permission android:name="android.permission.INTERNET"/>
```

Make sure your google-services.json file is in your app directory: 

![alt text](/images/google-services.jpg)

## Conclusion

In conclusion, Firebase is very easy to set up given the right circumstances. I made it a lot more difficult than it should have been. One good thing about having no wifi is it forces you to focus on the design part of your project. Happy coding!


