# ZMCKit

ZMCKit is an Android library that simplifies the integration of camera functionalities in your applications. This library is designed to work seamlessly with the CameraActivity for capturing images and videos.

## Table of Contents
- [Installation](#installation)
- [Usage](#usage)
- [License](#license)

## Installation

### Step 1: Add the Repository

Add the following Maven repository to your project-level `build.gradle` file:

```groovy
allprojects {
    repositories {
        google()
        mavenCentral()
        maven {
            url "https://raw.githubusercontent.com/arbabkh/ZMCKit-Android/main/"
        }
    }
}
```

### Step 2: Add the Dependency

In your app-level `build.gradle` file, add the following dependency:

```groovy
dependencies {
    implementation 'com.snap:zmckit:1.0.0' // Update the version as necessary
}
```

## Usage

### Step 1: Initialize ZMCKitManager

In your main activity or wherever you want to use the camera functionality, initialize the `ZMCKitManager`:

```kotlin
import com.snap.zmckit.ZMCKitManager

class MainActivity : AppCompatActivity() {

    private lateinit var zmckitManager: ZMCKitManager

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        zmckitManager = ZMCKitManager()
        zmckitManager.init(
            cameraKitApiToken = BuildConfig.CAMERA_KIT_API_TOKEN,
            cameraKitApplicationId = "", // Your application ID
            lensGroupIds = LENS_GROUP_IDS // Your lens group IDs
        )
    }
}
```

### Step 2: Open the Camera

To open the camera, call the `openCamera` method:

```kotlin
zmckitManager.openCamera()
```

### Step 3: Handle Camera Results

Implement the callback to handle the camera results:

```kotlin
override fun onActivityResult(requestCode: Int, resultCode: Int, data: Intent?) {
    super.onActivityResult(requestCode, resultCode, data)
    zmckitManager.handleCameraResult(requestCode, resultCode, data)
}
```

### Example

Here’s a complete example of how to use the `ZMCKit` library in an activity:

```kotlin
class MainActivity : AppCompatActivity() {
    
    private lateinit var zmckitManager: ZMCKitManager

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        zmckitManager = ZMCKitManager()
        zmckitManager.init(
            cameraKitApiToken = BuildConfig.CAMERA_KIT_API_TOKEN,
            cameraKitApplicationId = "",
            lensGroupIds = LENS_GROUP_IDS
        )

        // Button click to open camera
        findViewById<Button>(R.id.openCameraButton).setOnClickListener {
            zmckitManager.openCamera()
        }
    }

    override fun onActivityResult(requestCode: Int, resultCode: Int, data: Intent?) {
        super.onActivityResult(requestCode, resultCode, data)
        zmckitManager.handleCameraResult(requestCode, resultCode, data)
    }
}
```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

---

### Additional Notes
- **Customization**: Feel free to customize the README with additional sections, such as Features, Contributing, or FAQ, as needed.
- **Usage Examples**: If you have specific examples or configurations, include them to help users understand how to utilize your library effectively.
- **Badges**: Consider adding badges (like build status, license, etc.) at the top of your README for better visibility.

Once you have this README drafted, you can save it in the root of your repository as `README.md`. This will provide users with a clear guide on how to use your `ZMCKit` library. Let me know if you need any further help!
