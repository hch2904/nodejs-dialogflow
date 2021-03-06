[//]: # "This README.md file is auto-generated, all changes to this file will be lost."
[//]: # "To regenerate it, use `npm run generate-scaffolding`."
<img src="https://avatars2.githubusercontent.com/u/2810941?v=3&s=96" alt="Google Cloud Platform logo" title="Google Cloud Platform" align="right" height="96" width="96"/>

# [Dialogflow: Node.js Client](https://github.com/googleapis/nodejs-dialogflow)

[![release level](https://img.shields.io/badge/release%20level-beta-yellow.svg?style&#x3D;flat)](https://cloud.google.com/terms/launch-stages)
[![npm version](https://img.shields.io/npm/v/dialogflow.svg)](https://www.npmjs.org/package/dialogflow)
[![codecov](https://img.shields.io/codecov/c/github/googleapis/nodejs-dialogflow/master.svg?style=flat)](https://codecov.io/gh/googleapis/nodejs-dialogflow)

[Dialogflow](https://dialogflow.com/docs/reference/v2-agent-setup) is an enterprise-grade NLU platform that makes it easy for developers to design and integrate conversational user interfaces into mobile apps, web applications, devices, and bots.


* [Using the client library](#using-the-client-library)
* [Samples](#samples)
* [Versioning](#versioning)
* [Contributing](#contributing)
* [License](#license)

## Using the client library

1.  [Select or create a Cloud Platform project][projects].

1.  [Enable billing for your project][billing].

1.  [Enable the Dialogflow API][enable_api].

1.  [Set up authentication with a service account][auth] so you can access the
    API from your local workstation.

1. Install the client library:

        npm install --save dialogflow

1. Try an example:

```javascript
// You can find your project ID in your Dialogflow agent settings
const projectId = 'ENTER_PROJECT_ID_HERE'; //https://dialogflow.com/docs/agents#settings
const sessionId = 'quickstart-session-id';
const query = 'hello';
const languageCode = 'en-US';

// Instantiate a DialogFlow client.
const dialogflow = require('dialogflow');
const sessionClient = new dialogflow.SessionsClient();

// Define session path
const sessionPath = sessionClient.sessionPath(projectId, sessionId);

// The text query request.
const request = {
  session: sessionPath,
  queryInput: {
    text: {
      text: query,
      languageCode: languageCode,
    },
  },
};

async function main() {
  // Send request and log result
  const responses = await sessionClient.detectIntent(request);
  console.log('Detected intent');
  const result = responses[0].queryResult;
  console.log(`  Query: ${result.queryText}`);
  console.log(`  Response: ${result.fulfillmentText}`);
  if (result.intent) {
    console.log(`  Intent: ${result.intent.displayName}`);
  } else {
    console.log(`  No intent matched.`);
  }
}

main().catch(err => {
  console.error('ERROR:', err);
});
```

## Samples

Samples are in the [`samples/`](https://github.com/googleapis/nodejs-dialogflow/tree/master/samples) directory. The samples' `README.md`
has instructions for running the samples.

| Sample                      | Source Code                       | Try it |
| --------------------------- | --------------------------------- | ------ |
| Detect Intent (Text) | [source code](https://github.com/googleapis/nodejs-dialogflow/blob/master/samples/detect.js) | [![Open in Cloud Shell][shell_img]](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googleapis/nodejs-dialogflow&page=editor&open_in_editor=samples/detect.js,samples/README.md) |
| Create Knowledge Base | [source code](https://github.com/googleapis/nodejs-dialogflow/blob/master/samples/detect.v2beta1.js) | [![Open in Cloud Shell][shell_img]](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googleapis/nodejs-dialogflow&page=editor&open_in_editor=samples/detect.v2beta1.js,samples/README.md) |
| Get Knowledge Base | [source code](https://github.com/googleapis/nodejs-dialogflow/blob/master/samples/detect.v2beta1.js) | [![Open in Cloud Shell][shell_img]](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googleapis/nodejs-dialogflow&page=editor&open_in_editor=samples/detect.v2beta1.js,samples/README.md) |
| list Knowledge Base | [source code](https://github.com/googleapis/nodejs-dialogflow/blob/master/samples/detect.v2beta1.js) | [![Open in Cloud Shell][shell_img]](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googleapis/nodejs-dialogflow&page=editor&open_in_editor=samples/detect.v2beta1.js,samples/README.md) |
| list Knowledge Base | [source code](https://github.com/googleapis/nodejs-dialogflow/blob/master/samples/detect.v2beta1.js) | [![Open in Cloud Shell][shell_img]](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googleapis/nodejs-dialogflow&page=editor&open_in_editor=samples/detect.v2beta1.js,samples/README.md) |
| create Document | [source code](https://github.com/googleapis/nodejs-dialogflow/blob/master/samples/detect.v2beta1.js) | [![Open in Cloud Shell][shell_img]](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googleapis/nodejs-dialogflow&page=editor&open_in_editor=samples/detect.v2beta1.js,samples/README.md) |
| list Documents | [source code](https://github.com/googleapis/nodejs-dialogflow/blob/master/samples/detect.v2beta1.js) | [![Open in Cloud Shell][shell_img]](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googleapis/nodejs-dialogflow&page=editor&open_in_editor=samples/detect.v2beta1.js,samples/README.md) |
| Get Document | [source code](https://github.com/googleapis/nodejs-dialogflow/blob/master/samples/detect.v2beta1.js) | [![Open in Cloud Shell][shell_img]](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googleapis/nodejs-dialogflow&page=editor&open_in_editor=samples/detect.v2beta1.js,samples/README.md) |
| delete Document | [source code](https://github.com/googleapis/nodejs-dialogflow/blob/master/samples/detect.v2beta1.js) | [![Open in Cloud Shell][shell_img]](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googleapis/nodejs-dialogflow&page=editor&open_in_editor=samples/detect.v2beta1.js,samples/README.md) |
| detect Intent with sentiment analysis | [source code](https://github.com/googleapis/nodejs-dialogflow/blob/master/samples/detect.v2beta1.js) | [![Open in Cloud Shell][shell_img]](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googleapis/nodejs-dialogflow&page=editor&open_in_editor=samples/detect.v2beta1.js,samples/README.md) |
| detect Intent with text-to-speech response | [source code](https://github.com/googleapis/nodejs-dialogflow/blob/master/samples/detect.v2beta1.js) | [![Open in Cloud Shell][shell_img]](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googleapis/nodejs-dialogflow&page=editor&open_in_editor=samples/detect.v2beta1.js,samples/README.md) |
| detect Intent with Knowledge Base | [source code](https://github.com/googleapis/nodejs-dialogflow/blob/master/samples/detect.v2beta1.js) | [![Open in Cloud Shell][shell_img]](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googleapis/nodejs-dialogflow&page=editor&open_in_editor=samples/detect.v2beta1.js,samples/README.md) |
| Detect Intent (Audio) | [source code](https://github.com/googleapis/nodejs-dialogflow/blob/master/samples/detect.js) | [![Open in Cloud Shell][shell_img]](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googleapis/nodejs-dialogflow&page=editor&open_in_editor=samples/detect.js,samples/README.md) |
| Detect Intent (Streaming) | [source code](https://github.com/googleapis/nodejs-dialogflow/blob/master/samples/detect.js) | [![Open in Cloud Shell][shell_img]](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googleapis/nodejs-dialogflow&page=editor&open_in_editor=samples/detect.js,samples/README.md) |
| Create Entity | [source code](https://github.com/googleapis/nodejs-dialogflow/blob/master/samples/resource.js) | [![Open in Cloud Shell][shell_img]](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googleapis/nodejs-dialogflow&page=editor&open_in_editor=samples/resource.js,samples/README.md) |
| Delete Entity | [source code](https://github.com/googleapis/nodejs-dialogflow/blob/master/samples/resource.js) | [![Open in Cloud Shell][shell_img]](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googleapis/nodejs-dialogflow&page=editor&open_in_editor=samples/resource.js,samples/README.md) |
| Create Intent | [source code](https://github.com/googleapis/nodejs-dialogflow/blob/master/samples/resource.js) | [![Open in Cloud Shell][shell_img]](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googleapis/nodejs-dialogflow&page=editor&open_in_editor=samples/resource.js,samples/README.md) |
| Delete Intent | [source code](https://github.com/googleapis/nodejs-dialogflow/blob/master/samples/resource.js) | [![Open in Cloud Shell][shell_img]](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googleapis/nodejs-dialogflow&page=editor&open_in_editor=samples/resource.js,samples/README.md) |
| Create Context | [source code](https://github.com/googleapis/nodejs-dialogflow/blob/master/samples/resource.js) | [![Open in Cloud Shell][shell_img]](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googleapis/nodejs-dialogflow&page=editor&open_in_editor=samples/resource.js,samples/README.md) |
| Delete Context | [source code](https://github.com/googleapis/nodejs-dialogflow/blob/master/samples/resource.js) | [![Open in Cloud Shell][shell_img]](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googleapis/nodejs-dialogflow&page=editor&open_in_editor=samples/resource.js,samples/README.md) |
| Create Session Entity Type | [source code](https://github.com/googleapis/nodejs-dialogflow/blob/master/samples/resource.js) | [![Open in Cloud Shell][shell_img]](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googleapis/nodejs-dialogflow&page=editor&open_in_editor=samples/resource.js,samples/README.md) |
| Delete Session Entity Type | [source code](https://github.com/googleapis/nodejs-dialogflow/blob/master/samples/resource.js) | [![Open in Cloud Shell][shell_img]](https://console.cloud.google.com/cloudshell/open?git_repo=https://github.com/googleapis/nodejs-dialogflow&page=editor&open_in_editor=samples/resource.js,samples/README.md) |

The [Dialogflow Node.js Client API Reference][client-docs] documentation
also contains samples.

## Versioning

This library follows [Semantic Versioning](http://semver.org/).

This library is considered to be in **beta**. This means it is expected to be
mostly stable while we work toward a general availability release; however,
complete stability is not guaranteed. We will address issues and requests
against beta libraries with a high priority.

More Information: [Google Cloud Platform Launch Stages][launch_stages]

[launch_stages]: https://cloud.google.com/terms/launch-stages

## Contributing

Contributions welcome! See the [Contributing Guide](https://github.com/googleapis/nodejs-dialogflow/blob/master/.github/CONTRIBUTING.md).

## License

Apache Version 2.0

See [LICENSE](https://github.com/googleapis/nodejs-dialogflow/blob/master/LICENSE)

## What's Next

* [Dialogflow Documentation][product-docs]
* [Dialogflow Node.js Client API Reference][client-docs]
* [github.com/googleapis/nodejs-dialogflow](https://github.com/googleapis/nodejs-dialogflow)

Read more about the client libraries for Cloud APIs, including the older
Google APIs Client Libraries, in [Client Libraries Explained][explained].

[explained]: https://cloud.google.com/apis/docs/client-libraries-explained

[client-docs]: https://dialogflow.com/docs/reference/api-v2/rpc/
[product-docs]: https://dialogflow.com/docs/reference/api-v2/rpc/
[shell_img]: https://gstatic.com/cloudssh/images/open-btn.png
[projects]: https://console.cloud.google.com/project
[billing]: https://support.google.com/cloud/answer/6293499#enable-billing
[enable_api]: https://console.cloud.google.com/flows/enableapi?apiid=dialogflow.googleapis.com
[auth]: https://cloud.google.com/docs/authentication/getting-started
