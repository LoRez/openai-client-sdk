# OpenAI Java Client SDK

The SDK is generated with [openapi-generator](https://openapi-generator.tech) based on the OpenAPI schema provided by OpenAI [here](https://github.com/openai/openai-openapi).

In order to make this work some changes had to be made to the schema:

- Add Bearer Authentication to the schema so that API-Keys can be used
- Remove defaults that were set to null for arrays and objects
- Add Descriptions to get rid of warnings

The changes were made with Stoplight which also changed the formatting a bit.

To be able to compile the SDK with Java 17, I had to add a few dependencies to the project and disabled test generation.

## Example

        OpenAiApi api = new OpenAiApi();
        api.getApiClient().setBearerToken(<INSERT_API_KEY>);

        CreateImageRequest createImageRequest = new CreateImageRequest()
                .prompt("Camel in the desert")
                .size(CreateImageRequest.SizeEnum._256X256);

        ImagesResponse imagesResponse = api.createImage(createImageRequest);
