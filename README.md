
<p align="center">
  <h1 align="center">Max Profit Problem</h1>
</p>

## Problem Statement

Given a array of numbers representing the stock prices of a company in chronological order, write a function that calculates the maximum profit you could have made from buying and selling that stock once. You must buy before you can sell it.

For example, given [9, 11, 8, 5, 7, 10], you should return 5, since you could buy the stock at 5 dollars and sell it at 10 dollars.

## Explanation of Problem

### Understanding the Problem
We need to find two days, **i** and **j**, such that:

1. **i** comes before **j** (You must buy before selling).
2. The difference between the stock prices on day **j** and day **i** is the maximum among all possible pairs of days.

### Intuitive Approach
An intuitive way to approach this problem is to use a nested loop where, for every day i, you check the difference in price with every subsequent day j. This approach will give the correct answer, but it is inefficient with a time complexity of O(n^2) for an array of length n.

### Efficient Approach
To solve the problem efficiently, we can do it in O(n) time. Here's how:

1. **Track Minimum Price:** As we iterate through the list, we'll keep track of the minimum stock price we've seen so far. This represents our best day to buy the stock.
2. **Calculate Potential Profit Daily:** For each day, we'll calculate the potential profit by subtracting the current day's price with the minimum stock price we've seen. This gives us the profit we'd get if we sold on the current day.
3. **Update Maximum Profit:** We'll keep track of the maximum profit we can get. If the potential profit of the current day is greater than the maximum profit we've seen so far, we'll update it.

The following is the pseudocode for the efficient approach. 

```pseudocode

function maxProfit(prices: array of numbers) -> number:
    if length of prices is less than 2:
        return 0

    minPrice = prices[0]
    maxProfit = 0

    for each price in prices:
        if price < minPrice:
            minPrice = price
        else:
            potentialProfit = price - minPrice
            maxProfit = maximum of maxProfit and potentialProfit

    return maxProfit
```

Using the above algorithm with the example [9, 11, 8, 5, 7, 10], the function will indeed return a max profit of 5 (buy at 5 and sell at 10).

Here is a flowchart for the pseudocode.

<p align="center">
  <img alt="Pseudocode Flowchart" src="assets/diagrams/PseudoCodeFlowChart.png" width="500px" />
</p>

How It Works
1. Start by initializing minPrice to the first price in the array. This will keep track of the lowest price we've seen so far.
2. Initialize maxProfit to 0. This will keep track of the highest profit we've found.
3. Iterate through the list of prices.
    3.1 If the current price is less than our stored minPrice, update minPrice.
    3.2 Otherwise, calculate the potential profit by subtracting the minPrice from the current price. If this potential profit is greater than the current maxProfit, update maxProfit.
6. Return maxProfit at the end of the function.

Using the provided example, [9, 11, 8, 5, 7, 10]:

- On day 1: Price is 9 (set as initial minPrice)
- On day 2: Profit is 11-9=2
- On day 3: Price is 8 (minPrice changes from 9 to 8)
- On day 4: Price is 5 (minPrice changes from 8 to 5)
- On day 5: Profit is 7-5=2
- On day 6: Profit is 10-5=5 (highest profit found)
- Result: 5 (Buy at 5 and sell at 10)

