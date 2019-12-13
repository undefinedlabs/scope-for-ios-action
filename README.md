![logo](scope_logo.svg)

# Scope for iOS Action

GitHub Action to run your tests automatically instrumented with the [Scope iOS agent](http://home.undefinedlabs.com/goto/ios-agent). It supports Xcode projects as well as Swift Package Manager packages.

## About Scope

[Scope](https://scope.dev) gives developers production-level visibility on every test for every app – spanning mobile, monoliths, and microservices.

## Usage

1. Set Scope DSN inside Settings > Secrets as `SCOPE_DSN`.

2. Add a step to your GitHub Actions workflow YAML that uses this action:

   ```yaml
   steps:
     - name: Checkout
       uses: actions/checkout@v1
     - name: Scope for iOS
       uses: undefinedlabs/scope-for-ios-action@v1
       with:
         dsn: ${{ secrets.SCOPE_DSN }} #required
   ```

   

## Configuration

These are the optional parameters of the action:

```yaml
workspace: .xcworkspace file, if not set workspace will be autoselected
project:  .xcodeproj file, if not set project will be autoselected
scheme: Scheme to test, if not set scheme will be autoselected
sdk:  Sdk used for building, by default: \"iphonesimulator\" will be used
destination: destination for testing, by default: 'platform=iOS Simulator,name=iPhone 11'

```

<!--For SPM packages, in the case of multiplatform projects, executable targets are not supported in iOS. Desabling targets per platform is still not supported in SPM, so in the meantime you can put a Package_iOS.swift beside de original Package.swift and the action will use this for building-->