## Summary
--

## The Cart Update Request 
Information on cart updates may be received via your defined Merchant API url(s). In the example below, a POST request is sent to your unique merchant url, which can then return a success or failure response based on the transaction results.

Merchant url: https://sampleurl.com/api/cart_update
Request type: POST

## Reading the Request
Below is a sample cart.update request containing the shopper’s current cart, the requested cart additions and removals, and other identifying information such as order number, billing address, and shipping address.

``` json linenums="1" title="Cart Update Request"
"event": "cart.update",
"data": {
    "order_reference": "order-004",
    "add_items": [
        {
            "product_id": "t-shirt-floral-44",
            "price": 999,
            "currency": "USD",
            "quantity": 1
        }
    ],
    "remove_items": [
        {
            "product_id": "sunglasses-456",
            "quantity": 1
        }
    ],
    "discount_codes_to_add": [
        "SUMMERFUN15"
    ],
    "cart": {
        "order_reference": "order-12345",
        "display_id": "ID-12345",
        "billing_address": {
            "street_address1": "42 Wallaby Way",
            "street_address2": "42 Wallaby Way",
            "locality": "Kings County",
            "region": "New York",
            "postal_code": "11209",
            "country_code": "US",
            "country": "United States",
            "name": "Paul Sherman",
            "first_name": "Paul",
            "last_name": "Sherman",
            "phone": "867-5309",
            "email": "my.email@gmail.com"
        },
        "shipments": {
            "shipping_address_id": "address-1",
            "shipping_address": {
                "street_address1": "340 86th street",
                "street_address2": "APT 220",
                "locality": "Kings County",
                "region": "New York",
                "postal_code": "11209",
                "country_code": "US",
                "country": "United States",
                "name": "Charlotte Charles",
                "first_name": "Charlotte",
                "last_name": "Charles",
                "phone": "123-4567",
                "email": "my.email@gmail.com"
            },
            "total_weight": 55,
            "total_weight_unit": "kg",
            "shipping_method": "Shipping Method",
            "carrier": "FedEx",
            "reference": "1123",
            "signature": "a1B2s3dC4f5g5D6hj6E7k8F9l0",
            "service": "Option 1",
            "expedited": false,
            "cost": 1200,
            "tax_amount": 300,
            "package_type": "Standard",
            "package_width": 222,
            "package_height": 103,
            "package_depth": 90,
            "package_dimension_unit": "cm",
            "estimated_delivery_date": "08-30-2022",
        }
    }
}
```


### Event and Order Information
Our cart.update event above includes a set of data unique to this shopper and cart. 

With some of the customer-specific information removed, the data in this request looks as follows:

``` json linenums="1" title="Cart Update: Order Reference"
{
"event": "cart.update",
  "data": {
    "order_reference": "order-004",
    "add_items": [ ... ],
    "remove_items": [ ... ],
    "discount_codes_to_add": [ ... ],
    "cart": { ... }
    }
}
```

At its simplest, this request contains a reference to a specific order number (order-004) and its cart, as well as a series of actions to take based on the shopper’s changes: add_items, remove_items, and discount_codes_to_add.

Here, the order_reference helps ensure that the correct order is updated any time information is exchanged with Bolt.


### Adding and Removing Items 
As part of the defined cart.update event, we can see that several actions are being attempted just below the order number:

``` json linenums="1" title="Cart Update: Add/Remove Items"
"add_items": [
    {
    "product_id": "t-shirt-floral-44",
    "price": 999,
    "currency": "USD",
    "quantity": 1
    }
],
"remove_items": [
    {
    "product_id": "sunglasses-456",
    "quantity": 1
    }
],
```

Within ```add_items```, a product is defined that the shopper is attempting to add to their cart.


```product_id```: the unique product key used to identify the item
```price```: the price the product was added to the cart at
```currency```: the shopper’s chosen currency
```quantity```: the amount of the item to be added to the cart

Within ```remove_items```, a product is defined that the shopper has in their cart already, and would like to remove.


```product_id```: the unique product key used to identify the item
```quantity```: the amount of the item to be removed from the cart

Both of these sections can include a list of products to add or remove multiple items at once.

### Applying A Discount Code 
Our shopper is also adding a SUMMERFUN15 discount code:

``` json title="Cart Update: Discount Code"
"discount_codes_to_add": [
    "SUMMERFUN15"
],
```

If added successfully, the server response will confirm the discount applied: 

``` json title="Cart Update: Discount Reply"
"discounts": [
      {
        "amount": 754,
        "description": "Take 15% off of your order.",
        "details_uri": "https://sampleurl.com/discounts/#12345",
        "discount_category": "coupon",
        "reference": "SUMMERFUN15"
      }
],
```

### Reading Shopper Information
Shopper information is also defined within the cart section of the cart.update request.

``` json title="Cart Update: Shopper Information"
"cart": {
    "order_reference": "order-12345",
    "display_id": "ID-12345",
    "billing_address": {
    "street_address1": "42 Wallaby Way",
    "street_address2": "42 Wallaby Way",
    "locality": "Kings County",
    "region": "New York",
    "postal_code": "11209",
    "country_code": "US",
    "country": "United States",
    "name": "Paul Sherman",
    "first_name": "Paul",
    "last_name": "Sherman",
    "phone": "867-5309",
    "email": "my.email@gmail.com"
    },
    "shipments": {
    "shipping_address_id": "addres-1",
    "shipping_address": {
        "street_address1": "340 86th street",
        "street_address2": "APT 220",
        "locality": "Kings County",
        "region": "New York",
        "postal_code": "11209",
        "country_code": "US",
        "country": "United States",
        "name": "Charlotte Charles",
        "first_name": "Charlotte",
        "last_name": "Charles",
        "phone": "123-4567",
        "email": "my.email@gmail.com"
    },
    "total_weight": 55,
    "total_weight_unit": "kg",
    "shipping_method": "Shipping Method",
    "carrier": "FedEx",
    "reference": "1123",
    "signature": "a1B2s3dC4f5g5D6hj6E7k8F9l0",
    "service": "Option 1",
    "expedited": false,
    "cost": 1200,
    "tax_amount": 300,
    "package_type": "Standard",
    "package_width": 222,
    "package_height": 103,
    "package_depth": 90,
    "package_dimension_unit": "cm",
    "estimated_delivery_date": "08-30-2022",
    }
}
```


There are several features of this section that are important to note:

```order_reference```: the external order id, which ensures that the correct order is updated any time information is exchanged with the Merchant. This reference may not match the outer order number.

```display_id```: the external order id’s display value.
```billing_address```: includes all of the fields relevant to specific billing information for this order 

Within the cart is also a section for shipments, which separates out all relevant shipping details from the billing and order information, and includes shipping method, carrier, and packaging specifications like size and weight.


```shipment_address```: includes all of the fields relevant to specific shipping information for this order. This address may be different from the billing address.

## Errors & Troubleshooting
Several cart specific errors exist for failed transactions: 


Code
Code Name
Error Text
6300
MerchantCartUnknownError
An unknown error occurred when fetching the cart.
6301
MerchantCartOutOfStock
An item in your cart is no longer available. Please refresh your cart and try again.
6302
MerchantCartInvalidSize
The sizes for some of the items are invalid.
6303
MerchantCartInvalidQuantity
The quantities for some of the items are invalid.
6304
MerchantCartInvalidReference
The references for some of the items are invalid.
6305
MerchantCartInvalidAmount
An item in your cart has been updated. Please refresh your cart and try again.
6306
MerchantCartExpired
Your session timed out due to inactivity. Please refresh your cart and try again.
6307
MerchantOrderAlreadyExists
Your order may have been placed. Please check your email for an order confirmation. If you did not receive an email please refresh this page and retry checkout.


For a full list of specific errors in merchant api responses, visit the error codes documentation.
