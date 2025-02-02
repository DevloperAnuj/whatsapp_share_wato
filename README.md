# Whatsapp Share Plugin

A Flutter plugin for IOS and Android providing a simple way to share a message, link or local files to specific WhatsApp contact.

## Features:

* null safe
* Share messages or link urls to specific contact.
* Share local files to specific contact.


## Installation

First, add this to your package's pubspec.yaml file:
```
dependencies:
  whatsapp_share2: ^2.0.0
```

Now in your Dart code, you can use:
```
import 'package:whatsapp_share2/whatsapp_share2.dart';
```
## Installation (Platform Specific)

### iOS

Add if not exists one row to the `ios/podfile` after target runner:

```
...

target 'Runner' do
    use_frameworks!

...
```

### Android

If you pretends to use the file share, you need to configure the file provider, this will give access to the files turning possible to share with other applications.

Add to `AndroidManifest.xml`:

```
<application>
...
<provider
    android:name="androidx.core.content.FileProvider"
    android:authorities="${applicationId}.provider"
    android:exported="false"
    android:grantUriPermissions="true">
    <meta-data
        android:name="android.support.FILE_PROVIDER_PATHS"
        android:resource="@xml/provider_paths"/>
</provider>
</application>
```
Obs: You can change the android:name if you have an extension of file provider.

Add `res/xml/provider_paths.xml`:

```
<?xml version="1.0" encoding="utf-8"?>
<paths xmlns:android="http://schemas.android.com/apk/res/android">
    <root-path name="root" path="." />
    <external-path name="external" path="." />
    <external-files-path name="external_files" path="." />
    <cache-path name="cache" path="." />
    <external-cache-path name="external_cache" path="." />
    <files-path name="files" path="." />
</paths>
```

If you want to learn more about file provider you can access:

  - https://developer.android.com/reference/android/support/v4/content/FileProvider

## How to use?

Here is an snippets app displaying the two whatsapp share methods .

### Whatsapp installed in this device ?

```Dart
 Future<void> isInstalled() async {
    final val = await WhatsappShare.isInstalled(
      package: Package.businessWhatsapp
    );
    print('Whatsapp Business is installed: $val');
  }
```
<small>If whatsapp is not installed, please do not call ```WhatsappShare.share()``` and ```WhatsappShare.shareFile()```
</small>


### Share text, links

```Dart

 Future<void> share() async {
    await WhatsappShare.share(
      text: 'Whatsapp share text',
      linkUrl: 'https://flutter.dev/',
      phone: '91xxxxxxxxxx',
    );
  }

```

### Share images, files

```_image1.path``` contains path of the file which is shared to the whatsapp.

```Dart

 Future<void> shareFile() async {
    await WhatsappShare.shareFile(
      text: 'Whatsapp share text',
      phone: '91xxxxxxxxxx',
      filePath: [_image1.path, _image2.path],
    );
  }

```"# whatsapp_share" 
"# whatsapp_share" 
"# whatsapp_share" 
"# whatsapp_share2" 
"# whatsapp_share null safe" 
