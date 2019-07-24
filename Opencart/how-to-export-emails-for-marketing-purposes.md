# Export emails for Marketing Purposes

`SELECT email FROM oc_customer ORDER BY customer_id`  
`SELECT email FROM oc_customer WHERE newsletter = 1` *< The customer said **YES** to newsletter*  
`SELECT DISTINCT(email) FROM oc_order WHERE order_status_id = 5` *< This is for **COMPLETE** orders*

`SELECT email_id FROM oc_subscribe` *< This TABLE comes with an extension about newsletter*  
