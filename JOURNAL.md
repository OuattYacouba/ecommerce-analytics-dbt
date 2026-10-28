# Journal de bord 
Projet: Une entreprise e-commerce qui veut piloter sa performance (bigquery-public-data.thelook_ecommerce.users)
ID du projet : ae-portfolio-512910

le grain des tables:
-  orders: une ligne = une commande
- orders_items: une ligne = un article dans une commande (une commande peut en avoir plusieurs)
- products: une ligne = un produit du catalogue
- users: une ligne = un client
Localisation: US

## Etape 1.1 - le 27/10/2026
1 - Combien y a-t-il de commandes?
Il y a 124669 commandes
SELECT 
count(order_id) as nb_commandes
FROM `bigquery-public-data.thelook_ecommerce.orders` 

2 - Quels statuts de commande existent, et combien de commandes par status?
Les status de commande existants et leurs nombres de commandes:
- Cancelled:18884 commandes
- Complete: 31031 commandes
- Processing:24754 commandes
- Returned:12570 commandes
- Shipped: 37430 commandes
Requêtes:
SELECT distinct
status,
count(order_id) as nb_commandes
FROM `bigquery-public-data.thelook_ecommerce.orders` 
GROUP BY status

3 - Quelles sont la première et la dernière date de commande?
La première date de commande est 2019-01-11 02:07:42 UTC et la dernière date de commande est 2026-10-27 00:30:01.750414 UTC
Requête:
SELECT
Min(created_at) as date_debut,
Max(created_at) as date_fin
FROM `bigquery-public-data.thelook_ecommerce.orders`

4 - Quel est le chiffre d'affaires total des articles, hors articles annulés ou retournés?
Le CA total des articles, hors articles annulés ou retournés est:8 061 545.088356
Requête:
SELECT
SUM(sale_price)
FROM bigquery-public-data.thelook_ecommerce.order_items 
WHERE status in not ("Cancelled", "Returned")

- Appris:

- Bloqué sur :

