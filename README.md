This package provides lint rules for Dart and Flutter which are used at [Cidroy Technologies](https://cidroy.com). For more information on lint used in flutter, see the complete [list of options](https://dart.dev/tools/linter-rules).

Note: This package was heavily inspired by [very_good_anaylysis](https://github.com/VeryGoodOpenSource/very_good_analysis).

## Usage

To use the lints, add a dependency in your `pubspec.yaml`:

```yaml
# If you use `package:cidroy_analysis/cidroy_analysis.dart`, add a normal dependency.
dependencies:
  cidroy_analysis: ^0.0.3

# Or, if you just want `analysis_options.yaml`, it can be a dev dependency.
dev_dependencies:
  cidroy_analysis: ^0.0.3
```

Then, add an include in `analysis_options.yaml`: 

```yaml
include: package:cidroy_analysis/analysis_options.yaml
```

## Suppressing Lints

There may be cases where specific lint rules are undesirable. Lint rules can be suppressed at the line, file, or project level.

An example use case for suppressing lint rules at the file level is suppressing the `prefer_const_constructors` in order to achieve 100% code coverage. This is due to the fact that const constructors are executed before the tests are run, resulting in no coverage collection.

### Line Level

To suppress a specific lint rule for a specific line of code, use an `ignore` comment directly above the line:

```dart
// ignore: public_member_api_docs
class A {}
```

### File Level

To suppress a specific lint rule of a specific file, use an `ignore_for_file` comment at the top of the file:

```dart
// ignore_for_file: public_member_api_docs

class A {}

class B {}
```

### Project Level

To suppress a specific lint rule for an entire project, modify `analysis_options.yaml`:

```yaml
include: package:cidroy_analysis/analysis_options.yaml
linter:
  rules:
    public_member_api_docs: false
```
