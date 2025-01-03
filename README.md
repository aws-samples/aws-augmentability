## AWS AugmentAbility

***This is an experimental fork of the [AWS AugmentAbility project](https://aws.amazon.com/blogs/machine-learning/use-aws-ai-and-ml-services-to-foster-accessibility-and-inclusion-of-people-with-a-visual-or-communication-disability/) in which some of the vision capabilities have been re-implemented to leverage multi-modal Generative AI models through Amazon Bedrock instead of Amazon Rekognition.***

**AWS AugmentAbility** is a mobile web app which showcases 5 AWS AI/ML services (Amazon Transcribe, Amazon Translate, Amazon Polly, **Amazon Bedrock** and Amazon Textract) and, at the same time, provides features that may benefit people with a visual or communication impairment, including difficulties in reading written text (text recognition), hearing (live transcription), speaking (text-to-speech), or having a conversation in a foreign language (voice-to-voice live translation).

### Main features
* **Live transcription & text-to-speech**: the app transcribes conversations and speeches for you, in real-time. Can't speak? Type what you want to say, and the app will say it for you. This feature is currently available in Arabic, Catalan, Chinese, Czech, Danish, English (Australia, UK, India, New Zealand, South Africa, US), Finnish, French (France, Canada), German (Germany, Switzerland), Hindi, Italian, Japanese, Korean, Polish, Portuguese (Portugal, Brazil), Romanian, Russian, Spanish (Spain, US), and Swedish.
* **Live transcription & text-to-speech with translation**: the app transcribes and translates conversations and speeches for you, in real-time. Can't speak? Type what you want to say, and the app will translate and say it for you. Translation currently available in 75+ languages.
* **Real-time Conversation Translation**: select a target language, speak in your own language, and the app will translate what you say in the target language. This feature is currently available in Arabic, Catalan, Chinese, Czech, Danish, English (Australia, UK, India, New Zealand, South Africa, US), Finnish, French (France, Canada), German (Germany, Switzerland), Hindi, Italian, Japanese, Korean, Polish, Portuguese (Portugal, Brazil), Romanian, Russian, Spanish (Spain, US), and Swedish.
* 🆕 **Scene description and Visual Q&A**: take a picture with your smartphone, and the app will describe the objects around you by leveraging Anthropic Claude 3 Haiku's vision capabilites via Amazon Bedrock. If you enable <b>Q&A mode</b>, the app will also be able to answer your questions based on what's around.
* **Text extraction from documents**: point your camera at any full-page document, and the app will read it out loud for you. AugmentAbility can also translate the text into 75+ languages, or make it more readable for users with dyslexia by leveraging the OpenDyslexic font.

### Supported languages 
* **Live transcription & text-to-speech**, **Real-time Conversation Translation**, **Scene description and Visual Q&A** features are currently available in Arabic, Catalan, Chinese, Czech, Danish, English (Australia, UK, India, New Zealand, South Africa, US), Finnish, French (France, Canada), German (Germany, Switzerland), Hindi, Italian, Japanese, Korean, Polish, Portuguese (Portugal, Brazil), Romanian, Russian, Spanish (Spain, US), and Swedish. 
* The **Live transcription & text-to-speech with translation** feature is currently available in the following 75 languages supported by Amazon Translate: Afrikaans, Albanian, Amharic, Arabic, Armenian, Azerbaijani, Bengali, Bosnian, Bulgarian, Chinese (Simplified), Catalan, Chinese (Traditional), Croatian, Czech, Danish, Dari, Dutch, English, Estonian, Finnish, French, French Canadian, Georgian, German, Greek, Gujarati, Haitian Creole, Hausa, Hebrew, Hindi, Hungarian, Icelandic, Indonesian, Irish, Italian, Japanese, Kannada, Kazakh, Korean, Latvian, Lithuanian, Macedonian, Malay, Malayalam, Maltese, Mongolian, Marathi, Norwegian, Farsi (Persian), Pashto, Polish, Portuguese, Portuguese Portugal , Punjabi, Romanian, Russian, Serbian, Sinhala, Slovak, Slovenian, Somali, Spanish, Spanish Mexican, Swahili, Swedish, Filipino Tagalog, Tamil, Telugu, Thai, Turkish, Ukrainian, Urdu, Uzbek, Vietnamese, and Welsh. 
* The **Text extraction from documents** feature is currently available in English, French, German, Italian, Portuguese, Russian and Spanish.

### Supported regions
Make sure to launch the solution in a AWS Region in which all the AWS services and models in scope (Amazon Cognito, AWS Amplify, Amazon Transcribe, Amazon Polly, Amazon Translate, Amazon Bedrock > Anthropic Claude 3 Haiku, and Amazon Textract) are available (us-east-1, us-west-2, ap-south-1, ap-northeast-2, ap-southeast-2, ca-central-1, eu-central-1, eu-west-2). To select the region, use the Region selector in the console navigation bar. To use Amazon Polly Neural voices, launch the solution in one of the following regions: us-east-1, us-west-2, ap-northeast-2, ap-south-1, ap-southeast-2, ca-central-1, eu-central-1, eu-west-2. To use Amazon Polly Generative voices, launch the solution in one of the following regions: us-east-1, us-west-2, eu-central-1.

### Solution architecture
![Solution architecture](https://github.com/aws-samples/aws-augmentability/raw/bedrock/images/architecture.jpg)


### Changelog
* Object detection & text extraction features (Nov 2021)
* Amazon Polly Neural voices (Nov 2021)
* Performance improvements - Terser JavaScript compression (Dec 2021)
* New languages in text translation features - Irish, Marathi, Portuguese Portugal, and Punjabi (Mar 2022)
* Arabic support in text detection features  (Mar 2022)
* Automatic language identification for streaming transcriptions (Mar 2022)
* Improved authentication logic (Apr 2022)
* CloudFormation template for automatic deployment (Apr 2022)
* 3 new Amazon Polly Neural voices: Canadian French, German, US Spanish (Jun 2022)
* Improved UX for ASR and TTS features (Sep 2022)
* 3 new Amazon Polly Neural voices: Hindi, Indian English, Mandarin Chinese (Sep 2022)
* Various fixes and dependency upgrades (2023)
* Hindi support in live transcription, text-to-speech and conversation translation features; Amazon Polly integration enhancements (Jul 2024)
* Image upload support in text extraction from documents feature (Jul 2024)
* Support for additional ASR and TTS languages in Live transcription & text-to-speech, Live transcription & text-to-speech with translation, and Real-time Conversation Translation features (Dec 2024)
* Support for Amazon Polly Generative voices and additional Neural voices (Dec 2024)
* New **Scene description and Visual Q&A** features powered by Anthropic Claude 3 Haiku's vision capabilites via Amazon Bedrock (Jan 2025)


### Deployment options

#### Preconditions: enable access to Anthropic Claude 3 Haiku in Amazon Bedrock in your region of choice
Follow the steps described in [this web page](https://docs.aws.amazon.com/bedrock/latest/userguide/model-access-modify.html) to enable access to Anthropic Claude 3 Haiku in Amazon Bedrock in your region of choice

#### Option 1: building and deploying AWS AugmentAbility to the AWS Amplify Console

Follow the steps described in [this blog post](https://aws.amazon.com/blogs/machine-learning/use-aws-ai-and-ml-services-to-foster-accessibility-and-inclusion-of-people-with-a-visual-or-communication-impairment/)

🆕 At Step 1.1, manually download the template available at [this link](https://raw.githubusercontent.com/aws-samples/aws-augmentability/refs/heads/bedrock/template.yml), navigate to [this web page](https://console.aws.amazon.com/cloudformation/home?region=eu-central-1#/stacks/new?stackName=augmentability-bedrock-stack), choose `Upload a template file` and upload the template.yml file. At Step 2.1, clone the repository from [this link](https://github.com/aws-samples/aws-augmentability/tree/bedrock).

#### Option 2: building and deploying AWS AugmentAbility locally

 1. Follow Step 1 and 2 (Create the Amazon Cognito user pool and identity pool, and grant permissions for accessing AWS AI services; Clone the GitHub repository and edit the configuration file) from [this blog post](https://aws.amazon.com/blogs/machine-learning/use-aws-ai-and-ml-services-to-foster-accessibility-and-inclusion-of-people-with-a-visual-or-communication-impairment/)

 🆕 At Step 1.1, manually download the template available at [this link](https://raw.githubusercontent.com/aws-samples/aws-augmentability/refs/heads/bedrock/template.yml), navigate to [this web page](https://console.aws.amazon.com/cloudformation/home?region=eu-central-1#/stacks/new?stackName=augmentability-bedrock-stack), choose `Upload a template file` and upload the template.yml file. At Step 2.1, clone the repository from [this link](https://github.com/aws-samples/aws-augmentability/tree/bedrock).


 2. run `npm install` (only first time)
 3. run `npm install --global local-web-server` (only first time)
 4. run `npm run-script build` (only first time, or in case of changes to JavaScript code)
 5. run `ws`
 6. Before accessing the app for the first time, you have to set a new password for the user that has been automatically created during Step 1. You can find the link to the temporary login screen in the Outputs tab for the CloudFormation stack (field UserPoolLoginUrl). For this first sign-in, you use the user name you set up and the temporary password you received via email. After you set your new password, you’re ready to test the mobile web app by opening the index.html file in a browser.


### Acknowledgments and Credits

amazon-archives/amazon-transcribe-websocket-static * (Apache 2.0 License), ziniman/amazon-transcribe-websocket-static * (Apache 2.0 License), aws-sdk (Apache 2.0 License), bensonruan/webcam-easy * (MIT License), department-stockholm/aws-signature-v4 * (MIT License), jquery/jquery (MIT License), browserify/browserify (MIT License), lwsjs/local-web-server (MIT License), microphone-stream/microphone-stream (MIT License), sindresorhus/query-string (MIT License), babel/babel (MIT License), babel/babelify (MIT License), Semantic-Org/Semantic-UI (MIT License), uikit/uikit (MIT License), shoelace-style/shoelace (MIT License), Font Awesome icons (CC BY 4.0 License), Twemoji icons (CC BY 4.0 License), Lordicon free icons (CC BY ND 4.0 License), terser/terser (BSD license).

\* In accordance with its license, this package was subject to some modifications (edited files available in the "lib" and "style" directories)


### Notices

This sample is provided for demonstration purposes only; it is not meant for production deployments as is. Customers are responsible for making their own independent assessment of the information in this document and any use of AWS products or services, each of which is provided "as is" without warranty of any kind, whether express or implied.

AWS AugmentAbility is licensed under Apache License Version 2.0.



