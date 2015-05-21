**Gateways supported**

We support both **bank gateways** and **aggregators**.

+ Bank Gateways
    * HDFC
    * ICICI
    * AXIS
+ Aggregators
    * PayU
    * Citrus
    * CCAvenue
    * EBS
    * Atom

### HDFC

HDFC Bank would give you SSL Gateway by default. In order to use Express Checkout with HDFC, the SSL account must be converted to a TranPortal account. This entails the following:

1. Write to your Relationship Manager in this regard
* Copy us in the email and we will share the required documentation from our side
* HDFC would insist on a **Tripartite Agreement**. This is similar to the Merchant Services Agreement that you signed with HDFC. Three copies of this agreement must be executed. Any changes required in this agreement would take a long time for consensus. So, we recommend that you sign this agreement as it is.
* Post signing this, HDFC PG would convert your account to TranPortal.
* Configure the TranPortal ID & TranPortal password in the Merchant Portal of JusPay and you are ready to start driving transactions.

Time taken: 2 - 4 weeks

### ICICI

SSL PG account of ICICI must be converted to MOTO account. The following steps could help achieve this:

1. Write to your Relationship Manager in this regard
* Copy us in the email and we will share the required documentation from our side
* ICICI will create a MOTO account will share the access credentials. The following will be required to commence integration: 
    * MID
    * MPI ID
    * Key (can be obtained by logging in to ICICI console)
* Once you have all these three, configure this PG account in JusPay Merchant Portal for your merchant account
* 3D Secure Response URL must be updated to `https://api.juspay.in/payment/second-factor-response`. Place a request to ICICI PG Helpdesk for this.
* Once the above step is done, you will have to run a test transaction using your credit/debit card. This transaction will fail with an error message **'No suitable acquirer found'**. 
* Contact PG Helpdesk again and share with them the transaction details and the response. ICICI PG will confirm that the integration is successful and they will go on to make your account LIVE.

Time taken: 1 - 3 weeks

### Axis

SSL PG account of AXIS must be converted to VPC account. The following steps could help achieve this:

1. Write to your Relationship Manager asking to upgrade your account to VPC Enabled. Mention that you are using JusPay as the technology company to handle sensitive card data.
* Copy us in the email and we will share the required documentation from our side
* Axis will enable VPC for your account
* Once you have the confirmation from Axis, configure the Axis PG credentials in JusPay Merchant Portal for your merchant account
* Do a transaction with real credit/debit card to ensure that this feature is working fine. If you directly land on the 3D secure page, then the account has been upgraded

Time taken: 1 - 3 weeks

### PayU

1. The PG account must have **Seamless** option enabled to use Express Checkout
* Write to your Relationship Manager asking to upgrade your account to Seamless Enabled. Mention that you are using JusPay as the technology company to handle sensitive card data.
* Copy us in the email and we will share the required documentation from our side
* PayU will enable Seamless for your account
* Once you have the confirmation from PayU, configure the PayU account details in JusPay Merchant Portal for your merchant account. The following are the required details:
    * PayU merchant key
    * PayU salt
* Do a transaction with real credit/debit card to ensure that this feature is working fine. If you directly land on the 3D secure page, then the account has been upgraded
* You should be able to see the above transaction in your PayU dashboard too

Time taken: 2 - 3 days

### CCAvenue

Contact us

### EBS

Contact us

### Citrus

Contact us

### Atom 

Contact us