# content_resolver

The plugin is to resolve Android's content URI that is often used by [Content providers](https://developer.android.com/guide/topics/providers/content-providers).

## Install

Add this to your package's pubspec.yaml file and execute flutter pub get:

```yaml
dependencies:
  content_resolver: ^0.3.0
```

## Usage

### Resolving content

The following fragment is a use case with [app_links](https://pub.dev/packages/app_links) to receive `content:...` URI content:

```dart
_appLinks = AppLinks(onAppLink: (uri) async {
  // If the data is some image, you can pass the data directly to Image.data or something.
  final Content content = await ContentResolver.resolveContent(uri);
  ...
});
```

### Writing content

The following fragment illustrates how to write data to `content:...` URI:

```dart
  final data = Uint8List.fromList(utf8.encode('Hello World'));
  await ContentResolver.writeContent(uri.toString(), data);
  ...
```

Please note that if the URI is not writable, the code throws certain exception.
