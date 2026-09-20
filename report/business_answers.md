# Business Report: Hotel Bar Inventory System

### 1. What is the core business problem and why does it matter?
The main problem is that hotel bars are struggling with two opposite issues. On busy weekends, they run out of popular drinks (stockouts), which makes guests unhappy and loses the hotel money. On the other hand, they are ordering way too much of the slow-moving drinks. This means the hotel has too much money tied up in bottles just sitting in the back room taking up space. Finding the perfect balance—ordering just enough to not run out, but not too much—is why this matters.

### 2. What assumptions did you make? Why?
I made a few basic assumptions to keep the math simple and realistic:
* **2-day lead time:** I assumed it takes exactly 2 days for the alcohol supplier to deliver the bottles after the bar orders them. 
* **Lost sales:** If a guest asks for a drink and the bar is out, I assumed that sale is lost forever (the guest doesn't come back tomorrow for it).
* **Missing days mean zero sales:** The original data only showed when drinks were poured. I assumed that if a specific brand wasn't listed on a certain day, it meant exactly zero milliliters were consumed.

### 3. What model did you use and why did you choose it? Why not others?
I tested a few models (like just using last week's sales, or a simple 7-day average), but I chose the **Random Forest** model. 

I chose it because bar sales are very dependent on the day of the week (weekends are much busier than Tuesdays). Simple averages smooth everything out too much and miss those weekend spikes. Random Forest is smart enough to look at multiple things at once—like the day of the week, the recent average, and yesterday's sales—and combine them to make a really good guess. I didn't use super complex models like Neural Networks because they are too hard to explain to a bar manager.

### 4. How does your system perform? What would you improve?
The system performs really well! When I tested it on the data, the model's "Par Levels" (how much they should keep in stock) almost completely eliminated stockouts. For example, for a popular vodka, the old naive way had 20 stockout days, but my 95% par level dropped that down to just 1 stockout day, without holding crazy amounts of extra inventory.

**To improve it, I would:**
* Add a calendar for local holidays or big hotel events (like weddings), since those cause huge random spikes in drinking.
* Connect it to the weather (people might drink different things if it's raining vs. a hot summer day).

### 5. How would this solution work in a real hotel?
In a real hotel, this wouldn't be a notebook. It would be a computer script that runs every night at 3:00 AM after the bar closes. It would look at the cash register (POS) data, calculate the new Par Levels, and automatically email a simple "Order Sheet" to the bar manager when they wake up.

**What would break at scale?**
* **Supplier delays:** The system assumes the delivery truck always arrives in 2 days. If a snowstorm delays the truck to 4 days, the bar will run out of alcohol because the safety stock wasn't big enough.
* **Spillage and theft:** The model tracks what is *sold*, but bartenders spill drinks or over-pour. Over time, the computer's inventory won't match the physical bottles on the shelf. 

**What to track in production:**
We would need to track the "Forecast Error" (how far off our predictions are from reality) every week. If the error gets too big, it means customer tastes have changed and we need to retrain the model.
