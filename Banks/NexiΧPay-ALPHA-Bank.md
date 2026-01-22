# NEXI XPay Greece

# Test environment
This section describes how to test your integrations in the XPay test environment.  
https://developer.nexigroup.com/xpaygreece/en-EU/docs/test-environment/

## Test environment
This section describes how to test your integrations in the XPay test environment.

### Overview
During the implementation phase of the integrations, as well as in the plugin tests, a test area is made available, with the data necessary to make calls to XPay and payment cards to simulate purchases, in particular:  
- **Api-Key**: the apikey is the key and identifying parameter of the merchant's terminal, which must be passed in the header of each API call. XPay provides a series of apikey divided by usable functionality. In production, this key can be recovered from the merchant's back office.
- **Payment cards**: in the test area it is possible to use specific cards to simulate positive or negative payments.

It is always recommended to run tests before going into production. Also for plugins, Nexi invites you to carry out payment tests to verify that there are no problems with the notifications sent by Nexi servers, which could be filtered by firewalls or other systems; to verify that there are no incompatibilities with third party plugins installed in the CMS.  

At this stage, in case of integration difficulties or errors returned by the plugins, please refer to the support contacts at the bottom left.  

### X-Api-Key
Here are the api-keys that can be used to perform tests with XPay:  
- Api-Key implicit accounting terminal: **8372f58a-3e55-45f4-a71b-b08b810757ae**  
- Api-Key terminal explicit accounting: **9ceae112-ad7b-4051-96e3-bc02746bb068**  
It is necessary to proceed with the payments using the cards made available in the section Payment cards, and use the TEST addresses made available in each API.  

In order to see the main differences between Implicit and Explicit accounting, please see directly the following section Accounting and Reversal Process.  

Instead if it was necessary to test Plug In, please here are the api-keys that can be used to perform tests with XPay for Plug In:  
- (**WE NEED THIS**) Api-Key implicit accounting terminal: **430f7949-bd32-44df-a4ac-1beb2029e2b2**  
- Api-Key terminal explicit accounting: **4d5941ec-ae5d-461c-8ab7-6040626703ad**  

### Payment Cards  
in the test area, it is possible to use specific cards to simulate positive or negative payments. Below are the cards that can be used to make payments in the test area.  

| Schema | Card No. | Expiry date | CVV | Result |
|--------|----------|-------------|-----|--------|
| Visa   | 4509 0345 4361 5006 | 10/2028 | 298 | OK |
| Mastercard | 5100 9908 1789 6004 | 04/2027 | 301 | OK |
| Visa | 43499 4019999 7007 | 12/2028 | 829 | KO |

# XPay Greece API reference
The XPay APIs provide a secure way to add online payments to your website or application by sending JSON over HTTPS.  
This is the complete API reference for the XPay APIs.  
https://developer.nexigroup.com/xpaygreece/en-EU/api/

# Οδηγίες για τη διεξαγωγή δοκιμών με IRIS:
- Εκκινήστε μια συναλλαγή χρησιμοποιώντας το endpoint `orders/hpp` και το ακόλουθο **κλειδί API**: 5a3bf3c3-fa05-4a6b-beac-2e09df4163ee.
- Μόλις ανοίξει ο σύνδεσμος πληρωμής, επιλέξτε τη μέθοδο πληρωμής IRIS και κάντε κλικ στο κουμπί **«ΔΗΜΙΟΥΡΓΙΑ ΚΩΔΙΚΟΥ QR»** για να εμφανιστεί ο κωδικός QR.
- Χρησιμοποιώντας ένα σαρωτή κωδικών QR (για παράδειγμα: https://qrscanner.net/), διαβάστε τη διεύθυνση που σχετίζεται με τον κωδικό QR και ανακτήστε τον αναγνωριστικό που εμφανίζεται μετά το `IRISCOM`.
**Παράδειγμα**: `IRISCOM52bb5e73-2ebd-4299-9ccf-e9714b9873fc` (αυτή είναι η συμβολοσειρά που περιέχεται στον κωδικό QR).
- Με τον αναγνωριστικό που ανακτήσατε, αποκτήστε πρόσβαση στον simulator: `https://test-iris.dias.com.gr/iris-ecommerce-demo/webBanking.html?authorizationRequestID=` 
(Πρέπει να προσθέσετε τον αναγνωριστικό που ανακτήσατε στο προηγούμενο βήμα μετά το σύμβολο = π.χ από το `IRISCOM52bb5e73-2ebd-4299-9ccf-e9714b9873fc` μόνο το `52bb5e73-2ebd-4299-9ccf-e9714b9873fc`).
- Τώρα θα αποκτήσετε πρόσβαση στον προσομοιωτή συναλλαγών.
- Για να ολοκληρώσετε την προσομοιωμένη συναλλαγή:
1. Επιλέξτε **SCT** στο πρώτο dropdown menu ,
2. Επιλέξτε έναν από τους παρεχόμενους IBAN στο δεύτερο dropdown menu,
3. Κάντε κλικ στο κουμπί **«Επιβεβαίωση της συναλλαγής»**.
- Μετά την επιβεβαίωση, μπορείτε να επιστρέψετε στo checkout page της NEXI, όπου η πληρωμή θα ολοκληρωθεί αυτόματα.
  
