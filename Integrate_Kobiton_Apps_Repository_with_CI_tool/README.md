# A. PREREQUISITE SETUP

Tools needed to run sample project:

* Install node: https://nodejs.org/en/download/

* Install node dependencies:

```bash
npm install
```

# B. HOW TO RUN SAMPLE

This sample contains 03 standalone scripts that demo 03 needs:

1. Upload app to Kobiton apps repo

2. Run app test for uploaded app

3. Get session logs and video download link

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

This sample will run one test using the uploaded app in #B1.

```bash
KOBITON_USERNAME=<YOUR_USERNAME> KOBITON_API_KEY=<YOUR_KOBITON_API_KEY> KOBITON_APP_ID=<YOUR_APP_ID> npm test
```

Sample output:

```bash
> app-repo-sample@1.0.0 test
> mocha --no-timeouts app-auto-test



  Android App sample
 > CALL init({"sessionName":"Apps Repo Demo","sessionDescription":"This is an example to demostrate Android apps repo","platformName":"android","deviceName":"Galaxy S6 Edge","app":"kobiton-store:9235"})
 > POST /session {"desiredCapabilities":{"sessionName":"Apps Repo Demo","sessionDescription":"This is an example to demostrate Android apps repo","platformName":"android","deviceName":"Galaxy S6 Edge","app":"kobiton-store:9235"}}
...

 Complete session 283949
```

In this sample output, the session ID is 283949.

## B3. Get session logs and video download link

This sample we will get the session info for previous executed session in #B2.

```bash
KOBITON_USERNAME=<YOUR_USERNAME> KOBITON_API_KEY=<YOUR_KOBITON_API_KEY> KOBITON_SESSION_ID=<YOUR_SESSION_ID> node get-session-info.js
```

Sample output:

```bash
https://kobiton-us-east.s3.amazonaws.com/sessions/230421/logs/230421-e6028540-2-11e8-9c42-db8f2a6e0840.zip?AWSAccessKeyId=&Signature=xxx&response-cache-control=max-age%3D86400
https://kobiton-us-east.s3.amazonaws.com/sessions/230421/videos/Video_230421-e7626360-2-11e8-a432-df734f4134ff.mp4?AWSAccessKeyId=xxxxx&Expires=xxxxx&Signature=xxx
```

It will return 2 links for logs and video to download.