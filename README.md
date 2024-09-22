# Pizza-Case-Study---MYSQL


# Case Study - PIZZA RUNNER - MYSQL 

**Introduction :**

Danny started by recruiting “runners” to deliver fresh pizza from Pizza Runner Headquarters (otherwise known as Danny’s house) and also maxed out his credit card to pay freelance developers to build a mobile app to accept orders from customers.



**Technology Used :**

* MYSQL


**Case Study Questions :**

**1.How many pizzas were ordered?**

      ANS :   select count(pizza_id) AS Total_pizza from customer_orders;
      
![image](https://github.com/user-attachments/assets/5091902e-0b21-433d-81e0-bfabaf27e71c)


**2. How many unique customer orders were made?****

       ANS : Select  distinct(customer_id) , count(order_id) from customer_orders group by customer_id;

![image](https://github.com/user-attachments/assets/56f82604-8311-43e6-b4f3-5cf64b350d5c)



**3. How many successful orders were delivered by each runner?**

        ANS :     Select runner_id , 
        COUNT(Distinct ro.order_id) 
        From customer_orders as co 
        join runner_orders as ro on co.order_id = ro.order_id
        where pickup_time<>"null"
        Group by runner_id;

![image](https://github.com/user-attachments/assets/dcf02469-2a4a-4bb9-81fa-d1212ae5e861)



**4. How many of each type of pizza was delivered?**

         ANS :  Select pn.pizza_name, 
         count(co.pizza_id)
         From runner_orders as ro 
        join customer_orders as co on ro.order_id = co.order_id
        join pizza_names as pn on co.pizza_id = pn.pizza_id
        where pickup_time<>"null"
        group by pizza_name;

![image](https://github.com/user-attachments/assets/184c82bb-9fe4-459c-be06-8b5a393b9003)



**5. How many Vegetarian and Meatlovers were ordered by each customer?**

        ANS : Select pn.pizza_name, 
        co.customer_id, 
        count(co.pizza_id) 
        from runner_orders as ro
        join customer_orders as co on ro.order_id = co.order_id
        join pizza_names as pn on co.pizza_id = pn.pizza_id 
        group by pn.pizza_name,
        co.customer_id
        order by pizza_name;

![image](https://github.com/user-attachments/assets/47d99c93-f9ae-4238-97cf-09afa62ff362)











