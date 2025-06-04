---
title: Text-to-Speech Quickstart
description: Get started with Sarvam AI Speech Models
icon: lightbulb
---

<p
  style={{
    fontSize: "1.5rem",
    fontWeight: "500",
    lineHeight: "1.4",
    marginBottom: "1.5rem",
  }}
>
  Sarvam AI offers a powerful text-to-speech model:
</p>

<div
  style={{
    display: "grid",
    gridTemplateColumns: "repeat(auto-fit, minmax(300px, 1fr))",
    gap: "1.5rem",
    marginTop: "1.5rem",
  }}
>
  <Card title="Bulbul V2" icon="microphone" href="models/bulbul">
    Advanced text-to-speech model with multiple voices, code-mixing support, and
    high-quality natural speech synthesis for Indian languages.
  </Card>
</div>

<Note>
  View our [pricing page](https://dashboard.sarvam.ai/admin/billing/plans) for
  detailed information about model-specific pricing and usage tiers.
</Note>

## Bulbul: Our Text to Speech Model

Bulbul is our state-of-the-art text-to-speech model that excels in generating natural-sounding speech with support for multiple Indian languages, code-mixing, and various voice options.

## Text to Speech Features

<Tabs>
  <Tab title="Basic Synthesis">
    <div className="mb-8">
      <h3>Basic Text to Speech Synthesis</h3>
      <p>
        Convert text to natural-sounding speech with high quality. Features include:
      </p>
      <ul>
        <li>Multiple voice options</li>
        <li>Support for Indian languages</li>
        <li>Natural prosody and intonation</li>
        <li>High-quality audio output</li>
      </ul>
    </div>
    <Tabs>
      <Tab title="Python">
    ```python
from sarvamai import SarvamAI
from sarvamai.play import save

client = SarvamAI(api_subscription_key="YOUR_API_SUBSCRIPTION_KEY")
# Convert text to speech
audio = client.text_to_speech.convert(
      target_language_code="en-IN",
      text="Welcome to Sarvam AI!",
      model="bulbul:v2",
      speaker="anushka"
  )
save(audio, "output1.wav")
    ```
      </Tab>
      <Tab title="JavaScript">
        ```javascript
        import { SarvamAIClient } from "sarvamai";

        const client = new SarvamAIClient({
          apiSubscriptionKey: "YOUR_API_SUBSCRIPTION_KEY"
        });

        const response = await client.textToSpeech.convert(
          {
            text: "Welcome to Sarvam AI!",
            model: "bulbul:v2",
            speaker: "anushka",
            target_language_code: "en-IN"
          }
        );

        // Handle audio data
        console.log(response.audio);
        ```
      </Tab>
      <Tab title="cURL">
        ```bash
        curl -X POST https://api.sarvam.ai/text-to-speech \
     -H "api-subscription-key: <YOUR_API_SUBSCRIPTION_KEY>" \
     -H "Content-Type: application/json" \
     -d '{
"text": "Welcome to Sarvam AI!",
"target_language_code": "en-IN",
"speaker": "anushka",
"model": "bulbul:v2"
}'

````
</Tab>
</Tabs>

  </Tab>

  <Tab title="Voice Selection">
    <div className="mb-8">
      <h3>Available Voices</h3>
      <p>
        Choose from a variety of natural-sounding voices for different use cases and languages.
      </p>
      <CardGroup cols={2}>
        <Card title="Female Voices">
          - Anushka: Clear and professional
          - Manisha: Warm and friendly
          - Vidya: Articulate and precise
          - Arya: Young and energetic
        </Card>
        <Card title="Male Voices">
          - Abhilash: Deep and authoritative
          - Karun: Natural and conversational
          - Hitesh: Professional and engaging
        </Card>
      </CardGroup>
    </div>
    <Tabs>
      <Tab title="Python">
        ```python
import base64
from sarvamai import SarvamAI

client = SarvamAI(api_subscription_key="YOUR_API_SUBSCRIPTION_KEY")

# Convert text to speech
response = client.text_to_speech.convert(
    text="Welcome to Sarvam AI!",
    model="bulbul:v2",
    speaker="anushka"
)

# Decode and save the audio to a WAV file
combined_audio_b64 = "".join(response.audios)
decoded_audio = base64.b64decode(combined_audio_b64)

with open("output1.wav", "wb") as f:
    f.write(decoded_audio)
    
        ```
      </Tab>
      <Tab title="JavaScript">
        ```javascript
       import { SarvamAIClient } from "sarvamai";

const client = new SarvamAIClient({
    apiSubscriptionKey: "YOUR_API_SUBSCRIPTION_KEY"
});

const response = await client.textToSpeech.convert({
    text: "Hello, how are you?",
    target_language_code: "hi-IN",
    model: "bulbul:v2"
});

console.log(response);
        ```
      </Tab>
      <Tab title="cURL">
        ```bash
        # Generate speech with Anushka's voice
        curl -X POST https://api.sarvam.ai/text-to-speech \
     -H "api-subscription-key: <YOUR_API_SUBSCRIPTION_KEY>" \
     -H "Content-Type: application/json" \
     -d '{
  "text":
    "Welcome to Sarvam AI!"
  ,
  "target_language_code": "en-IN",
  "speaker": "anushka",
  "model": "bulbul:v2"
}'

        # Generate speech with Abhilash's voice
        curl -X POST https://api.sarvam.ai/text-to-speech \
     -H "api-subscription-key: <YOUR_API_SUBSCRIPTION_KEY>" \
     -H "Content-Type: application/json" \
     -d '{
  "text":
    "Welcome to Sarvam AI!"
  ,
  "target_language_code": "en-IN",
  "speaker": "abhilash",
  "model": "bulbul:v2"
}'

        # Generate speech with Manisha's voice
         curl -X POST https://api.sarvam.ai/text-to-speech \
     -H "api-subscription-key: <YOUR_API_SUBSCRIPTION_KEY>" \
     -H "Content-Type: application/json" \
     -d '{
  "text":
    "Welcome to Sarvam AI!"
  ,
  "target_language_code": "en-IN",
  "speaker": "manish",
 "model": "bulbul:v2"
}'
        ```
      </Tab>
    </Tabs>

  </Tab>

  <Tab title="Advanced Options">
    <div className="mb-8">
      <h3>Speech Customization</h3>
      <p>
        Fine-tune the speech output with various parameters:
      </p>
      <ul>
        <li>Adjust speech rate and pitch</li>
        <li>Control volume and emphasis</li>
        <li>Configure audio quality</li>
        <li>Enable text preprocessing</li>
      </ul>
    </div>
    <Tabs>
      <Tab title="Python">
        ```python
        from sarvamai import SarvamAI

        client = SarvamAI(
            api_subscription_key="YOUR_API_SUBSCRIPTION_KEY"
        )

        audio = client.text_to_speech.convert(
            text="Welcome to Sarvam AI!",
            model="bulbul:v2",
            speaker="anushka",
            pitch=0.2,
            pace=1.2,
            loudness=1.1,
            speech_sample_rate=24000,
            enable_preprocessing=True
        )
        
combined_audio = "".join(audio.audios)
b64_file = base64.b64decode(combined_audio)

with open("output1.wav", "wb") as f:
    f.write(b64_file) 

        ```
      </Tab>
      <Tab title="JavaScript">
        ```javascript
        mport { SarvamAIClient } from "sarvamai";

        const client = new SarvamAIClient({
          apiSubscriptionKey: "YOUR_API_SUBSCRIPTION_KEY"
        });

        async function generateCustomizedSpeech() {
          const response = await client.textToSpeech.convert(
            {
              text: "Welcome to Sarvam AI!",
              model: "bulbul:v2",
              target_language_code: "en-IN",
              speaker: "anushka",
              pitch: 0.2,
              pace: 1.2,
              loudness: 1.1,
              speech_sample_rate: 24000,
              enable_preprocessing: true
            }
          );

          // Handle the audio data
          console.log(response);
        }

        generateCustomizedSpeech();
        ```
      </Tab>
      <Tab title="cURL">
        ```bash
        curl -X POST https://api.sarvam.ai/text-to-speech \
     -H "api-subscription-key: <YYOUR_API_SUBSCRIPTION_KEY>" \
     -H "Content-Type: application/json" \
     -d '{
  "text":
    text: "Welcome to Sarvam AI!",
              model: "bulbul:v2",
              speaker: "anushka",
              pitch: 0.2,
              pace: 1.2,
              loudness: 1.1,
              "target_language_code": "en-IN",
              speech_sample_rate: 24000,
              enable_preprocessing: true
}'
        ```
      </Tab>
    </Tabs>

  </Tab>
</Tabs>

<Card title="Key Considerations">
  - Text length limit: 500 characters per input - Maximum 3 texts per API call -
  For numbers > 4 digits, use commas (e.g., '10,000') - Enable preprocessing for
  better mixed-language handling
</Card>
````