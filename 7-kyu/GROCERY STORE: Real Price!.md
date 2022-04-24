## GROCERY STORE: Real Price!


You are the owner of the Grocery Store. All your products are in the database, that you have created after CodeWars SQL exercises! :)

Customer often need to now how much really they pay for the products. Manufacturers make different sizes of same product so it is hard to compare prices, sometimes they make packages look big, but the weight of the product is small.

Make a SELECT query which will tell the price per kg of the product.

Weight is in grams! Round the price_per_kg to 2 decimal places.

Order results by price_per_kg ascending, then by name ascending.

*Products table schema:*
* id (int)
* name (string)
* price (float)
* stock (int)
* weight (float)
* producer (string)
* country (string)

*Results table schema:*
* name (string)
* weight (float)
* price (float)
* price_per_kg (float)


### **My solutions:**
*Notes: I'm not sure i really understand the only one possible of solution of this kata (nessesery to use casting, format). 
Why it doesn't work (`round()` funcion):
`ROUND((price / (weight / 1000)), 2) as price_per_kg  -- dlaczego nie działa?`

Maby I have to stronger understand and learn specificity of numeric datatypes used with arithmetic/math Operations or specific of postgreSql syntaxs. 

Another problem can be with specificity of CodeWars working: solutions is checked by prewroted test. 
There is possibility that this Kata sets too much accent on adapting output to the test result template (math operating and 'take care on decimal places'). whether there will be problem, in real life with division result being numeric or floating-point?
Maby siply using of round() funcion will be enough?

I got to the desirable solution at least with searching a lot in net, but i'm not sure it was wort of spended time. 
(* what i understand: math operation in query, usage of "as", order by, round()
* what i don't quite: nessesery to use cast() for math operations with float data type for each).

Maby is more advanced than 7-kyu


**solutions which worked (CodeWars):**

```sql
SELECT name, weight, price,
cast(round(CAST(price / weight * 1000 as numeric), 2) as float) as price_per_kg -- 'as real' instead of 'as float' works too
 
-- round(((price / weight * 1000) :: numeric), 2) :: float as price_per_kg


--ROUND((price / (weight / 1000)), 2) as price_per_kg // dlaczego nie działa?

FROM products
ORDER BY price_per_kg, name;
```

```sql
SELECT name, weight, price,
round(((price / weight * 1000) :: numeric), 2) :: real as price_per_kg -- 'as float' instead of 'as real' works too


--ROUND((price / (weight / 1000)), 2) as price_per_kg // dlaczego nie działa? / why doesn't work?

FROM products
ORDER BY price_per_kg, name
```
