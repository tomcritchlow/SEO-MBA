---
title: Executive Presence for SEOs - Course Beta
layout: page
---

Ready to join the live cohort beta version of the course? See here for all the details.

The course will run for 5 weeks, 90min zoom every Thursday at 2pm PT / 5pm ET on the following dates:

- April 15
- April 22
- April 29
- May 6
- May 13

Price is $200, which includes free access to the full self-paced course when it launches later this year.

Questions? Email me: tjcritchlow@gmail.com

<!-- Load Stripe.js on your website. -->
<script src="https://js.stripe.com/v3"></script>

<!-- Create a button that your customers click to complete their purchase. Customize the styling to suit your branding. -->
<div class="">
  
  <a id="checkout-button-price_1Id673L5622gsGmhuuzXenee" class="f4 link dim br3 ph3 pv2 mb2 dib white bg-seomba-red" href="#0">Checkout</a>
  
</div>

<div id="error-message"></div>

<script>
(function() {
  var stripe = Stripe('pk_test_51IbsfsL5622gsGmhJJ5dSs1jyz8DT7fHab9VY8OviLn3a8BuDoCmcItTB7fNB9x39hNVlXfDlgI8hdSLRwRuobfs00rkVJ2QO5');

  var checkoutButton = document.getElementById('checkout-button-price_1Id673L5622gsGmhuuzXenee');
  checkoutButton.addEventListener('click', function () {
    /*
     * When the customer clicks on the button, redirect
     * them to Checkout.
     */
    stripe.redirectToCheckout({
      lineItems: [{price: 'price_1Id673L5622gsGmhuuzXenee', quantity: 1}],
      mode: 'payment',
      /*
       * Do not rely on the redirect to the successUrl for fulfilling
       * purchases, customers may not always reach the success_url after
       * a successful payment.
       * Instead use one of the strategies described in
       * https://stripe.com/docs/payments/checkout/fulfill-orders
       */
      successUrl: 'https://seomba.com/thankyou',
      cancelUrl: 'https://seomba.com/cancelled',
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