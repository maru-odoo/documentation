Before enabling Apple Pay in Odoo, you must register as an Apple Pay merchant. To do this:

- Enroll in the `Apple Developer Program <https://developer.apple.com/support/app-account>`_.
- In your developer account, navigate to the `merchant identifier list <https://developer.apple.com/account/resources/identifiers/list/merchant>`_
  and click the plus to create a new identifier.
- Select :guilabel:`Merchant IDs` and click :guilabel:`Continue`.
- Enter a short description and identifier. Click :guilabel:`Continue` followed by :guilabel:`Register`.

  .. note::

     It is recommended that you follow the reverse-domain name style string for your merchant ID. For example,
     the domain `myapp.odoo.sh` would correspond to the merchant ID `merchant.sh.odoo.myapp`.

- Open the merchant configuration page by clicking on the newly created identifier.
- Under :guilabel:`Apple Pay Payment Processing Certificate`, click :guilabel:`Create Certificate`.
- If a question appears, answer it and click :guilabel:`Continue`.
- |payment-processing-csr|
- Navigate back to the merchant identifier configuration page in your Apple developer account.
  Under :guilabel:`Apple Pay Merchant Identity Certificate`, click :guilabel:`Create Certificate`.
- Generate a merchant identity CSR.

  .. tabs::

    .. tab:: macOS

      Open :guilabel:`Keychain Access`. Then, do the following:

        - Navigate to :menuselection:`Keychain Access --> Certificate Assistant --> Request a Certificate From a Certificate Authority...`.
        - Enter your email address and the common name :guilabel:`merchant`. Select :guilabel:`Save to disk` and then click :guilabel:`Continue`.

      This file is the CSR that will be uploaded to Apple. You will also need to download your private key by doing the following:

        - Back in :guilabel:`Keychain Access`, locate the private key :guilabel:`merchant`. Right click on the key and click :guilabel:`Export "merchant"...`.
        - Make sure to select the file format `.p12` and then click :guilabel:`Save`.

    .. tab:: Linux

      Run the following command:
        
      .. code-block:: console

        $ openssl req -new -newkey rsa:2048 -nodes -keyout merchant.p12 -out CertificateSigningRequest.certSigningRequest

      If prompted, do not enter a password.

  .. danger::
    Do **not** share your merchant identity private key :file:`merchant.p12`.

- Upload the merchant identity CSR :file:`CertificateSigningRequest.certSigningRequest` to Apple. Click :guilabel:`Continue`,
  and then click :guilabel:`Download`.
- Navigate back to the merchant identifier configuration page. Under :guilabel:`Merchant Domains`, click :guilabel:`Add Domain`.
- Enter the domain for your Odoo website and then click :guilabel:`Save`.
- Download the domain verification file by clicking :guilabel:`Download`.

For more information, see `Apple's official documentation <https://developer.apple.com/help/account/configure-app-capabilities/configure-apple-pay-on-the-web/>`_.
