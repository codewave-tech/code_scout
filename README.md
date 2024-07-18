# CodeScout Logger

CodeScout is a versatile logging solution for Flutter applications, designed to facilitate debugging during development and provide valuable insights post-development through a desktop application using sockets. This logger is particularly useful for QA teams, allowing them to monitor logs related to network API calls, analytics, and other crucial information without requiring a debug connection.

## Features

- Configurable logging levels
- Console logging during development
- Socket-based logging for remote monitoring
- Support for various log types: development traces, debug logs, crashes, errors, and analytics

## Installation

Add the following dependency to your `pubspec.yaml` file:

```yaml
dependencies:
  code_scout: ^x.x.x # Replace with the latest version
```

## Usage

### Initialization

Before using CodeScout, initialize it with the desired configuration:

```dart
void main() {
  CodeScout.init(
    terimalLoggingConfigutation: CodeScoutLoggingConfiguration(
      devTraces: true,
      devLogs: true,
      networkCall: true,
      analyticsLogs: true,
      crashLogs: true,
      errorLogs: true,
      isDebugMode: true,
    ),
  );

  // Your app initialization code
}
```

### Logging

Use the following methods to log different types of messages:

```dart
// Development trace
CodeScout.logDevTrace("Development trace message");

// Debug log
CodeScout.logDebug("Debug message");

// Crash log
CodeScout.logCrash("Crash message", error: exception, stackTrace: stackTrace);

// Error log
CodeScout.logError("Error message", error: error);

// Analytics log
CodeScout.logAnalytics("Analytics event");
```

### Socket Logging

To enable socket-based logging for remote monitoring:

1. Implement the `CodeScoutSocketLogger` function:

```dart
void mySocketLogger(
  bool Function(CodeScoutLoggingConfiguration configuration) shouldLog,
  OutputEvent? outputEvent
) {
  // Implement your socket logging logic here
}
```

2. Bind the socket logger:

```dart
CodeScout.bindSocketLogger(mySocketLogger);
```

3. To stop socket logging:

```dart
CodeScout.unbindSocketLogger();
```

## Configuration

The `CodeScoutLoggingConfiguration` class allows you to customize the logging behavior:

- `devTraces`: Enable/disable development trace logs
- `devLogs`: Enable/disable debug logs
- `networkCall`: Enable/disable network call logs
- `analyticsLogs`: Enable/disable analytics logs
- `crashLogs`: Enable/disable crash logs
- `errorLogs`: Enable/disable error logs
- `isDebugMode`: Set to true for development, false for production

## Benefits for QA

- Real-time monitoring of application behavior
- Easy access to logs without debug connections
- Ability to track network API calls, analytics events, and errors
- Improved debugging and issue reproduction capabilities

## Note

Ensure that sensitive information is not logged in production environments. Always review and sanitize logs before sharing or storing them.

Would you like me to elaborate on any specific part of the documentation?
