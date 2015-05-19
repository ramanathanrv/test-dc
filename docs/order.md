**Creating your first Order**

**Order** is cornerstone for conducting payments with Juspay. Order to Juspay is akin to what a shopping cart to a merchant is. Order encapsulates all the information that is required for a payment. All the payments, refunds, etc. are associated to an Order and it becomes the root reference.

Keeping in mind the fundamentals of distributed systems, we have let you choose your `order_id` when you create the order. This way, you can check the status of your order through our API whenever you want.

To know how to create the order, please refer to our [API documentation](https://apidocs.juspay.in/#api-Order-CreateOrder)

Nonetheless, please find the below snippet to quickly create an order. Note that you have to substitute the correct API Key.

    curl -k https://api.juspay.in/order/create \
        -u api_key: \
        -d "amount=10.00" \
        -d "order_id=ord_007" \
        -d "customer_id=guest_user_101" \
        -d "customer_email=customer@mail.com" \
        -d "customer_phone=919988665522" \
        -d "product_id=:pid" \
        -d "description=Order Info" \

