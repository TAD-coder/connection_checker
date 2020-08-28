# ConnectionChecker
Android library for checking the internet connectivity of a device.

## Add Dependencies:
Add the following in your project level build.gradle
```groovy
// ...
allprojects {
    repositories {
        // ...
        
        maven { url 'https://jitpack.io' }
    }
    // ...
}
```
and the following in your app level build.gradle
```groovy
dependencies {
    // ...
    implementation 'com.github.muddassir235:connection_checker:v1.1'
}
```

## Use The Library

Instantiate an object
```kotlin
val connectionChecker = ConnectionChecker(this, lifecycle)
```
Add connectivity listener
```kotlin
connectionChecker.connectivityListener = object: ConnectivityListener {
    override fun onConnected() {

    }

    override fun onConnectionSlow() {

    }

    override fun onDisconnected() {

    }
}
```
Start checking the connection.
```kotlin
connectionChecker.startChecking()
```

Example in an android activity.
```kotlin
class MainActivity : AppCompatActivity(), ConnectivityListener {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val connectionChecker = ConnectionChecker(this, lifecycle)
        connectionChecker.connectivityListener = this
        
        connectionChecker.startChecking()
    }

    override fun onConnected() {
        connection_status_tv.text = "Connected"
    }

    override fun onConnectionSlow() {
        connection_status_tv.text = "Slow Internet Connection"
    }

    override fun onDisconnected() {
        connection_status_tv.text = "Disconnected"
    }
}
```
