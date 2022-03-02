
--Get all customers and their addresses.

SELECT customers, addresses
from customers
JOIN addresses ON customers.id = addresses.customer_id
;
--Get all orders and their line items (orders, quantity and product).
SELECT orders, line_items.quantity, line_items.product_id, line_items.order_id 
FROM line_items
JOIN orders on orders.id = line_items.order_id;

--Which warehouses have cheetos?
SELECT warehouse, products.description from warehouse
JOIN warehouse_product on warehouse_product.warehouse_id = warehouse.id
JOIN products on products.id = warehouse_product.product_id
WHERE products.description = 'cheetos'

;
--Which warehouses have diet pepsi?
SELECT warehouse from warehouse
JOIN warehouse_product on warehouse_product.warehouse_id = warehouse.id
JOIN products on products.id = warehouse_product.product_id
WHERE products.description = 'diet pepsi'

;


--Get the number of orders for each customer. NOTE: It is OK if those without orders are not included in results.

SELECT COUNT(*)  orders, customers.first_name, customers.last_name from orders
JOIN addresses on orders.address_id = addresses.id
JOIN customers on customers.id = addresses.customer_id
GROUP BY customers.first_name, customers.last_name
;


--How many customers do we have?
SELECT COUNT(*)  as "Number of Customers" from customers
;


--How many products do we carry?
SELECT COUNT(*)  AS "Number of Products" from products
;

--What is the total available on-hand quantity of diet pepsi?
SELECT count(*) as "Quantity of Pepsi" from products
JOIN warehouse_product on warehouse_product.on_hand = products.id
WHERE products.description ='diet pepsi'
;



