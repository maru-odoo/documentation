To set up Apple Pay in Odoo:

- Install the `express_payment_|payment-provider-code|_apple` Odoo module.
- Open the Odoo configuration page for Authorize.Net.
- Enter your Apple Pay merchant ID in the field :guilabel:`Merchant ID`.
- Upload the domain verification file :file:`apple-developer-merchantid-domain-association.txt`.
- Upload the merchant identity certificate :file:`merchant_id.cer`.
- Upload the merchant identity key :file:`merchant.p12`.
- Back in your Apple Developer Account, click the :guilabel:`Verify` button on the domain
  verification page.

At this point, the Apple Pay express checkout option will appear in the eCommerce cart.
