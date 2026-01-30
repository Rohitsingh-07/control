## Lean Inventory

- Lean Inventory. If you have well planned production, why should you hold lots and lots inventory? You don't need to, if you switch to your just in time inventory system. So here we are in a place selling granite. And if you think about this product. It's large, it's heavy, and it's expensive. You want to have some in stock to show your customers, but you don't want to have too much.
- Therefore you have to be very careful with your inventory. In the automotive industries, there are companies that get a resupply every single day. And there are others that take it even a step further, and they get inventory for just the next two hours. So they will get a delivery every two hours, of their production day. And that maintains your inventory at the lowest possible level. Now, you will not get economies of skill and warehousing that way, but you don't need to. Because you almost don't need warehouses, as your transportation system acts like a warehouse.
- Holding costs are often wrongly accounted for. In other words, most companies underestimate the amount of money it takes to hold inventory. And this really causes them to hold too much inventory. Because they don't think it costs them a lot. Now if we calculate holding cost the correct way, which is we take into account the cost of money and the opportunity cost of what we could do if we didn't have that money tied up in inventory. If we take into account the service costs which are taxes and insurance on inventory. The storage space costs.
- All the warehouses, equipment, and labor to maintain that level of inventory and the risk costs. Things may go out of style, they break, or they expire. Then a more true accounting of how expensive it is to hold inventory emerges. Now as we see in the economic or the quantity model that we just discussed, if your holding costs are higher, your optimal inventory levels are going to go down. Because you will hold less inventory and order more often. We can lower the level of inventory also by looking at our order cost. Order cost is made of two parts, order submission and order receipt.
- On the order submission part, we can look at automation and using technology to generate automatic orders that don't require human intervention, which is expensive. On the receiving side, we can used automation, better technology, and better management methods, to make unloading trucks and putting away the inventory more efficient. Therefore, overall reducing the order cost. Again, back to the EOQ model, if we have lower cost of placing orders, we will place them more often, therefore reducing the average level of inventory. Safety stocks add to inventory tremendously because we have to hold on to it all the time. Now, there are several ways we can remove the need for safety stock, and that's addressing uncertainty. So the one on the demand side, if we're able to take out the fluctuation in demand.
- I.e, we limit our system to more stable sales over time, that should remove the need for safety stock. Another one is the variation amongst lead times. And receiving an order faster or quicker will add uncertainty, by fixing that we can remove the need for safety stock. Finally, it's the length of the lead time. If we can shorten the length of the lead time, then we're able to be much quicker in resupplying ourselves, and the risk of stocking out becomes smaller. And that's why in the lot of lean production facilities, having your suppliers close by is very critical. If we shorten that lead time, we're able to get by with less safety stock, reducing our overall need for inventory.
- Let's talk about the Kanban inventory system. I'm in the back of a grocery store. You see the dock doors here. This was the inspiration for the Kanban systems. As a Toyota engineers went to visit the River Rouge Plant in Michigan. They stopped at a couple of grocery stores in California. And what they saw, really sparked their interest.
- Every day, there's a new truck bringing in supplies and produce to the grocery store. And every day, customers are buying items. The following day, only the items that were used are getting delivered. So there's constant turnover, but inventory is not piling up. Now the way that works is, we have three different bins of inventory, all equally sized. The first bin sits on the production floor, and it is ready to be used for making our product. The second bin sits in the warehouse next to the production facility, and it's ready to go.
- The third bin sits at the supplier location, ready to be shipped to us. So as we start building our products, we take raw materials out of bin one. As soon as bin one is empty, we place an order to our supplier and start working on bin two, which has been moved from the warehouse to our production floor. Bin three is supposed to arrive before we empty bin two. So, therefore we have continuous supply, and just enough inventory to get us by. Now, the size of the bin typically is calculated as the lead time demand. So the demand we experience over the lead time.
- It takes one day for the supplier to ship their bin to us, then one day's worth of inventory should be in each bin. The Kanban system is a very simple inventory system. You only replenish what you use. And you don't anticipate what you're going to use, because you have just enough to get you by for at least a day. And you get deliveries every single day of the week. Therefore you're not going to run out of inventory, but it's also not going to pile up.

###########################################################################################################
###########################################################################################################
###########################################################################################################

## Economic Order Quantity Terms and Notation

The Economic Order Quantity Calculation
Please remember the following notation of the formulas:

TC = Total Cost of Ordering and Holding Inventory

Q = Order Quantity (how much we order each time)

D = Demand (how much we sell in a given period – usually one year)

V = Value of the item (purchase cost or production cost)

O = Order Cost (on-time cost of placing and receiving an order)

C = Inventory Carrying Cost (expressed as a percentage of the value of the item)

###########################################################################################################
###########################################################################################################
###########################################################################################################

## The EOQ Calculation

The Economic Order Quantity Calculation
Please remember the following notation of the formulas:

Q = Order Quantity (how much we order each time)

D = Demand (how much we sell in a given period – usually one year)

V = Value of the item (purchase cost or production cost)

O = Order Cost (placing and receiving it)

C = Inventory Carrying Cost

<img width="1038" height="370" alt="image" src="https://github.com/user-attachments/assets/44af9903-7dfe-4842-a1f6-8ba5f7995fd8" />

<img width="895" height="465" alt="image" src="https://github.com/user-attachments/assets/2d3afd7f-ee46-47b2-94b4-d91c610e5af9" />

<img width="989" height="460" alt="image" src="https://github.com/user-attachments/assets/f8d5eaae-dc6e-42f5-8577-ebc77295e7c8" />

###########################################################################################################
###########################################################################################################
###########################################################################################################

## Safety Stock Terms and Calculation

The Safety Stock Calculation
If you are not familiar with the safety stock concept, I would recommend you review the lecture entitled "
How much inventory do we need
" in the 
Supply Chain Logistics
 course.

Please remember the following notation:

SS = safety stock

k = service factor (the number of standard deviations to cover for a given service level)

Sc = combined standard deviation of lead time and demand

t = average replenishment lead time

Sd = standard deviation of daily sales

d = average daily sales

St = standard deviation of replenishment cycle

- Step 1: Calculate the Combined Standard Deviation of Lead Time and Demand

<img width="1028" height="223" alt="image" src="https://github.com/user-attachments/assets/cdd5e323-e5e5-4563-9ef4-29e5d47849bb" />

- Step 2: Pick your desired Service Level

- This step depends on how much inventory you can carry to prevent a stockout. The higher the service level the more inventory you need to carry. Most companies pick a service level between 90% and 99%.

<img width="931" height="573" alt="image" src="https://github.com/user-attachments/assets/70b28e5c-198f-45a4-9176-f171b1b9e917" />

- Step 3: Calculate the Safety Stock

<img width="1022" height="247" alt="image" src="https://github.com/user-attachments/assets/55f7ff8b-02ea-41c7-a4b5-a182aecfcf48" />

<img width="955" height="519" alt="image" src="https://github.com/user-attachments/assets/93dc579d-19d6-4611-8b21-23d308287c64" />

###########################################################################################################
###########################################################################################################
###########################################################################################################

## Kanban

- Kanban, what I'll show you now is how to calculate the size of a bin in a Kanban system. Just as a quick refresher a Kanban is a three-bin system and we have three equal sized bins in which we hold inventory, for a certain, let's say manufacturing process. The idea behind the Kanban system is that Bin 1 sits right there where we use it. Bin 2 sits in the shop back room or in an attached warehouse, and Bin 3 sits with the supplier. Now the idea about Bin 3 is that it is ready to be shipped. We cannot add any wait time or any manufacturing time. You can't just say, once I get the order I will start building products for Bin 3.

<img width="1919" height="909" alt="image" src="https://github.com/user-attachments/assets/a7a655d7-c4c2-4393-8978-723cc16b5675" />

- That is not possible. It has to be finished goods ready to be shipped. Now back to be in Bin 1. As we take items out of Bin 1 and it becomes empty, we are going to move Bin 2 onto the shop floor and place an order to the supplier to move Bin 3 into our facility. Now in an ideal system, Bin 1 is almost empty as we move Bin 2 onto the shop floor. Bin 3 Is on the shop floor, ready to be shipped. Now the big question is, how large should the bins be?
- First of all, they should all be the equal size, and that corresponds to the lead time demand. After all those complex formulas that I taught you in the previous screen captures, this one will be very simple. Here we have an example of demand and the lead time for each order that has been shipped. Now, this is based on historical information and it is not set up to be a Kanban system yet. However, the calculation for Kanban is fairly simple. All we need to do is, we need to calculate average demand, average lead time, and then from that it's fairly simple to do the lead time demand calculation. So to get the average demand, we use the Average function.
- There's that to get the Average Lead Time, the average or historical lead times. And then the lead time demand equals the average demand times the average lead time. So in other words, we should have a Kanban size of 112 units because on average, that's our lead time demand, and we should be able to have a functioning Kanban system with this set up. And ship out every five days, five and a half days if we need to. So there you see how simple it is to set up a Kanban system. There are more complex methods and sometimes you do need to take safety stock into account, but at its very core this is how simple it can be.

###########################################################################################################
###########################################################################################################
###########################################################################################################

