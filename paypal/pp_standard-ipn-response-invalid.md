# PP_STANDARD :: IPN RESPONSE: INVALID (Solution)

From your `paypal.log` file check the parameter **`charset`** of the **`IPN REQUEST`**:

`PP_STANDARD :: IPN REQUEST: charset=windows-1253`  
`PP_STANDARD :: IPN RESPONSE: INVALID`

**SOLUTION**  
1. Login to your **PayPal** account
2. Click on **Profile and Settings** (gear button) in the upper right hand corner next to **Log Out**.
3. Go to **My Selling Tools**
4. At the bottom of the screen click on **PayPal button language encoding**
5. Press **More Options**
6. Change both drop-downs to **UTF-8**. The "_Do you want to use the same encoding for data sent from PayPal to you (e.g., IPN, downloadable logs, emails)?"_ radio button should be **YES**
7. Save

Now check again your `paypal.log` file:

`PP_STANDARD :: IPN REQUEST: charset=UTF-8`  
`PP_STANDARD :: IPN RESPONSE: VERIFIED`
