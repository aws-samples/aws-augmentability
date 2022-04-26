## AWS AugmentAbility

**AWS AugmentAbility** is a mobile web app which showcases 5 AWS AI services (Amazon Transcribe, Amazon Translate, Amazon Polly, Amazon Rekognition and Amazon Textract) and, at the same time, provides features that may benefit people with a visual or communication impairment, including difficulties in reading written text (text recognition), hearing (live transcription), speaking (text-to-speech), or having a conversation in a foreign language (voice-to-voice live translation).

### Main features
* **Live transcription and text-to-speech**: the app transcribes conversations and speeches for you, in real-time. Can't speak? Type what you want to say, and the app will say it for you. This feature also leverages Amazon Transcribe automatic language identification for streaming transcriptions: with a minimum of 3 seconds of audio, Transcribe can automatically detect the dominant language and generate transcript without having to specify the spoken language.
* **Live transcription and text-to-speech with translation**: the app transcribes and translates conversations and speeches for you, in real-time. Can't speak? Type what you want to say, and the app will translate and say it for you. Translation currently available in 75+ languages.
* **Real-time Conversation Translation**: select a target language, speak in your language, and the app will translate what you said in your target language.
* **Object detection**: take a picture with your smartphone, and the app will describe the objects around you.
* **Text recognition for labels, signs and documents**: take a picture with your smartphone of any label, sign or document, and the app will read it out loud for you. AugmentAbility can also translate the text into 75+ languages, or make it more readable for users with dyslexia by leveraging the OpenDyslexic font.

Live transcription, text-to-speech and real-time conversation translation features are currently available in Chinese, English, French, German, Italian, Japanese, Korean, Portuguese and Spanish. Text recognition features are currently available in Arabic, English, French, German, Italian, Portuguese, Russian and Spanish.


### Solution architecture
![Solution architecture](https://github.com/aws-samples/aws-augmentability/raw/main/images/architecture.jpg)

## Phase 1: Pre-deployment steps

 1. Create an Amazon Cognito user pool with Hosted UI enabled and an Amazon Cognito identity pool, integrate the two pools, and grant permissions for accessing AWS services to the IAM role associated with the identity pool. You can either complete this step by manually working on each task, or by deploying an AWS CloudFormation template (https://github.com/aws-samples/aws-augmentability/raw/main/template.yml). The CloudFormation template automatically provisions and configures the necessary resources, including the Cognito pools, IAM roles and IAM policies.
 
 2. Clone the repository, create a file named "config.js" in the main folder, and paste the following code:

.

    var appConfig = {
    "IdentityPoolId": "INSERT_COGNITO_IDENTITY_POOL_ID"
    }
    var amplifyConfig = {
        "Auth": {
            "region": "INSERT_AWS_REGION_ID",
            "userPoolId": "INSERT_COGNITO_USER_POOL_ID",
            "userPoolWebClientId": "INSERT_COGNITO_USER_POOL_CLIENT_ID",
            "mandatorySignIn": true,
            "cookieStorage": {
                "domain": window.location.hostname,
                "path": "/",
                "expires": 30,
                "secure": true
          }
        }
    }

3. In the config.js file you have created, replace the 4 “INSERT_” strings with the Cognito identity pool ID, the identifier of your Region of choice, the Cognito user pool ID, and the Cognito user pool Client ID. You can retrieve such values by accessing the AWS CloudFormation console, selecting the stack and choosing the Outputs tab. 
4. Before accessing the app for the first time, you will have to set a new password for the user that has been automatically created by the CloudFormation template. You can find the link to the temporary login screen in the CloudFormation stack Outputs tab. For this first sign-in, you will use the username and temporary password you received via email.
 

## Phase 2, option 1: building and deploying locally

 1. Complete Phase 1 (see above)
 2. run `npm install` (only first time)
 3. run `npm install --global local-web-server` (only first time)
 4. run `npm run-script build` (only first time, or in case of changes to JavaScript code)
 5. run `ws`
 6. Open the index.html file in a browser


## Phase 2, option 2: building and deploying to AWS Amplify Console

 1. Complete Phase 1 (see above)
 2. Deploy to the AWS Amplify Console (https://docs.aws.amazon.com/amplify/latest/userguide/getting-started.html). At Step 2a make sure to replace command `npm run build` with `npm run-script build`



## Acknowledgments and Credits

amazon-archives/amazon-transcribe-websocket-static * (Apache 2.0 License), ziniman/amazon-transcribe-websocket-static * (Apache 2.0 License), aws-sdk (Apache 2.0 License), aws-amplify/amplify-js (Apache 2.0 License), bensonruan/webcam-easy * (MIT License), department-stockholm/aws-signature-v4 * (MIT License), jquery/jquery (MIT License), browserify/browserify (MIT License), lwsjs/local-web-server (MIT License), microphone-stream/microphone-stream (MIT License), sindresorhus/query-string (MIT License), babel/babel (MIT License), babel/babelify (MIT License), Semantic-Org/Semantic-UI (MIT License), uikit/uikit (MIT License), shoelace-style/shoelace (MIT License), Font Awesome icons (CC BY 4.0 License), Twemoji icons (CC BY 4.0 License), Lordicon free icons (CC BY ND 4.0 License), terser/terser (BSD license).

\* In accordance with its license, this package was subject to some modifications (edited files available in the "lib" and "style" directories)


## Notices

This sample is provided for demonstration purposes only. Customers are responsible for making their own independent assessment of the information in this document and any use of AWS products or services, each of which is provided "as is" without warranty of any kind, whether express or implied.

AWS AugmentAbility is licensed under Apache License Version 2.0.



