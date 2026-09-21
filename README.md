# ReVanced / Morphe Custom Builder

A customized GitHub Actions-based builder for creating patched Android apps using **ReVanced/Morphe patches**.

This repository is configured to build selected apps independently, allowing different patch sources and configurations for each application.

### Supported Apps

| App           | Package                                 |
| ------------- | --------------------------------------- |
| YouTube       | `com.google.android.youtube`            |
| YouTube Music | `com.google.android.apps.youtube.music` |
| Instagram     | `com.instagram.android`                 |
| Google Photos | `com.google.android.apps.photos`        |

##  Features

*  Automated builds through **GitHub Actions**
*  Builds patched APKs automatically
*  Automatically fetches the required app versions
*  Supports different patch sources/configurations per app
*  Separate configurations for YouTube, YouTube Music, Instagram and Google Photos
*  Uses ReVanced/Morphe CLI and patches
*  Downloads required prebuilts automatically
*  Build configuration is controlled through repository config files
*  Can be scheduled for automatic builds
*  Release artifacts can be published through GitHub Releases

## Apps

### YouTube

Package:

```text
com.google.android.youtube
```

YouTube is built using the configured **Morphe/ReVanced patch set** and CLI.

### YouTube Music

Package:

```text
com.google.android.apps.youtube.music
```

YouTube Music uses its own configuration and patching setup.

### Instagram

Package:

```text
com.instagram.android
```

Instagram is patched using the configured patch source specifically intended for the application.

### Google Photos

Package:

```text
com.google.android.apps.photos
```

Google Photos is built independently using its corresponding configuration and patches.

---

##  How It Works

The build process is handled by GitHub Actions.

At a high level:

```text
GitHub Actions
      │
      ├── Fetch configuration
      │
      ├── Download required APK
      │
      ├── Download CLI / patches
      │
      ├── Apply selected patches
      │
      ├── Build patched APK
      │
      └── Publish build artifacts / release
```

Different applications can use different patch sources and configurations, allowing the repository to maintain independent build setups instead of forcing every application through the same patch set.

##  Patch Sources

The YouTube and YouTube Music builds use the **Morphe** ecosystem:

* Patches: `MorpheApp/morphe-patches`
* CLI: `MorpheApp/morphe-cli`

The exact versions of the applications and patches are determined by the repository configuration and workflow.

## 🔧 Configuration

Build configuration is stored in the repository configuration files.

Depending on the build, the repository can be invoked with:

```bash
./build.sh config.json
```

or:

```bash
./build.sh config.toml
```

This allows each application to have its own build configuration, including:

* Target APK
* Package name
* Patch source
* CLI source
* Selected patches
* APK download source
* Output configuration

##  GitHub Actions

The primary build environment is **GitHub Actions**.

Workflows can be triggered manually or configured to run automatically.

Typical workflow:

```text
Workflow
   ↓
Prepare environment
   ↓
Load application configuration
   ↓
Download APK
   ↓
Download CLI / patches
   ↓
Patch APK
   ↓
Verify build
   ↓
Upload artifact / create release
```

Build outputs can be downloaded directly from the corresponding GitHub Actions run or from **Releases**, depending on the workflow configuration.

##  Building Locally

Clone the repository:

```bash
git clone https://github.com/Ravi-Kishor/Revanced-Extended.git --depth 1
cd Revanced-Extended
```

Make the build script executable if required:

```bash
chmod +x build.sh
```

Then run the desired configuration:

```bash
./build.sh config.json
```

or:

```bash
./build.sh config.toml
```

##  Output

Successfully patched applications are generated as APKs and can be collected from the build output directory.

When using GitHub Actions, the workflow can also upload the generated APKs as workflow artifacts or attach them to a GitHub Release.

## ⚠️ Disclaimer

This repository is an **unofficial community/custom build setup**.

It is not affiliated with or endorsed by:

* Google
* YouTube
* Instagram
* Google Photos
* ReVanced
* Morphe
* Meta

Use the builds at your own discretion.

## 📜 Credits

This project builds upon the work of the open-source Android patching community.

Special thanks to the developers and contributors behind:

* ReVanced
* Morphe
* ReVanced CLI
* Morphe CLI
* ReVanced/Morphe patches
* The original Magisk Module builder

---


