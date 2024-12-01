---
project: openai-cf-workers-ai
stars: 234
description: Replacing OpenAI's API with Cloudflare AI.
url: https://github.com/chand1012/openai-cf-workers-ai
---

⚡️ OpenAI for Workers AI 🧠
===========================

### 

Simple, quick, and dirty implementation of OpenAI's API on Cloudflare's new Workers AI platform.

Why?
----

I think that in the near future, smaller, cheaper LLMs will be a legitimate competitor to OpenAI's GPT-3.5 and GPT-4 APIs. Most developers will not want to rewrite their entire codebase in order to use these up-and-coming models. I also think that Cloudflare Workers are a neat way to host AI and APIs, so I implemented the OpenAI API on Workers AI. This allows developers to use the OpenAI SDKs with the new LLMs without having to rewrite all of their code. This code, as is Workers AI, is not production ready but will be semi-regularly updated with new features as they roll out to Workers AI.

Compatibility
-------------

Here are all the APIs I would like to implement or have implemented that are currently possible with the Workers AI platform.

-   Completions
-   Chat Completions
-   Audio Transcription
-   Embeddings
-   Audio Translation
    -   Uses Whisper to transcribe, Llama 2 to identify the language, and m2m-100 to translate.
-   Images
    -   Image Generation
-   Files
    -   Needed for Assistants.
    -   Use a D1 database for metadata, R2 for the actual file.
-   Assistants
    -   Assistants
        -   Store assistants in a D1 database.
        -   File support may be just limited to text files if there is any at all.
    -   Threads
        -   Use a D1 database to store threads. Relate them to an assistant.
    -   Messages
        -   Store messages in a D1 database. Relate them to a thread.
    -   Runs
        -   Use a queue to handle runs. Get messages from a D1 database, return results to database.

Here are the APIs that I would like to implement but are not currently possible with the Workers AI platform.

-   Fine Tuning
-   Images
    -   Image Editing
    -   Image Variants

Here are the APIs that could probably be implemented but I don't have the need to implement them.

-   Moderation
    -   Use Llama 2 to classify. May be difficult to prompt engineer.

Deploying
---------

First, clone the repository.

git clone https://github.com/chand1012/openai-cf-workers-ai
cd openai-cf-workers-ai

Then modify the `CLOUDFLARE_ACCOUNT_ID` variable in the `wrangler.toml` file to match your Cloudflare Account ID.

\[vars\]
CLOUDFLARE\_ACCOUNT\_ID = "c8c30db3dddc4ad31065d336368c7905" # replace with your own.

Next, install the dependencies and deploy to your account. If you are not logged in to wrangler, you will be prompted to log in.

yarn
yarn init-prod # only needs run the first time!!!
yarn deploy

Finally, set the `ACCESS_TOKEN` and `CLOUDFLARE_API_TOKEN` variables using wrangler. To get your Cloudflare API token, go to the Cloudflare dashboard and create a new token with the `Workers AI` template. `ACCESS_TOKEN` can be any string you want, but I recommend creating a random string with `openssl rand -hex 32` .

wrangler secret put ACCESS\_TOKEN # put the access token here
wrangler secret put CLOUDFLARE\_API\_TOKEN # put the Cloudflare API token here

Now you're ready to use the API! You can find the URL in the output of the `yarn deploy` command.

Development
-----------

Before Testing, copy `.dev.vars.example` to `.dev.vars` and populate the variables with the appropriate values. See Deploying for more information.

As of 07/10/2023 testing locally does not work. However, you can test remotely using the following command:

yarn init-dev # only needs run the first time!!!
yarn dev

This will start a local server that will proxy requests to your deployed API. You can then use the API as you normally would, but with the local server's URL instead of the deployed URL.

Usage
-----

See the OpenAI API docs for more information on the API. Here's an example from the OpenAI docs:

curl https://openai-cf.yourusername.workers.dev/v1/chat/completions \\
  -H "Content-Type: application/json" \\
  -H "Authorization: Bearer <Any string value you set.>" \\
  -d '{
    "model": "@cf/meta/llama-2-7b-chat-int8",
    "messages": \[
      {
        "role": "system",
        "content": "You are a helpful assistant."
      },
      {
        "role": "user",
        "content": "Hello!"
      }
    \]
  }'
# {"id":"ccfbc7fc-d871-4139-90dc-e6c33fc7f275","model":"@cf/meta/llama-2-7b-chat-int8","created":1696701894,"object":"chat.completion","choices":\[{"index":0,"message":{"role":"assistant","content":"Hello there! \*adjusts glasses\* It's a pleasure to meet you. Is there something I can help you with or would you like to chat? I'm here to assist you in any way I can. 😊"},"finish\_reason":"stop"}\],"usage":{"prompt\_tokens":0,"completion\_tokens":0,"total\_tokens":0}}

If you want to use this with the OpenAI Python or JavaScript SDK, you can use the following code, replace the base URL with your own. For example:

import openai
openai.api\_base \= 'https://openai-cf.yourusername.workers.dev/v1'

\# rest of code

import OpenAI from 'openai';

const openai \= new OpenAI({
    baseURL: 'https://openai-cf.yourusername.workers.dev/v1',
    ...
});

// rest of code

Compromises
-----------

There were a few compromises I had to make in order to create the API.

The first is that the API does not count tokens, and will always return zero for the `usage` attribute in the return object. It will always return it for compatibility reasons, but until tokenization is added for the respective model, we cannot count tokens. Each model tokenizes differently, so we can't use tiktoken. It may be possible to tokenize using HuggingFace transformers, but that may take too long and not allow free users to deploy the API. More investigation is needed.

Stop tokens are also non-functional. There is no way to specify a stop reason or token with the current API. It will be ignored. Sometimes these stop tokens can leak through to the final response. This is a known issue and will be fixed in the future.

License
-------

Licensed under the MIT License.
