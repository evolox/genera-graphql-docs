---
id: step2
title: Step 2. Create Try On
sidebar_position: 3
pagination_next: null
hide_table_of_contents: true
---

# Step 2. Create Try On

After creating product and product image you can generate try on by using the `generateTryOn` mutation.
For our example we will be using `TOTAL_LOOK` product - 'suit'. If you want create try on with different combinations of tops and bottoms you will have to provide multiple products IDs as values to corresponding fields.

You need to provide `product.id` from the previous step and some additional user parameters:

See full documentation for `createProductImage` mutation [here](/api/mutations/create-try-on).

```graphql
mutation {
  createTryOn(
    input: {
      selfiePhoto: <File, multipart/form-data> # Same Upload scalar as for product image
      topProductId: <PRODUCT_ID>
      gender: "MALE"
      bodyType: "RECTANGLE"
      height: 180
      weight: 80
      age: 30
    }
  ) {
    taskID
  }
}
```

After successful mutation execution you will get `taskId` which you can use to get try on result. You need to poll the `getTryOn` query to get the result.
If you are using Apollo Client you can use `pollInterval` option to poll the server with a specific interval.

See full documentation for `createProductImage` mutation [here](/api/queries/get-try-on-result).

```graphql
query {
  getTryOn(taskID: <TASK_ID>) {
    resultImg
  }
}
```

After some short period of time you will get image url in the `resultImg` field. You can use it to show the try on result to the user.

That's all! You have successfully created a try on with Genera API. Now you can show the result to the user and get feedback from them.
