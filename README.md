# Ecommerce

Data Analysis of Olist Store (Brazilian E-Commerce)

Análise de Dados da Olist Store, um e-commerce brasileiro

Got data stored as CSV file so uploaded it to BigQuery for exploratory analysis,
then created a Query to build a dashboard with Looker Studio.

```SQL
SELECT  
 c.customer_id,
 c.customer_unique_id,
 c.customer_city,
 c.customer_state,
 c.customer_zip_code_prefix,
 o.order_id,
 oi.order_item_id,
 oi.price,
 oi.product_id,
 oi.seller_id,
 oi.freight_value,
 op.payment_type,
 op.payment_value,
 p.product_category_name,
 ct.product_category_name_english
FROM brazilian_ecommerce.customers c
LEFT JOIN brazilian_ecommerce.geolocation g ON c.customer_zip_code_prefix = g.geolocation_zip_code_prefix
LEFT JOIN brazilian_ecommerce.orders o ON c.customer_id = o.customer_id
LEFT JOIN brazilian_ecommerce.order_items oi ON o.order_id = oi.order_id
LEFT JOIN brazilian_ecommerce.order_payments op ON o.order_id = op.order_id
LEFT JOIN brazilian_ecommerce.products p ON oi.product_id = p.product_id
LEFT JOIN brazilian_ecommerce.sellers s ON oi.seller_id = s.seller_id
LEFT JOIN brazilian_ecommerce.category_translation ct ON p.product_category_name = ct.product_category_name;
```

Dashboard

![imagem_2023-09-16_201600738](https://github.com/Ronan-Alencar/Dados_ANP/assets/133599706/1b1e45c7-7090-4996-9ec5-6dcb3ed1fefb)

https://lookerstudio.google.com/reporting/a14378d6-916b-4515-9dfd-34f853c118a5
