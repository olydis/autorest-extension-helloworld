# Simple AutoRest Extension

A simple AutoRest extension that can be used as a template for or documentation about writing such extensions.
Since this a TypeScript project, we distinguish between language agnostic and language dependent requirements.

## Language Agnostic Requirements

More information about these can be found [here](https://github.com/Azure/autorest/tree/master/docs/developer), summary:

1) Specify the start command of the extension as the `start` script in the `package.json` 
2) Specify potential `engines` required to run the `start` script (none in this example, see for example [azure-openapi-validator](https://github.com/Azure/azure-openapi-validator/search?q=engines))
3) Implement the AutoRest extension protocol (here: handled by library, see below)
4) Hook up plugins into the AutoRest pipeline DAG, e.g.

``` yaml
pipeline:
    hello-world: # <- name of plugin
        scope: hello
        # ^ will make this plugin run only when `--hello` is passed on the CLI or
        # when there is `hello: true | <some object>` in the configuration file
        
        #input: swagger-document/identity
        # ^ other pipeline step to use as a predecessor in the DAG
        # takes the outputs of that step as input to this plugin.
        # If no `input` is declared here, the plugin runs immediately and gets
        # the `input-file`s of this AutoRest call as its inputs.
```

## Language Specific Requirements: TypeScript

For TypeScript projects, simply import [autorest-extension-base](https://github.com/olydis/autorest-extension-base) which implements the AutoRest extension protocol and offers a simple API to register plugins.
See [index.ts](./index.ts).