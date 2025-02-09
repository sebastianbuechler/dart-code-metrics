# Ban name

## Rule id {#rule-id}

ban-name

## Severity {#severity}

Style

## Description {#description}

Configure some names that you want to ban.

Example: When you add some extra functionalities to built-in Flutter functions (such as logging for `showDialog`), you may want to ban the original Flutter function and use your own version.

Limitation: When trying to ban some methods in your package, it also triggers on imported from an external package code.

### Example {#example}

Bad:

```dart
// suppose the configuration is the one shown below

showDialog('some_arguments', 'another_argument'); // LINT
material.showDialog('some_arguments', 'another_argument'); // LINT

var strangeName = 42; // LINT

void strangeName() {} // LINT

// LINT
class AnotherStrangeName {
  late var strangeName; // LINT
}
```

Good:

```dart
myShowDialog();
```

### Config example {#config-example}

```yaml
dart_code_metrics:
  ...
  rules:
    ...
    - ban-name:
        entries:
        - ident: showDialog
          description: Please use myShowDialog in this package
        - ident: strangeName
          description: The name is too strange
        - ident: AnotherStrangeName
          description: Oops
```
