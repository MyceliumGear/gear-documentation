This section describes some basic things about payment processing, as well as introduces terms that will be used in the following sections. Some things described here are common to all payment processors, whereas others may not be. After reading this section, you should have a good general understanding of how Mycelium Gear works, and will be able to proceed to the next sections.

## Why do you need a payment processor?
A payment processor is used to handle payments for you — charge credit cards, for example — and then report back to your site or online store when a payment is completed. When a user clicks "Pay" on your site, you redirect them to a special payment page on the payment processor website where they can input their credit card information and pay. Then, when they complete (or cancel) the payment, the payment processor lets your site know via a callback (sometimes called a webhook) and transfers the information about the payment by issuing an http request to your site. It is then your site's duty to receive that information and process it.

## How do payment processors usually work?
For example, suppose you have a website called worldsbestshoes.com that accepts payments through VeryPay.com, a credit card payment processor. A user picks his shoes, adds them to the "cart" on the site, and clicks "Complete purchase." At this point, you redirect him to the

```text
https://verypay.com/order/08ccaf5cd48628fb69900d7295cd46de5ac97dc3d798816f550a266f3eec01e1
```

There, the user sees a form into which he can type his credit card info. Once he finishes entering it, he clicks "Pay." As soon as he does that, VeryPay connects to his credit card company's API and attempts to charge the card. If the operation was successful, it redirects the user back to your website (or shows him the button which will redirect him there manually) and also issues a callback (webhook) to

```text
POST https://worldsbestshoes.com/payments/callback
```
where it sends (via POST parameters) all the info about the payment. If the payment fails, it lets the customer know, and also issues a callback to the same URL at your site, but this time the payment info contains information about the fact that the payment failed.

Your site then receives the payment information and, depending on whether it is okay or not, decides what to do. If the payment went through, it marks the order in its own database as paid, and then your shipping department can start packing the shoes. Or it may mark it as "payment failed," in which case you would probably want to offer your customer an option of trying again with a different credit card.

## How is Bitcoin payment processing different?
The described process is almost identical to Bitcoin payments. The only difference is that a customer doesn't need to provide any sensitive information, like a credit card number. Instead, on the payment page, he sees a Bitcoin address (both written and as a QR code) and then can use his wallet to send money to that address. It is then the payment processor's job to detect that the payment was made, notify the merchant, and redirect the customer back to the merchant site. This is exactly what Mycelium Gear does.

## Handling the money
The important question is: where does the money go when a payment is made? Traditionally, with credit card payment processors, the money first goes from the customer's bank account to the payment processor's bank account, and only then goes to the merchant. The problem with this system is that the payment processor has to accept and temporarily store the money on behalf of many different merchants, and be very confident in its ability to protect that money. The merchant on the other hand must be willing to trust the payment processor. Luckily, with Bitcoin, you can decouple storage of money and payment processing. Using BIP32, Mycelium Gear can generate a new address from a public key you get from your Bitcoin wallet (either Mycelium, or Electrum) for each payment invoice. That way, the money paid by a customer always goes directly from the customer's wallet into the merchant's wallet, while the payment processor simply watches the blockchain and checks whether that particular address received the bitcoins. Merchants don't have to trust their payment processor and don't risk losing the money that is held on their behalf, and the merchant processor doesn't have to worry about the costs associated with securely storing money and customer data.

Because of this, it is best to think of Mycelium Gear as a payment notification system rather than a payment processor. We only watch the blockchain, we don't actually hold anyone's money.

## Terminology
The next sections will explain exactly how you can integrate payment processing into your website or app. However, it is a good idea to get familiar with the terms that will be used first.

  * _Payment processor_ is a specialized software or service that integrates into your website and notifies it when a payment is made. For Bitcoin payment processing, Mycelium Gear takes care of exchange rate conversion, various Bitcoin denominations, generating new bitcoin addresses, and monitoring the blockchain for payments. Note that sometimes payment processors are also called payment gateways. These terms are synonymous, however a gateway in our terminology will have a slightly more specific meaning.

  * A _Gateway_ is an instance that is created in Mycelium Gear that processes all the payments for a particular store. For example, you as a merchant may have two online stores. You would then create two gateways in Mycelium Gear admin panel, and use each one for its respective website.

  * An _Order_ is created each time your customer decides to pay. An order is a data set that contains information such as an amount to be paid, a bitcoin address to which the payment will be sent, and many other things. Each order is stored in our database, and is associated with a particular Gateway and merchant. An order also has a status that can change. For example, a "paid" status is set when the associated Bitcoin address receives the correct amount.

  * A _Callback_ is an http request that is issued by the payment processor whenever an order changes its status. Each gateway allows you to set a URL to which this request is issued. You have to program your site so that it can process this request, extract the necessary information, and make proper use of it.
