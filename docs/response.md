**Payment Response**

Once the payment is complete the user is redirected to the `return_url` configured by you. Following is the typical destination where the user is taken to:

    HTTP GET https://merchant.shop.com/paymentresponse/handler?order_id=ORD1000&status=CHARGED&status_id=21

Please note that the parameters are sent using **HTTP GET**. 

**Transaction Status codes and their meaning**

| Status        | ID           | Meaning  |
| ------------- |:------------:|:---------|
| NEW                   | 10 | Newly created order |
| PENDING_VBV           | 23 | Authentication is in progress |
| CHARGED               | 21 | Successful transaction |
| AUTHENTICATION_FAILED | 26 | User did not complete authentication |
| AUTHORIZATION_FAILED  | 27 | User completed authentication. But bank refused the transaction |

Transaction is successful only if you receive `CHARGED` as the value in status. For all other cases, you must assume that the payment has failed.

### Status Verification

Since the `return_url` parameter group doesn't contain a way to check the integrity, you must always ensure that you read the status from the server using `/order/status` API explained [here](https://apidocs.juspay.in/#api-Order-GetOrder). **Status** along with many other data will be returned as part of the `/order/status` API. 

Failing to do status verification will result in hackers gaming your system. So, please ensure that status verification is in place before you go LIVE with us.

**Example request**

    curl -u api_key: \
      https://api.juspay.in/order/status?order_id=wv_test_ord_110011&merchant_id=skyview

**HTTP Response**

    {
      "merchant_id": "wv_test",
      "order_id": "wv_test_ord_110011",
      "customer_id": "wv_test_user@gmail.com",
      "product_id": "",
      "status": "CHARGED",
      "status_id": 21,
      "amount": 400,
      "currency": "INR",
      "refunded": false,
      "amount_refunded": 0,
      "return_url": "http://skyview./order/cc-confirm",
      ....
    }

The above response is truncated for brevity. However, as you can see above, the `status` was received as **CHARGED**. This indicates that the payment was successful and so, you can proceed with the fulfillment of the order.
