# wallet-sdk-android 


[![Publish package CI](https://github.com/coming-chat/wallet-sdk-android/actions/workflows/gradle-publish.yml/badge.svg)](https://github.com/coming-chat/wallet-sdk-android/actions/workflows/gradle-publish.yml)
![GitHub release (latest by date)](https://img.shields.io/github/v/tag/coming-chat/wallet-sdk-android)

Android releases are hosted on [GitHub packages](https://github.com/coming-chat/wallet-sdk-android/packages/1670316), you need to add GitHub access token to install it. Please checkout [this installation guide](https://docs.github.com/en/packages/working-with-a-github-packages-registry/working-with-the-gradle-registry).

## Using

add `GITHUB_USER` and `GITHUB_TOKEN` to `local.properties`:

```
gpr.user=
gpr.key=
```

```
allprojects {
    repositories {
        // ...
        repositories {
            maven {
                Properties properties = new Properties()
                File localProps = new File(rootDir.absolutePath, "local.properties")
                if (localProps.exists()) {
                    properties.load(localProps.newDataInputStream())
                    println "Authenticating user: " + properties.getProperty("gpr.user")
                } else {
                    println "local.properties not found, please create it next to build.gradle and set gpr.user and gpr.key (Create a GitHub package read only + non expiration token at https://github.com/settings/tokens)\n" + "Or set GITHUB_USER and GITHUB_TOKEN environment variables"
                }
                url = uri("https://maven.pkg.github.com/coming-chat/wallet-sdk-android")
                credentials {
                    username = properties.getProperty("gpr.user") as String ?: System.getenv("GITHUB_USER")
                    password = properties.getProperty("gpr.key") as String ?: System.getenv("GITHUB_TOKEN")
                }
            }
        }
    }
}
```

```
implementation("org.comingchat:wallet-sdk-android:Tag")
```

> replace the `Tag` in the code with [latest](https://github.com/coming-chat/wallet-sdk-android/packages/1670316)



## Others

- [**Go**](https://github.com/coming-chat/wallet-SDK)
- [**IOS**](https://github.com/coming-chat/wallet-swift-package)
