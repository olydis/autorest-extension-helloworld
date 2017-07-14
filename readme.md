# Simple AutoRest Extension

A simple AutoRest extension that can be used as a template for or documentation about writing such extensions.
Since this a TypeScript project, we distinguish between language agnostic and language dependent requirements.

## Language Agnostic Requirements

More information about these can be found [here](https://github.com/Azure/autorest/tree/master/docs/developer), summary:

1) Specify the start command of the extension as the `start` script in the `package.json` 
2) Specify potential `engines` required to run the `start` script (none in this example, see for example [azure-openapi-validator](https://github.com/Azure/azure-openapi-validator/search?q=engines))
3) Implement the AutoRest extension protocol (here: handles by library, see below)

## Language Specific Requirements: TypeScript

For TypeScript projects, simply import [autorest-extension-base](https://github.com/olydis/autorest-extension-base) which implements the AutoRest extension protocol and offers a simple API to register plugins.
