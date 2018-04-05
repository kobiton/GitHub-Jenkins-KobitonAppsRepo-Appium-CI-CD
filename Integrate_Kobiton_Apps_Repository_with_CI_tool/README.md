# A. PREREQUISITE SETUP

`node` & `yarn` are required to use this sample.

You can install Yarn through the Homebrew package manager. This will also install Node.js if it is not already installed.

```bash
brew install yarn
```

Then, install node dependencies for the sample project:

```bash
npm install
```

```bash
yarn install
```

# B. HOW TO RUN SAMPLE

This sample contains 03 standalone scripts that demo 03 needs:

* Upload app to Kobiton apps repo

* Run app test for uploaded app

* Get session logs and video download link

They will need your API key value which you can get at: https://portal.kobiton.com/settings/keys


## B1. Upload app to Kobiton apps repo

This sample will upload `apps/ContactManager.apk` file to apps repo and show the app ID of this app.

```bash
KOBITON_USERNAME=<YOUR_USERNAME> KOBITON_API_KEY=<YOUR_KOBITON_API_KEY> node upload-app.js apps/ContactManager.apk ContactManager.apk
```

Sample output:

```bash
7441
```

In this sample output, the App ID is 7441.

## B2. Run app test for uploaded app

This sample will open the app to prove that this app was uploaded and testable.

```bash
KOBITON_USERNAME=<YOUR_USERNAME> KOBITON_API_KEY=<YOUR_KOBITON_API_KEY> KOBITON_APP_ID=<YOUR_APP_ID> yarn test
```

Sample output:

```bash
yarn run v1.5.1
$ mocha --no-timeouts app-auto-test
...
Complete session 230421
```

In this sample output, the session ID is 230421.

## B3. Get session logs and video download link

This sample we will get the session info of a completed session.

```bash
KOBITON_USERNAME=<YOUR_USERNAME> KOBITON_API_KEY=<YOUR_KOBITON_API_KEY> KOBITON_SESSION_ID=<YOUR_SESSION_ID> node get-session-info.js
```

Sample output:

```bash
https://kobiton-us-east.s3.amazonaws.com/sessions/230421/logs/230421-e6028540-2-11e8-9c42-db8f2a6e0840.zip?AWSAccessKeyId=AKIAJ7BONOZUJZMWR4WQ&Expires=1521066840&Signature=h4WCg6mdoB1Un%2F2%2BcmZ2nAkJtS8%3D&response-cache-control=max-age%3D86400
https://kobiton-us-east.s3.amazonaws.com/sessions/230421/videos/Video_230421-e7626360-2-11e8-a432-df734f4134ff.mp4?AWSAccessKeyId=AKIAJ7BONOZUJZMWR4WQ&Expires=1521066840&Signature=U0SPwOs%2FTkYjuEVk7sb%2F4agpBtY%3D
```

It will return 2 links for logs and video for you to download.