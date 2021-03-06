Integrating [Stripe's Checkout](https://stripe.com/docs/checkout/tutorial) with **custom pay button** to your react app is actually pretty simple. You don't need to install third party [package](https://github.com/azmenak/react-stripe-checkout). This project (bootstrapped with [Create React App](https://github.com/facebookincubator/create-react-app)) shows how to do it with a few lines of codes.

[DEMO VIDEO](https://youtu.be/UAKriPqatCA)

1. Add the following to [public/index.html](https://github.com/nicnocquee/react-stripe-checkout/blob/master/public/index.html#L30)

```html
 <script src="https://checkout.stripe.com/checkout.js"></script>
```

2. Configure the Stripe Checkout in any component you want. In this sample, it's in [App.js](https://github.com/nicnocquee/react-stripe-checkout/blob/master/src/App.js#L15).

```javascript
this.stripeHandler = window.StripeCheckout.configure({
  key: "<YOUR_STRIPE_PUBLISHABLE_KEY>",
  image: 'https://stripe.com/img/documentation/checkout/marketplace.png',
  locale: 'auto',
  token: this.onGetStripeToken.bind(this)
});
```

3. Open the Checkout modal when [the pay button is clicked](https://github.com/nicnocquee/react-stripe-checkout/blob/master/src/App.js#L39).

```javascript
this.stripeHandler.open({
  name: 'My Delightful Shop',
  description: 'An awesome product',
  amount: 1000, // 10 USD -> 1000 cents
  currency: 'usd',
  opened: onCheckoutOpened.bind(this)
});
```

4. [Send the Stripe token to your server](https://github.com/nicnocquee/react-stripe-checkout/blob/master/src/App.js#L23) when your customer's card has been validated.
5. ...
6. **PROFIT!** 🤑💰💵💸🌈🚀

# Getting Started

- Clone this repo.
- `yarn install` or `npm install`
- Open `src/App.js` and replace `<YOUR_STRIPE_PUBLISHABLE_KEY>` with your [Stripe's publishable key](https://dashboard.stripe.com/account/apikeys).
- `yarn run`

[@nicnocquee](https://twitter.com/nicnocquee).