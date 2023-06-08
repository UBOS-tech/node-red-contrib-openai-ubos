## node-red-contrib-openai-ubos

A Node-RED node that interacts with OpenAI machine learning models to generate text like ChatGPT.

### Quick Start

Install with the built in <b>Node-RED Palette manager</b> or using npm:
```
npm install node-red-contrib-openai-ubos
```

## Setup

When editing the nodes properties, to get your `OPENAI_API_KEY` log in to [ChatGPT](https://chat.openai.com/chat) and then visit https://platform.openai.com/account/api-keys click "+ Create new secret key" then copy and paste the "API key" into the nodes `API_KEY` property value.

To get your `Organization` visit https://platform.openai.com/account/org-settings then copy and paste the "OrganizationID" into the nodes `Organization` property value.

## Properties

 - `msg.OPENAI_API_KEY`: This is the API key provided by OpenAI. It is necessary for authentication when making requests to the OpenAI API.

 - `msg.prompt`: This string forms the initial text from which the model will generate its continuation.
 - `msg.model`: This property defines the name of the OpenAI model to be used for generating the text, for example, "text-davinci-003".
 - `msg.temperature`: This property controls the randomness in the output of the model. Higher values result in more random outputs. This is a numerical value.
 - `msg.max_tokens`: This property sets the maximum length of the model output. This is a numerical value.
 - `msg.messages`: This is an array meant to hold any messages that are to be passed along the Node-RED flow. Each object in the array can contain additional properties like `role` and `content`. For example:
   ```json
   "messages": [
       {"role": "system", "content": "Set the behavior"},
       {"role": "assistant", "content": "Provide examples"},
       {"role": "user", "content": "Set the instructions"}
   ]
   ```
 - `msg.top_p`: This property is used when nucleus sampling is preferred for generating the text. The value for this property is expected to be a number between 0 and 1.
 - `msg.frequency_penalty`: This property allows for penalization of new tokens based on their frequency. The value should be a number between 0 and 1.
 - `msg.stop`: Up to 4 sequences where the API will stop generating further tokens. For example:
   ```json
   msg.stop = ["word-1", "word-2"]
   ```
 - `msg.presence_penalty`: This property can be used to control the model's preference for introducing new concepts during text generation. Like `msg.frequency_penalty`, it should be a number between 0 and 1.
