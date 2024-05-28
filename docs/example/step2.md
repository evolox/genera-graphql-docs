---
id: step2
title: Step 2. Create a model
sidebar_position: 3
hide_table_of_contents: true
---

# Step 2. Create a model

Model creation could be done earlier than product creation. There is no strict sequence of steps. You can create a model at any time as long as you pass the model to the try on generation mutation.

To create a model you need to use the `createModel` mutation. You need to provide the model name and some additional body parameters:

See full documentation for `createModel` mutation [here](/api/mutations/create-model).

```graphql
mutation {
  createModel(
    input: {
      name: "John",
      gender: "MALE"
      bodyType: "RECTANGLE"
      height: 180
      weight: 80
      age: 30
      }
  ){
    id
  }
```

After successful mutation execution you need to create a model image with returned newly created `model.id`. Logic is the same as for product image creation.

We are using image types to define the model image. You should use `HEAD` for selfie upload.

See full documentation for `createModelImage` mutation [here](/api/mutations/create-model-image).

```graphql
mutation {
  createModelImage(
    input: {
      modelId: <MODEL_ID>
      data: <File, multipart/form-data>
      type: "HEAD"
    }
  ) {
    id
  }
}

```

If mutation succeed the new model image will be attached to the model. To check it you can use the `model` query.

```graphql
query {
  model(id: <MODEL_ID>) {
    id
    images {
      id
      type
      url
    }
  }
}
```
