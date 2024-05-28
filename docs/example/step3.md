---
id: step3
title: Step 3. Create Try On
sidebar_position: 4
pagination_next: null
hide_table_of_contents: true
---

# Step 3. Create Try On

After creating product, product image and model you can generate try on by using the `generateTryOn` mutation.
For our example we will be using `TOTAL_LOOK` product - 'suit'. If you want create try on with different combinations of tops and bottoms you will have to provide multiple products IDs as values to corresponding fields.

You need to provide `product.id` from the product creation step and `model.id` from the model creation step:

See full documentation for `createTryOn` mutation [here](/api/mutations/create-try-on).

```graphql
mutation {
  createTryOn(
    input: {
      modelId: <MODEL_ID>
      topProductId: <PRODUCT_ID>
    }
  ) {
    taskID
  }
}
```

After successful mutation execution you will get `taskID` which you can use to get try on result. You need to poll the `getTryOnResult` query to get the result.
If you are using Apollo Client you can use `pollInterval` option to poll the server with a specific interval.

`getTryOn` query returns `generationResult` that represents generation result and metadata such as: which products were used, which model was used, and result image url.

See full documentation for `getTryOnResult` mutation [here](/api/queries/get-try-on-result).

See full documentation for `generationResult` [here](/types/objects/try-on).

```graphql
query {
  getTryOn(taskID: <TASK_ID>) {
    generationResult {
      resultUrl
    }
  }
}
```

After some short period of time you will get image url in the `resultImg` field. You can use it to show the try on result to the user.

That's all! You have successfully created a try on with Genera API. Now you can show the result to the user and get feedback from them.
