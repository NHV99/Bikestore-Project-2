select 

ord.order_id ,

CONCAT (cus.first_name, ' ', cus.last_name) as cust_full_name ,

cus.city ,

cus.state ,

ord.order_date ,

sum(item.quantity) as total_units ,

sum (item.quantity * item.list_price) as revenue ,

p.product_name ,

pc.category_name ,

pb.brand_name ,

ss.store_name

from sales.orders ord

join sales.customers cus

on ord.customer_id = cus.customer_id

join sales.order_items item

on ord.order_id = item.order_id

join production.products p

on item.product_id = p.product_id

join production.categories pc

on p.category_id = pc.category_id


join production.brands pb

on p.brand_id = pb.brand_id

join sales.stores ss

on ord.store_id = ss.store_id

group by 

ord.order_id ,

CONCAT (cus.first_name, ' ', cus.last_name)  ,

cus.city ,

cus.state ,

ord.order_date ,

p.product_name ,

pc.category_name ,

pb.brand_name ,

ss.store_name