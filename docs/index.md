---
id: schema
slug: /
title: GraphQL API Genera Documentation
sidebar_position: 1
hide_table_of_contents: true
pagination_next: null
pagination_prev: null
sidebar_class_name: navbar__toggle
---

# Welcome to GraphQL API Genera Documentation

## Authentication

You will need your `API_KEY` in order to make requests to this API. Make sure you never share your API key with anyone, and you never commit it to a public repository. Include this key in the `X-API-KEY` header of your requests.

<!-- <code here> -->

## Support

If you have any questions or need help, please contact us at []

## How to use

This API is a GraphQL API. If you need some help with GraphQL, you can check the [official documentation](https://graphql.org/learn/).

### 1. Products Creation

For successful try on generation you need to provide us multiple single items or full look item.

- Firstly, you need to create product with product image. You can do this by using the `createProduct` mutation.
<!-- code here -->
- After successfully creating a product you need to create product image with returned newly created `product.id`.
<!-- code here -->

### 2. Generate Try On

After creating product and product image you can generate try on by using the `generateTryOn` mutation.

- You need to provide `product.id`s to generate try on.
<!-- code here -->
- After successful mutation execution you will get `tryOn.id` which you can use to get try on result. You need to poll the `getTryOn` query to get the result.
<!-- code here -->

## Billing

...
