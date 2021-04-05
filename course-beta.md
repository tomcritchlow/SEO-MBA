---
---


<!-- Load Stripe.js on your website. -->
<script src="https://js.stripe.com/v3"></script>

<!-- Create a button that your customers click to complete their purchase. Customize the styling to suit your branding. -->
<div class="ph3">
  
  <a id="checkout-button-price_1Ibss8L5622gsGmh54W16XLz" class="f6 link dim br3 ph3 pv2 mb2 dib white bg-seomba-red" href="#0">Checkout</a>
  
</div>


<div id="error-message"></div>

<script>
(function() {
var stripe = Stripe('pk_live_51IbsfsL5622gsGmhUlHqPNCa70Ac3I3l6pSeEenMhSzugJJGvXaVuD9U6rlgq1RVse1J4phWEGLGwIAoH8zSo2GL00kOBE7wRT');

var checkoutButton = document.getElementById('checkout-button-price_1Ibss8L5622gsGmh54W16XLz');
checkoutButton.addEventListener('click', function () {
/*
* When the customer clicks on the button, redirect
* them to Checkout.
*/
stripe.redirectToCheckout({
lineItems: [{price: 'price_1Ibss8L5622gsGmh54W16XLz', quantity: 1}],
mode: 'payment',
/*
* Do not rely on the redirect to the successUrl for fulfilling
* purchases, customers may not always reach the success_url after
* a successful payment.
* Instead use one of the strategies described in
* https://stripe.com/docs/payments/checkout/fulfill-orders
*/
successUrl: 'https://seomba.com/thankyou',
cancelUrl: 'https://seomba.com/canceled',
})
.then(function (result) {
if (result.error) {
/*
* If `redirectToCheckout` fails due to a browser or network
* error, display the localized error message to your customer.
*/
var displayError = document.getElementById('error-message');
displayError.textContent = result.error.message;
}
});
});
})();
</script>