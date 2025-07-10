# PP_STANDARD :: IPN RESPONSE: INVALID (Solution)

From your `paypal.log` file check the parameter **`charset`** of the **`IPN REQUEST`**:

`PP_STANDARD :: IPN REQUEST: charset=windows-1253`  
`PP_STANDARD :: IPN RESPONSE: INVALID`

**SOLUTION**  
1. Login into your **PayPal** account.
2. Click on your name (clicking the little person icon in the upper right hand corner).
3. Select **Account Settings**.
4. Select **Website payments** from the left vertical menu.
5. Then click the **Update** link next to **PayPal button language encoding** (Set the language your website uses.).
6. In **Language Encoding** click on **More Options**.
7. After **More Encoding Options** select `UTF-8` from the drop down menu and **Yes**.
8. Click the **Save** button.

Now check again your `paypal.log` file:

`PP_STANDARD :: IPN REQUEST: charset=UTF-8`  
`PP_STANDARD :: IPN RESPONSE: VERIFIED`
