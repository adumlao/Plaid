# Take Home Challenge

As a Technical Support Engineer, you will communicate with clients primarily via email. Below are a few examples of support requests you might see. In a new gist, please respond to these challenges as if you were a TSE replying to a real client. The ideal response will be accurate, clear, and helpfully formatted.

## Challenge 1

Hi there,

I’m trying to get up and running with Plaid, and I need some help. When I try to create an `item`, Plaid returns an `INVALID_CREDENTIALS` error.
What am I doing wrong? Also, can you explain the difference between a `public_token` and `access_token`?

Thanks for the help.

Amy

### ALFONSO - CHALLENGE 1 RESPONSE

Hi Amy-

I'm happy to help you get set up with Plaid.

Let's start with the `INVALID_CREDENTIALS` error you are receiving when trying to create an `item`.  You are receiving this error message because the financial institution you are trying to access cannot validate the credentials you provided.  I suggest double checking if the login details you are providing are correct.  If you are using the Plaid Link to initialize, re-enter your credentials in case of a typo or missing characters.

Check out our [list of error messages](https://support.plaid.com/hc/en-us/articles/360012859833-Handling-Plaid-Errors), as well as our list of [`Item` specific error codes](https://plaid.com/docs/#item-errors).


Regarding `public_tokens` and `access_tokens`:

A public token is returned by Plaid Link when creating an item. It is for one-time use and expires after 30 minutes. A public token is generated the `POST /item/public_token/create` endpoint.
- [Read more about public tokens here.](https://plaid.com/docs/#creating-public-tokens)

On the other hand, an access token is a rotatable token affiliated with an item.  It is used to make product requests on behalf of an item. You can generate an access token by exchanging a public token (this public token becomes invalidated once it has been successfully exchanged for an access token).
- [Read more about the difference between public and access tokens here.](https://support.plaid.com/hc/en-us/articles/360008413793-Access-token-and-Item-FAQ#What%20are%20the%20differences%20among%20a%20public_token,%20access_token,%20and%20an%20item?)
- [Read more about the exchange token flow here.](https://plaid.com/docs/#exchange-token-flow)


I hope all of this information has been helpful to you.  Should you have any questions, feel free to reach out to me- I would be happy to assist!

All the best,

Alfonso Dumlao








## Challenge 2

Hi Plaid,

I noticed things aren’t quite adding up like they should.  The balance of my checking account  (account_id: ANJrPey64AtBe3ebD7oyfdRQMbboGBF1Dzy55) at the beginning of March was 11086.74.  I should be able to add all of the transactions that have happened between then and a transaction call I made on March 22nd (I’ve attached Plaids response to this call) to get the current balance of this account. However, the balance you are reporting for this account is 520.00 and when I sum transactions and add them with my original balance, I get a balance of 430.60.  What’s wrong with your transaction data?

Regards,
Samantha

[link to call response](https://gist.github.com/plaid-cj/9e929246c3e0be778c9531e147a34629)

### ALFONSO - CHALLENGE 2 RESPONSE

Hi Samantha,

Thank you for providing me with your account information- that made it easier for me to investigate the balance discrepancy.

It looks like you have a pending balance of `$89.40` from `Sparkfun` on `2019-03-16`.  The id for this transaction is `E2B4x3U7M23Zz9w3XCMn21PpvBh4SAOMk3Q`.

The available balance is the amount of funds available to be withdrawn from an account, as determined by the financial institution. The available balance typically, but not always, equals the current balance less any pending outflows plus any pending inflows.  Whenever a transaction has the property `"pending": true`, it identifies the transaction as pending or unsettled; pending transaction details (description, amount) may change before they are settled.

- [Read more about balances here.](https://plaid.com/docs/#balance)


I hope all of this information has been helpful to you.  Should you have any questions, feel free to reach out to me- I would be happy to assist!

All the best,

Alfonso Dumlao

## Challenge 3

Follow the [Plaid Quickstart](https://plaid.com/docs/quickstart/), setting up a local application, to create a new `transactions` `item`, using [Sandbox](https://plaid.com/docs/api/#sandbox) credentials.
Once you've authenticated for the application, please provide the following information:

* Names of the accounts, and their respective balances

* Item details

### ALFONSO - CHALLENGE 3 RESPONSE

`ITEM_ID:` wk8x5348m1CwRMMkK5XViJxPnrllWjtr68XX6
`ACCESS_TOKEN:` access-sandbox-40ce2de0-704c-4842-a7ca-46f0bbb5576e

* Accounts and their balances from `/accounts/get`

| Name	| Balances |
|:------------------|:------:|
| Plaid Checking |	$100 |
| Plaid Saving |	$200 |
| Plaid CD |	$1000 |
| Plaid Credit Card |	$410 |
| Plaid Money Market |	$43200 |
| Plaid IRA |	$320.76 |
| Plaid 401k |	$23631.9805 |
| Plaid Student Loan |	$65262 |

* Item details from `/item/get`

`Institution name:`	TD Bank
`Billed products:`	transactions
`Available products:`	assets, auth, balance, identity, income


## Challenge 4

Write a script that uses Plaid’s `/institution/get` endpoint to output the total number of institutions that:
* support Plaid's identity product
* has the word "first" in the name

Please also include the script you used to arrive at these answers.
