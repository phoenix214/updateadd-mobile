## Get Started

### System Requirements

* Globally install [react-native CLI](https://facebook.github.io/react-native/docs/getting-started.html)

* Install [Yarn](https://yarnpkg.com/lang/en/docs/install/): `brew install yarn`


### Installation

On the command prompt run the following commands

```sh
yarn

react-native link
```

### Run on iOS

*	Run `react-native run-ios` or `yarn ios` in your terminal

### Run on Android

*	Run `react-native run-android` or `yarn android` in your terminal

### Integrate with [CodePush](https://github.com/Microsoft/react-native-code-push)

* Create an app on [ClearSummit's Mobile Center](https://mobile.azure.com/apps) to get deployment keys. We should have a separate app for iOS and Android.

> Below steps can be done through App Center's Dashboard

* Generate deployment keys: `code-push deployment add <app_name> "Staging or Production"`

* View deployment keys: `code-push deployment ls <app_name> -k`

* iOS: [muti-deployment testing doc](https://github.com/Microsoft/react-native-code-push/blob/master/docs/multi-deployment-testing-ios.md) Do step 9.

* Android: [muti-deployment testing doc](https://github.com/Microsoft/react-native-code-push/blob/master/docs/multi-deployment-testing-android.md) Do step 2.

### Integrate to [ClearSummit's Sentry](https://sentry.io/auth/login/ClearSummit/)

* Create a new project in Sentry

* Run `react-native link react-native-sentry` and follow instructions. Check out [documents](https://docs.sentry.io/clients/react-native/)

* Go to Project Settings -> Client Keys -> Copy and paste the DNS url to `SentryUtil.configure('')` in App.js

### Support multiple environments

* Change `API_URL` string in `.env`, `.env.staging`, `.env.production`

* Android: problems with Proguard? Check this [link](https://github.com/luggit/react-native-config#problems-with-proguard) out.

### Integrate CodeClimate for test report

* Change `<token here>` in `.circleci/config.yml` file with Code Climate's repo token

### Support visual regression test on CI

* Make sure circleci is running with macOS plan

* Modify `.circleci/config.yml` by uncommenting the commented lines and removing these:
```sh
docker:
    - image: circleci/node:10.10.0

curl -L https://codeclimate.com/downloads/test-reporter/test-reporter-latest-linux-amd64 > /tmp/cc-test-reporter
```

* Run `reg-suit init --use-yarn` to re-install and re-configure reg-suit and plugins into our project. Check out [documents](https://github.com/reg-viz/reg-suit)


## Writing contacts

### Load contacts
- [DANGER] Method removes information.  We have a debug sample of contacts which can be loaded onto the device, through the debug menu.  This will *clear* your contacts and load in our contacts.  Only use on test devices
