# Take Home Challenge

As a Technical Support Engineer, you will communicate with clients primarily via email. Below are a few examples of support requests you might see. In a new gist, please respond to these challenges as if you were a TSE replying to a real client. The ideal response will be accurate, clear, and helpfully formatted.

## Challenge 1

Hi there,

I’m trying to get up and running with Plaid, and I need some help. When I try to create an `item`, Plaid returns an `INVALID_CREDENTIALS` error.
What am I doing wrong? Also, can you explain the difference between a `public_token` and `access_token`?

Thanks for the help.

Amy

## Challenge 2

Hi Plaid,

I noticed things aren’t quite adding up like they should.  The balance of my checking account  (account_id: ANJrPey64AtBe3ebD7oyfdRQMbboGBF1Dzy55) at the beginning of March was 11086.74.  I should be able to add all of the transactions that have happened between then and a transaction call I made on March 22nd (I’ve attached Plaids response to this call) to get the current balance of this account. However, the balance you are reporting for this account is 520.00 and when I sum transactions and add them with my original balance, I get a balance of 430.60.  What’s wrong with your transaction data?

Regards,
Samantha

[link to call response](https://gist.github.com/plaid-cj/9e929246c3e0be778c9531e147a34629)


## Challenge 3

Follow the [Plaid Quickstart](https://plaid.com/docs/quickstart/), setting up a local application, to create a new `transactions` `item`, using [Sandbox](https://plaid.com/docs/api/#sandbox) credentials.
Once you've authenticated for the application, please provide the following information:

* Names of the accounts, and their respective balances

* Item details

## Challenge 4

Write a script that uses Plaid’s `/institution/get` endpoint to output the total number of institutions that:
* support Plaid's identity product
* has the word "first" in the name

Please also include the script you used to arrive at these answers.
