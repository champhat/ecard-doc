# Start up

Pledg's dashboard allows you to configure your means of payment and track the payments made to your various accounts.

## Account creation - first connection

If you do not have an account, you can create one at [test dashboard (staging)](https://staging.dashboard.ecard.pledg.co/#/).

When integration is complete, you can request activation of your account at support@pledg.co, and we will give you access to your [production dashboard](https://dashboard.ecard.pledg.co/#/).

![Capture_Login.png](https://pledg-assets.s3-eu-west-1.amazonaws.com/ecard-plugin-doc/dashboard/fr/Capture_Login.png)

To log in :

* Click on "Log in"
* Reset the password by entering your email address after clicking on :
  
![Capture_ForgotPassword.png](https://pledg-assets.s3-eu-west-1.amazonaws.com/ecard-plugin-doc/dashboard/fr/Capture_ForgotPassword.png)

* Click on the disposable link sent by email and specify a new password
* Login again with the chosen password

## General presentation of the dashboard

Once you have logged in, you will be taken to the main interface of the Pledg dashboard.

![GeneralView.png](https://pledg-assets.s3-eu-west-1.amazonaws.com/ecard-plugin-doc/dashboard/en/GeneralView.png)

Here you will find :

1. The list of accounts (your Pledg payment means) with a short description of their type (e.g. "2x Installation" for a payment split into two instalments). Click on one of the accounts / Pledg payment methods to view it.
2. Click on "Create an account" to create a new Pledg payment method.
3. You can change the language of the dashboard
4. Click on "Logout" to exit the dashboard.

## Create a new means of payment

To create a new payment method, click on the "Add an account" button at the bottom of the list of payment methods.

![CreerCompte.png](https://pledg-assets.s3-eu-west-1.amazonaws.com/ecard-plugin-doc/dashboard/en/CreerCompte.png)

Fill in all the fields then click on the "Create" button:

* Company name
* Logo URL
* Iframe CSS URL (if you wish to customize the for where customers enter their card details, can enter here the URL where the CSS is hosted, or Pledg can host it for you)
* Type of payment
* IBAN
* BIC

| Payment type in English | Payment type in French | Setup
| ----------- | ----------- | ----------- |
| Deferred | Deferred |  |
| Split | Installation | Fill in the field "Number of maturities" (cannot exceed 12x) |
| With down payment | Down payment | Fill in the fields "Percentage of down payment" and "Max number of days before capturing the balance" |

* Signature required: tick the box if you want to sign the exchanges with a secret key (additional level of security).

?????? All fields are required (including logo).

Once created, the new Pledg account / payment method will appear in the list of accounts. By clicking on it, you will find its characteristics.

?????? This newly created account is not **directly functional in production**. Actions are necessary by Pledg to complete its configuration and update the user contract.

## Consulting an account

In the accounts, click on the account / Pledg payment method you want to view.

![ConsulterCompte.png](https://pledg-assets.s3-eu-west-1.amazonaws.com/ecard-plugin-doc/dashboard/en/ConsulterCompte.png)

On the right side of the screen are displayed :

* The main characteristics of the means of payment
* The list of the last payments
* The list of the last transfers

### Key Account Features

![PrincipalesCaracteristiquesCompte.png](https://pledg-assets.s3-eu-west-1.amazonaws.com/ecard-plugin-doc/dashboard/en/PrincipalesCaracteristiquesCompte.png)

* UID: the technical identifier of your payment method also called MerID
* Key: the private key of your means of payment; it allows you to authenticate and secure the exchange of information with a signature. ?????? the key is optional and its use is reserved for developers.
* Type: the type of payment configured: "Split", "Deferred" ...
* Employees: the number of employees with access to the account (in this example: one employee).
* Change button: by clicking on the button you can change some of the account information.
* Generate purchase link button : See section [Purchase links](https://docs.pledg.co/en/guide/purchase-link.html)

### Changing the features of an account

Click on the small "change pencil" icon located under the main account features staff.

![InfosCompte.png](https://pledg-assets.s3-eu-west-1.amazonaws.com/ecard-plugin-doc/dashboard/en/InfosCompte.png)

Modify the desired information and click on the "Modify" button.

The following fields can be modified:

* "Brief description": text giving a brief description of your account (in this example "2x" for a payment split in two)
* "Logo URL": select a file with your logo and upload it.
* "CSS URL" : page where the iframe's CSS is hosted (Pledg can host it for you)
* "Type of payment" (**not modifiable**): parameter indicating the type of payment (in this example "Split")
* "Number of instalments" (**not modifiable**): the number of instalments of your means of payment in the case of a split payment (in this example "2 instalments"); for information purposes, on the right you will find the charges applied to the buyer (in this example 0.5%)
* "Signature required": activate or deactivate the signature for this account

Below the editable account characteristics, you can add/delete and view the list of collaborators who have access to the account.

## Viewing last payments

In the list of accounts, click on the account / payment method for which you want to view the latest payments.

![Capture_CompteDerniersPaiements_Red.png](https://pledg-assets.s3-eu-west-1.amazonaws.com/ecard-plugin-doc/dashboard/fr/Capture_CompteDerniersPaiements_Red.png)

The list of the last five payments is displayed with :

* The amount and its currency
* Payment status :

  - `COLLECTING` : Payment accepted
  - `PRIMARY_KO`: Transaction refused
  - `SCORING_KO` : Transaction refused (customer has unsufficient score)
  - `CANCELLED` : Transaction cancelled

* The merchant's reference communicated to the Pledg payment
* Customer identification: email and phone number if necessary.
* The date of payment

### Displaying all payments

Click on "View All" to view all payments made to this account.

![Capture_CompteTousPaiements_Red.png](https://pledg-assets.s3-eu-west-1.amazonaws.com/ecard-plugin-doc/dashboard/fr/Capture_CompteTousPaiements_Red.png)

Tools at the top of the list allow you to :

* Search for a payment by typing the merchant's reference number
* Filter the list by date, status and amount
* Export list items in CSV format

To obtain the details of a payment, click on the eye to the right of the payment line.

### Viewing the details of a payment

Click on the eye of the payment you want to view.

![Capture_PurchaseDetailMain_Red.png](https://pledg-assets.s3-eu-west-1.amazonaws.com/ecard-plugin-doc/dashboard/fr/Capture_PurchaseDetailMain_Red.png)

The main features of the payment are followed by the sections :

* **Detail** :																							 
  - Date: the date on which the transaction was made
  - Reference: the reference transmitted to Pledg from your merchant site.
  - Transfer ("transfer" mode only): the reference of the transfer made to the merchant to pay for the purchase.
  - Virtual card (only for `back` and `front` modes): the status of the virtual card with our bank. The meaning of the status is detailed below :
  
| Status | Meaning |
| ----------- | ----------- |
| `AUTHORIZED ON TIME` | the bank received a request for authorization from the merchant within 3 minutes of the card generation | |
| `NOT_AUTHORIZED_ON_TIME` | the bank did not receive any authorisation request from the merchant even after 3 minutes |
| `AUTHORIZED` | the bank received a request for authorization from the merchant |
| `DEBITED` | the bank has received a debit request from the merchant |
| `DEBITED_LOWER_AMOUNT` | the bank has received a request from the merchant to debit an amount less than the authorised amount |
| `DEBITED_GREATER_AMOUNT` | the bank has received a debit request from the merchant for an amount greater than the authorised amount |
| `NOT DEBITED` | the bank has received a debit request from the merchant for an amount greater than the authorised amount |
| `CREDITED` | the bank received a credit application from the merchant |

* **Maturity dates**
  
  - For a split payment, you will find the list of due dates, amounts and associated statuses:
![Capture_PurchaseDetailEcheance.png](https://pledg-assets.s3-eu-west-1.amazonaws.com/ecard-plugin-doc/dashboard/fr/Capture_PurchaseDetailEcheance.png)
  - For a deferred payment, you will find the due date with its date, amount and associated status:
![Capture_PurchaseDetailEcheance_2.png](https://pledg-assets.s3-eu-west-1.amazonaws.com/ecard-plugin-doc/dashboard/fr/Capture_PurchaseDetailEcheance_2.png)

* **Refunds / Refunds**

Partial or full refunds can be made on payment. You have the option of monitoring the status of refunds or making a refund request for accounts set up in transfer mode.

![Capture_PurchaseDetailRefund.png](https://pledg-assets.s3-eu-west-1.amazonaws.com/ecard-plugin-doc/dashboard/fr/Capture_PurchaseDetailRefund.png)

If repayments have been made, the list of repayment transactions is displayed.

![Capture_Refund_List.png](https://pledg-assets.s3-eu-west-1.amazonaws.com/ecard-plugin-doc/dashboard/fr/Capture_Refund_List.png)

To refund a customer, the operation is different between the modes using a virtual card (`front` and `back`) and the `transfer` mode:

* Front and back mode (with virtual card): connect to your PSP (Payment Service Provider) and re-credit the virtual card; the customer's bank card will be re-credited afterwards.
* Mode `transfer`: the claim is made from the dashbord Pledg :

    - Click on the button "Request a refund".
    - Fill in the amount you want to reimburse
    - Click on "Request a refund"; a notification will tell you that the refund has been taken into account.

![Capture_Refund_Demande.png](https://pledg-assets.s3-eu-west-1.amazonaws.com/ecard-plugin-doc/dashboard/fr/Capture_Refund_Demande.png)

**Notes concerning the `transfer` mode**
::: tip
To refund the **full** amount of a customer's order, you must fill in the total amount of the customer's order; If you fill in the amount corresponding to the due dates drawn, this will correspond to a partial refund and the other due dates will be debited.
To refund **partially** a customer's order, enter the amount you want to refund. This partial request will not necessarily produce a credit on the customer's credit card. The amount you want to refund will reduce or cancel the customer's most distant debit dates in priority.
:::

::: tip
Refunds are usually effective at **D+1** and will appear at that time in the payment refund list in the dashboard.
:::

## View latest transfers

For accounts set up in `transfer' mode, i.e. a daily transfer is sent to the merchant for an amount corresponding to all the orders of the day, the list of transfers made can be consulted.

This section allows you to reconcile the payment of your orders with the transfers you receive on your bank account.

![Capture_DerniersVirements_Red.png](https://pledg-assets.s3-eu-west-1.amazonaws.com/ecard-plugin-doc/dashboard/fr/Capture_DerniersVirements_Red.png)

Information:

* Amount: the amount of the transfer
* Status: `sent` when the transfer has been successfully issued
* Reference: the reference of the transfer transmitted
* Date: the date of the transfer

Click on the "View All" button to see a list of all transfers. You can then view the details of a transfer with a list of the orders concerned.

![Capture_DerniersVirements_Details_Red.png](https://pledg-assets.s3-eu-west-1.amazonaws.com/ecard-plugin-doc/dashboard/fr/Capture_DerniersVirements_Details_Red.png)

In the "Payments" section, you can consult the list of corresponding orders and the reference you have sent to Pledg.

When the amount is negative, this corresponds to a refund. When you make a refund request, we take the refund amount from your bank account and credit the customer's credit card.

If you have any questions francois.delaitre@pledg.co ????
