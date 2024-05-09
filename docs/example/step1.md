---
id: step1
title: Step 1. Create a product
sidebar_position: 2
hide_table_of_contents: true
---

# Step 1. Create a product

For successful try on generation you need to provide us multiple products or full look item.

Firstly, you need to create product with product image. You can do this by using the `createProduct` mutation.
At this step we will only need product id to create image for it and generate try on.

```graphql
mutation {
  createProduct(
    input: {
      name: "Tom Ford Suit"
      brandId: <YOUR_BRAND_ID>
      category: "suits"
      type: "TOTAL_LOOK"
      price: 3,650
      fitOption: "FIT"
      sleeveLength: "LONG"
      externalUrl: "https://www.farfetch.com/uk/shopping/men/tom-ford-shelton-item-19278862.aspx"
    }
  ) {
    id
  }
}
```

After successfully creating a product you need to create product image with returned newly created `product.id`.
Please consider that we are using `Upload`. It's not part of the GraphQL specification itself, but is an extension provided by some GraphQL server implementations, such as Apollo Server.
You can use some libraries like `apollo-upload-client` to send files to the server. Or you can use `fetch` or `axios` to send files to the server with `multipart/form-data` content type.

```graphql
mutation {
  createProductImage(
    input: {
      productId: <PRODUCT_ID>
      data: <File, multipart/form-data>
      type: ["TRY_ON"]
    }
  ) {
    id
  }
}
```

If mutation succeed the new try on product image will be attached to the product.
To check it you can use the `getProduct` query.

```graphql
query {
  getProduct(id: <PRODUCT_ID>) {
    id
    name
    images {
      id
      type
      url
    }
  }
}
```
