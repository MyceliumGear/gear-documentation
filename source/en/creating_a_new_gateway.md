The first thing you will want to do after you sign up (and read the docs, of course) is to create a new <i>gateway</i>. Gateways are entities that create orders and process payments for a particular store. So, if you only have one online store, you will need to create one gateway.
## Filling the form

To create a gateway, simply go to this page and fill out the form. Almost all of the fields are optional, and are explained below.

  * _Name_ is what your customers will see at the top of the payment page when they try to make a purchase. It is also the name of the gateway that you see as a merchant in the admin panel. While it does not affect anything in particular, it's a good idea to put something meaningful in there.
    Confirmations required should typically be set to 0, unless you expect large payment amounts. In Bitcoin, each transaction is considered completely settled only when you have 6 confirmations (which may take about an hour). However, you can still assume with a degree of certainty that the payment will get processed and settled in one hour as soon as the transaction has been broadcasted to the Bitcoin network. You generally don't want your customers to wait, thus the current industry standard is to accept transactions with 0 confirmations. That way, as soon as your customer sends money from his wallet, we can detect that transaction and redirect him back to your website.

  * _BIP32 pubkey_ is the most important of the fields, and looks similar to this (beginning with xpub):

    ```text
    xpub6AHA9hZDN11k2ijHMeS5QqHx2KP9aMBRhTDqANMnwVtdyw2TDYRmF8PjpvwUFcL1Et8Hj59S3gTSMcUQ5gAqTz3Wd8EsMTmF3DChhqPQBnU
    ```  
 
    It is based on Bitcoin BIP32 standard, and is derived from your wallet's private key. Mycelium Gear uses it to generate new address for each new order. Not all wallets support BIP32, but two of the most popular ones — Mycelium and Electrum.

  * _Order expiration period_ is the period of time during which a customer has to pay for the order. If he does not pay in time, the order is considered expired. The default is 900 seconds (15 minutes) which is an industry standard.

  * _After payment redirect url_ is used to return the customer back to your website after a successful purchase. This could be a page specific to the order, or to their account.

  * When _auto redirect_ is checked, all users whose payments were successful are automatically redirected to the *After payment redirect url*.

  * _Active_ flag simply means that this gateway is currently ready to process payments. If you need to temporarily stop accepting payments, you can always come back to that form (edit the existing gateway) and uncheck that checkbox.

  * _Currency_ conversion options section allows you to choose what currency your order prices are displayed in, and which bitcoin price source to use to convert that value into the appropriate amount of bitcoins. The default setting is USD and you probably want to leave it that way, since the Bitcoin exchange rate can fluctuate substantially, making it inconvenient to set prices in BTC. The exchange rate provider fields allow you to choose which sources to use for the current exchange rate. Exchange rates are checked in the order set here, with subsequent providers only checked if the previous provider is unavailable for some reason.

  * _Additional info_ about the merchant block is completely optional, but we would prefer if merchants fill it, since this will help us provide our customers with better service. This information is not used for compliance — Mycelium Gear does not handle any money (just watches the transactions on the blockchain) and is not subject to AML/KYC — and we do not share this information with anyone.

## Getting the gateway secret

After you click the "Create gateway" button below the form, if all fields are valid, you will be redirected to the gateway info page and will be presented with a gateway secret. **You must write it down** as it will not appear again anywhere. If you ever lose that secret, you will need to come back to that form (edit the gateway) and check the "Regenerate secret" checkbox. However this will invalidate your previous secret and any of your online stores that were using it will have to update it to the new one.

The secret key is essentially a signature that all your requests to the gateway are signed with, which the gateway uses to verify that it's you who is talking to it, and not some impostor. We will explain how to use this secret key in detail in the next section.
