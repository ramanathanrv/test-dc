**Checkout using Javascript**

This mode of integration is alternative to iFrame based integration. While the iFrame based integration lets you easily get to the market, javascript based integration gives you the ultimate flexibility to define the checkout experience for your customer.  

### Create order

To collect payment from a customer, you first need to create an `order` with Juspay. Order encapsulates all the information that is required for a payment. An `order` object to Juspay is similar to what a "shopping_cart" to an e­-commerce website is.

Important parameters to be passed while creating the order:

* customer_id
    * All the cards stored for `customer_id` will be rendered in the form
* return_url
    * If you choose the `redirect` based flow, the customer will be redirected to this url, once the payment is complete
    * Make sure that this url is clean and starts with `http`/`https`
    * The url must not contain any query parameters

### Include pay.js

In your checkout page, please include [pay.js](https://api.juspay.in/pay.js). This script takes care of completing the checkout process on your behalf. `pay.js` depends on **jQuery** library (any version after 1.4 is acceptable). 

    <script type="text/javascript" 
        src="https://api.juspay.in/pay.js"></script>

### Implementing Checkout

Before we get to the details, let's take a quick look at a typical payment form. This is the part you can build with your web framework, or by hand in HTML — however you're used to building forms on the web.

    <form class="juspay_inline_form" id="payment_form">
        <input type="hidden" class="merchant_id" value="guest">
        <input type="hidden" class="order_id" value="guest_order"/>
        <input type="text" class="card_number" placeholder="Card number">
        <input type="text" class="name_on_card" placeholder="Cardholder name">
        <input type="text" class="card_exp_month" placeholder="MM"> - <input type="text" class="card_exp_year" placeholder="YYYY">
        <input type="text" class="security_code" placeholder="CVV" >
        <input type="checkbox"  class="juspay_locker_save"> Save card information
        <button type="submit" class="make_payment">Pay</button>
        <input type="hidden" class="redirect" value="false">
    </form>


Besides the usual fields, there are some Juspay specific fields which will enable us to process the payment when the form is submitted. 

* `order_id` field represents the order_id of the `order` object that you have just created. 
* `merchant_id` helps us identify you. Changing this would mean that we credit the payment to someone else's account. So, please be careful with this field! 
* `juspay_locker_save` tells us whether we need to store this card after the payment is successful.
* If `redirect` is **true**, then we will choose the redirection flow for authentication. Otherwise, a popup window will be used for authentication. By default, popup window will be chosen for authentication.

`pay.js` listens to the form submit event and transports the card information safely to process it for payment. This is accomplished by the following snippet.

    <script type="text/javascript">
    Juspay.Setup({
        payment_form: "#payment_form",
        success_handler: function(status) {},
        error_handler: function(error_code, error_message, bank_error_code, 
            bank_error_message, gateway_id) {}
    })
    </script>

### Redirect or Popup?

Authentication can be performed either via a **popup** or using the traditional **redirection based flow**. In the former, a separate window opens up to conduct the authentication. This popup is closed as soon as the payment is complete. You can control this choice by passing the appropriate value in `redirect` element.

In the code snippet above showing `Juspay.Setup`, there are two handlers `success_handler` and `error_handler`. If the payment is successful, then success_handler is invoked. If the payment failed, then `error_handler` will be invoked.

### Redirect Flow

For mobile, redirection flow is chosen by default. You cannot change this. So, you **must always** ensure that you have coded the case to handle the **redirection flow** as well. 


### Card Form Validation

Validation must be implemented by you. Please ensure the following:

* Card Number must be validated using Luhn Algorithm
* Expiry date must be in future
* CVV (security_code) must be three digits for visa,mastercard and 4 digits for American Express
* Cardholder name must be alphabets & space only

### Stored cards

To checkout using stored card, the form must contain the `card_token` element and the `security_code` element. Please see the sample code below.

    <form class="juspay_express_form" id="payment_form">
        <input type="hidden" class="card_token" value="54eb18a0-c7ca-46a3-b122-448d93a3698a"/>
        <input type="hidden" class="merchant_id" value="guest">
        <input type="hidden" class="order_id" value="guest_order"/>
        <label>
            <p>5264-XXXXXXXX-3394</p>
            <p>Expires: 10/20</p>
        </label>
        <input type="text" class="security_code" placeholder="CVV" >
        <button type="submit" class="make_payment">Pay</button>
    </form>

Binding to `Juspay.Setup` is same as above. To handle multiple stored cards, you can create separate forms with different identifiers and bind them individually. It is also possible to handle using a single form.

### PCI Compliance

When using Javascript for checkout, since there is a possibility that the card information could flow to the merchant's servers, the PCI Compliance scope is higher than that of iFrame based integration. You can become PCI Compliant by completing the PCI DSS [SAQ-A EP questionnaire](https://www.pcisecuritystandards.org/documents/SAQ_A-EP_v3.pdf). Please note that this is only applicable for **e-commerce** merchants. For everyone else, filling up the PCI DSS [SAQ-A questionnaire](https://www.pcisecuritystandards.org/documents/SAQ_A_v3-1.docx) would suffice. 
