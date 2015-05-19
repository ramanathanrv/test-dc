**Checkout using Embedded iFrame**

# Create order

To collect payment from a customer, you first need to create an `order` with Juspay. Order encapsulates all the information that is required for a payment. An `order` object to Juspay is similar to what a "shopping_cart" to an e­-commerce website is.

Important parameters to be passed while creating the order:

* customer_id
    * All the cards stored for `customer_id` will be rendered in the form
* return_url
    * The customer will be redirected to this url, once the payment is complete
    * Make sure that this url is clean and starts with `http`/`https`
    * The url must not contain any query parameters

# Embedding the iFrame

Once you have create an `order` and setup the `order_id`, the next step is to render the payment form. For doing this, include the following iFrame in your checkout page.

    <iframe src="https://api.juspay.in/merchant/ipay?order_id=$order_id&merchant_id=$merchant_id" 
    width="630" height="400" 
    style="border: 1px solid #CCC;padding: 20px;height: auto;min-height: 300px;">
    </iframe>

Please note:

* Substitute `$order_id` with the `order_id` that you created in previous step
* Substitute `$merchant_id` with your `merchant_id` 

**Mobile optimized form**

Pass an extra parameter to the URL for rendering mobile optimized form: `&mobile=true`. Please see the code below:

    <iframe src="https://api.juspay.in/merchant/ipay?order_id=$order_id&merchant_id=$merchant_id&mobile=true" 
    width="630" height="400" 
    style="border: 1px solid #CCC;padding: 20px;height: auto;min-height: 300px;">
    </iframe>

