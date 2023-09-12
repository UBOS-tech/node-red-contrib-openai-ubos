## node-red-contrib-openai-ubos

A Node-RED node that interacts with OpenAI machine learning models to generate text like ChatGPT.

<img width="100%"  alt="Ubos - End-to-End Software Development Platform" src="https://ubos.tech/wp-content/uploads/2023/03/cropped-Group-21015-1.png">

<h3 align="center">
  <b><a href="https://ubos.tech/">UBOS</a></b>
  •
  <a href="https://community.ubos.tech/">Community</a>
  •
  <a href="https://www.youtube.com/@ubos_tech">Youtube</a>
  •
  <a href="https://discord.com/invite/dt59QaptH2">Discord</a>
  •
  <a href="https://github.com/UBOS-tech">GitHub</a>
</h3>
  
<div align="center">
 
[![flow](https://img.shields.io/badge/platform-Node--RED-red)](https://flows.nodered.org/node/node-red-contrib-openai-ubos)
[![npm](https://img.shields.io/npm/v/node-red-contrib-openai-ubos)](https://www.npmjs.com/package/node-red-contrib-openai-ubos)
 
</div>

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

### Create embeddings
 When msg.model is set to text-embedding-ada-002:
  - [Required] input: [Type: string or array] Input text to embed, encoded as a string or array of tokens. To embed multiple inputs in a single request, pass an array of strings or array of token arrays. Each input must not exceed the max input tokens for the model (8191 tokens for `text-embedding-ada-002`) and cannot be an empty string. [Example Python code](https://github.com/openai/openai-cookbook/blob/main/examples/How_to_count_tokens_with_tiktoken.ipynb) for counting tokens.

  - user: [Type: string] A unique identifier representing your end-user, which can help OpenAI to monitor and detect abuse. [Learn more](https://platform.openai.com/docs/guides/safety-best-practices).
  json
  msg.OPENAI_API_KEY = "your api key";
  msg.model = "text-embedding-ada-002";
  msg.input = "Lorem Ipsum is simply dummy text of the printing and typesetting industry";

## Demo
<img width="1439" alt="image" src="https://github.com/UBOS-tech/node-red-contrib-openai-ubos/assets/41735477/53e6e194-7a0b-4e09-b811-5a5c4521640e">

<img width="1440" alt="image" src="https://github.com/UBOS-tech/node-red-contrib-openai-ubos/assets/41735477/086e3ada-7003-4a8c-8ae1-722c0acc238f">

### Bugs reports and feature requests

Please report any issues or feature requests at <a href="https://github.com/UBOS-tech/node-red-contrib-openai-ubos/issues">GitHub</a>.

## License

[MIT License](https://github.com/UBOS-tech/node-red-contrib-openai-ubos/blob/main/LICENSE)
