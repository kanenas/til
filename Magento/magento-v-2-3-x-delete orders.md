# Magento v.2.3.x Delete Orders
```
SET FOREIGN_KEY_CHECKS=0;

TRUNCATE TABLE `prefix_sales_bestsellers_aggregated_daily`;
TRUNCATE TABLE `prefix_sales_bestsellers_aggregated_monthly`;
TRUNCATE TABLE `prefix_sales_bestsellers_aggregated_yearly`;
TRUNCATE TABLE `prefix_sales_creditmemo`;
TRUNCATE TABLE `prefix_sales_creditmemo_comment`;
TRUNCATE TABLE `prefix_sales_creditmemo_grid`;
TRUNCATE TABLE `prefix_sales_creditmemo_item`;
TRUNCATE TABLE `prefix_sales_invoice`;
TRUNCATE TABLE `prefix_sales_invoiced_aggregated`;
TRUNCATE TABLE `prefix_sales_invoiced_aggregated_order`;
TRUNCATE TABLE `prefix_sales_invoice_comment`;
TRUNCATE TABLE `prefix_sales_invoice_grid`;
TRUNCATE TABLE `prefix_sales_invoice_item`;
TRUNCATE TABLE `prefix_sales_order`;
TRUNCATE TABLE `prefix_sales_order_address`;
TRUNCATE TABLE `prefix_sales_order_aggregated_created`;
TRUNCATE TABLE `prefix_sales_order_aggregated_updated`;
TRUNCATE TABLE `prefix_sales_order_grid`;
TRUNCATE TABLE `prefix_sales_order_item`;
TRUNCATE TABLE `prefix_sales_order_payment`;
TRUNCATE TABLE `prefix_sales_order_status_history`;
TRUNCATE TABLE `prefix_sales_order_tax`;
TRUNCATE TABLE `prefix_sales_order_tax_item`;
TRUNCATE TABLE `prefix_sales_payment_transaction`;
TRUNCATE TABLE `prefix_sales_refunded_aggregated`;
TRUNCATE TABLE `prefix_sales_refunded_aggregated_order`;
TRUNCATE TABLE `prefix_sales_shipment`;
TRUNCATE TABLE `prefix_sales_shipment_comment`;
TRUNCATE TABLE `prefix_sales_shipment_grid`;
TRUNCATE TABLE `prefix_sales_shipment_item`;
TRUNCATE TABLE `prefix_sales_shipment_track`;
TRUNCATE TABLE `prefix_sales_shipping_aggregated`;
TRUNCATE TABLE `prefix_sales_shipping_aggregated_order`;
TRUNCATE TABLE `prefix_quote`;
TRUNCATE TABLE `prefix_quote_address`;
TRUNCATE TABLE `prefix_quote_address_item`;
TRUNCATE TABLE `prefix_quote_id_mask`;
TRUNCATE TABLE `prefix_quote_item`;
TRUNCATE TABLE `prefix_quote_item_option`;
TRUNCATE TABLE `prefix_quote_payment`;
TRUNCATE TABLE `prefix_quote_shipping_rate`;
TRUNCATE TABLE `prefix_sequence_invoice_1`;
TRUNCATE TABLE `prefix_sequence_invoice_2`;
TRUNCATE TABLE `prefix_sequence_order_1`;
TRUNCATE TABLE `prefix_sequence_order_2`;
TRUNCATE TABLE `prefix_sequence_shipment_1`;
TRUNCATE TABLE `prefix_sequence_shipment_2`;
TRUNCATE TABLE `prefix_sequence_creditmemo_1`;
TRUNCATE TABLE `prefix_sequence_creditmemo_2`;

SET FOREIGN_KEY_CHECKS=1;

```
