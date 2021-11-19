## AWS AugmentAbility

**AWS AugmentAbility** is a mobile web app which showcases 4 AWS AI services (Amazon Transcribe, Amazon Translate, Amazon Polly and Amazon Rekognition) and, at the same time, provides features that may benefit people with a visual or communication impairment, including difficulties in reading written text (text recognition), hearing (live transcription), speaking (text-to-speech), or having a conversation in a foreign language (voice-to-voice live translation).

### Main features
* **Real-time Conversation Translation**: select a target language, speak in your language, and the app will translate what you said in your target language. 
This feature is currently available in 9 languages (Chinese, English, French, German, Italian, Japanese, Korean, Portuguese, Spanish).
* **Live transcription and text-to-speech**: the app transcribes conversations and speeches for you, in real-time. Can't speak? Type what you want to say, and the app will say it for you. 
This feature is currently available in 9 languages (Chinese, English, French, German, Italian, Japanese, Korean, Portuguese, Spanish).
* **Live transcription and text-to-speech with translation**: the app transcribes and translates conversations and speeches for you, in real-time. Can't speak? Type what you want to say, and the app will translate and say it for you. You can benefit of translations in 70+ languages.
* **Object detection**: take a picture, and the app will describe the objects around you.
* **Text recognition for labels and signs**: point your camera at any label, sign or small chunk of text, and the app will read it out loud for you. AWS AugmentAbility can also translate the text into 70+ languages, or make it more readable for users with dyslexia by leveraging the OpenDyslexic font.
* **Text extraction from documents**: point your camera at any full-page document, and the app will read it out loud for you.  AWS AugmentAbility can also translate the text into 70+ languages, or make it more readable for users with dyslexia by leveraging the OpenDyslexic font.


### Solution architecture
![Solution architecture](https://github.com/aws-samples/aws-augmentability/raw/main/images/architecture.png)

## Phase 1: Pre-deployment steps

 1. Create a [Cognito Identity Pool] and take note of the *Cognito Identity pool ID* (https://docs.aws.amazon.com/cognito/latest/developerguide/tutorial-create-identity-pool.html)
 2. Navigate to *Identity and Access Management (IAM)* > *Roles*, find the *Unauth_Role* associated with the Cognito Identity Pool you created at step 1, and add the following inline policy to the role (change the value for the "aws:RequestedRegion" key to your preferred AWS region): 

.

    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Sid": "VisualEditor0",
                "Effect": "Allow",
                "Action": [
                    "transcribe:StartStreamTranscriptionWebSocket",
                    "translate:TranslateText",
                    "comprehend:DetectDominantLanguage",
                    "polly:SynthesizeSpeech",
                    "rekognition:DetectText",
                    "rekognition:DetectLabels",
                    "textract:DetectDocumentText"
                ],
                "Resource": "*",
                "Condition": {
                    "StringEquals": {
                        "aws:RequestedRegion": "eu-central-1"
                    }
                }
            }
        ] 
    }


 3. Clone the repository, create a file named "z-config.js" in the main folder, and paste the following code. Don't forget to replace INSERT_HERE_YOUR_COGNITO_IDENTITY_POOL with your *Cognito Identity pool ID*:

.

    var appConfig={
    'region' : 'eu-central-1',
    'IdentityPoolId' : 'INSERT_HERE_YOUR_COGNITO_IDENTITY_POOL' }
 

## Phase 2, option 1: building and deploying locally

 1. Complete Phase 1 (see above)
 2. run `npm install` (only first time)
 3. run `npm run-script build`
 4. run `npm install --global local-web-server` (only first time)
 5. run `ws`
 6. Open the index.html file in a browser


## Phase 2, option 2: building and deploying to AWS Amplify Console

 1. Complete Phase 1 (see above)
 2. Deploy to AWS Amplify Console (https://docs.aws.amazon.com/amplify/latest/userguide/getting-started.html)



## Acknowledgments and Credits

- amazon-archives/amazon-transcribe-websocket-static - Apache 2.0 License *
- ziniman/amazon-transcribe-websocket-static - Apache 2.0 License *
- aws-sdk - Apache 2.0 License
- bensonruan/webcam-easy - MIT License *
- department-stockholm/aws-signature-v4 - MIT License *
- jquery/jquery - MIT License
- browserify/browserify - MIT License
- lwsjs/local-web-server - MIT License
- microphone-stream/microphone-stream - MIT License
- sindresorhus/query-string -  MIT License
- babel/babel - MIT License
- babel/babelify - MIT License
- Semantic-Org/Semantic-UI - MIT License
- uikit/uikit - MIT License
- shoelace-style/shoelace - MIT License

- Font Awesome icons - CC BY 4.0 License
- Twemoji icons - CC BY 4.0 License
- Lordicon free icons - CC BY ND 4.0 License

\* In accordance with its license, this package was subject to some modifications (edited files available in the "lib" and "style" directories)


## Notices

This sample is provided for demonstration purposes only. Customers are responsible for making their own independent assessment of the information in this document and any use of AWS products or services, each of which is provided "as is" without warranty of any kind, whether express or implied.

AWS AugmentAbility is licensed under Apache License Version 2.0.



