# process_run.dart

Process run helpers for Linux/Win/Mac, which like feature

[![Build Status](https://travis-ci.org/tekartik/process_run.dart.svg?branch=master)](https://travis-ci.org/tekartik/process_run.dart)

## Goals

Currently using `Process.run` does not stream output which is not convenient for lengthy
operation. It requires using `Process.start` in a more complex way.

`run` and `runCmd` add verbose helper for that. Also dart binaries (pub, dart2js...) and any
script can be called consistently on Mac/Windows/Linux

`ProcessCmd` allow creating command object that can be run and modified.

## Usage

### process_run

Additional options to `Process.run` are
* specifying stdin
* making it verbose

Additional feature
* It tries to resolve simple command like `dart`, `firebase`, `flutter`, or any script available on the user path
  on any Platform.


### which

Like unix `which`, it searches for installed executables

```dart
var flutterExectutable = whichSync('flutter');
var firebaseExectutable = whichSync('firebase');

```

### Shell


Allows to run script from Mac/Windows/Linux in a portable way. Empty lines are added for lisibility

```dart
var shell = Shell();

await shell.run('''

# Display some text
echo Hello

# Display dart version
dart --version

# Display pub version
pub --version

''');
```

More information [on shell here](https://github.com/tekartik/process_run/blob/master/doc/shell.md)

### Additional features

Addtional features info are [available here](https://github.com/tekartik/process_run/blob/master/doc/more.md)

