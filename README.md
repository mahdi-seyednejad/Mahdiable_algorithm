# Mahdiable😁_algorithm

# Cryptocurrency Arbitrage: Leveraging Order Book Analysis for Profit

## Introduction

This repository contains the implementation of the Mahdiable Algorithm, a sophisticated approach to identifying cryptocurrency arbitrage opportunities across different exchanges. 
By analyzing limit order books, this algorithm provides a more accurate assessment of potential profits and risks associated with arbitrage trades.
The time complexity of this algorith is O(nlogn) where n is the number of orders in the order book.

## What is Exchange Arbitrage?
Exchange Arbitrage means buying a cryptocurrency on one exchange and selling it on another exchange at a higher price to make a profit.

## What are the complexities of Exchange Arbitrage?
1. The price of a cryptocurrency can vary between exchanges due to supply and demand, trading volume, and other factors.
2. Withdrawal fees, slippage, and trading fees can reduce the profit margin. The withdrawal fees are the fees charged by the exchange to transfer the cryptocurrency to another exchange. They are calculated based on the amount of cryptocurrency being transferred.
3. The trading volume of a cryptocurrency can affect the liquidity of the market. A high trading volume means that there are more buyers and sellers in the market, making it easier to execute trades at the desired price.
4. We need to know for each potential arbitrage trade the volume of the cryptocurrency that we should buy, amount of money that will be spent, the amount of money that will be earned, and the fees that will be paid.
5. We need to rank the cryptocurrencies based on their arbitrage potential to identify the most profitable trades.
6. We need to look into the limit order books of the exchanges to match the hypothetical buy and sell orders based on bids and asks prices and volumes to calculate the potential profit.

## Features

- Detailed analysis of limit order books from multiple exchanges
- Consideration of withdrawal fees, transaction fee (commission rate), and trading volumes
- Help ranking of cryptocurrencies based on arbitrage potential
- Modular design for easy extension and customization

## Algorithm Overview

Before running the algorithm, you need to:
1. Collect order book data from two exchanges for a specific cryptocurrency
2. Clean the order books to remove potential outliers (if applicable)

The Mahdiable Algorithm works as follows:
1. Compare prices to determine the source and destination exchanges
2. Match sell orders from the source with buy orders from the destination
3. Calculate potential profit, considering withdrawal fees
4. Compute total trading volume, spent money, earned money, and fees paid
5. Assign a score to a given cryptocurrency and help rank them by profitability


The notebook [mahdiable_algorithm.ipynb](mahdiable_algorithm.ipynb) provides a step-by-step guide to implementing the Mahdiable Algorithm.
It also contains 2 test cases to demonstrate the algorithm's functionality.

## Algorithm Complexity
The overall time complexity of this algorithm is O(nlogn) where n is the number of orders we take into account in the order book. This is due to the sorting of the orders based on their prices.
For more details on the time and space complexity of the algorithm, please refer to the [mahdiable-algorithm-complexity](docs/mahdiable-algorithm-complexity.md) file.
In case you can try to optimize the algorithm to reduce the time complexity, please feel free to submit a pull request.
In the case of big data, the algorithm can be optimized by using parallel processing or distributed computing. 
The final calculate_symbol_profit_mahiable() function can be applied to a dataframe as a dataframe.apply() function to calculate the profit for all the symbols in the dataframe.
## Big Picture
The Mahdiable Algorithm is part of a larger system that can be used to identify and execute arbitrage opportunities in the cryptocurrency market.
It is in a function called calculate_symbol_profit_mahiable() that can be used to calculate the profit for a given symbol.

The general workflow of the system is as follows:
```python
    FOR EACH cryptocurrency C:
        FOR EACH pair of exchanges (source, destination):
            src_order_book(C) = get_order_book(C, source) # 
            clean_order_book(src_order_book(C))
            dst_order_book(C) = get_order_book(C, destination)
            clean_order_book(dst_order_book(C))
            potential = EvaluateArbitragePotential(src_order_book(C), dst_order_book(C), withdrawal_fee_C, fee_rates, other_parameters)
            Store potential in results
            
    Rank results based on profit or other metrics
    Select most promising arbitrage opportunities
```

You can customize the algorithm by modifying the following parameters:

- In the function `clean_order_book()`, you can implement your own logic for cleaning the order book.
- Scoring in EvaluateArbitragePotential(): In addition to the volume and profit of a given crypto, you can also use other parameters to cryptocurrencies such as:
    - Liquidity: The trading volume of a cryptocurrency can affect the liquidity of the market. A high trading volume means that there are more buyers and sellers in the market, making it easier to execute trades at the desired price.
    - Volatility: The price of a cryptocurrency can vary between exchanges due to supply and demand, trading volume, and other factors.
    - Risk: The risk associated with a cryptocurrency can be calculated based on its historical price data and other factors.
    - Market conditions: The overall market conditions can affect the profitability of an arbitrage trade. For example, if the market is highly volatile, it may be riskier to execute an arbitrage trade.

## Contributing

Contributions to improve the algorithm or extend its functionality are welcome. Please feel free to submit pull requests or open issues to discuss potential improvements.

## Disclaimer

This software is for educational purposes only. Cryptocurrency trading carries a high level of risk, and may not be suitable for all investors. Before deciding to trade cryptocurrency, you should carefully consider your investment objectives, level of experience, and risk appetite.

## License

This project is licensed under the MIT License - see the [LICENSE](docs/LICENSE.md) file for details.

## Contact

For any queries regarding this project, please open an issue on this GitHub repository.

---

Please remember to star this repository if you find it useful!
