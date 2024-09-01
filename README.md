# Mahdiable_algorithm

# Cryptocurrency Arbitrage: Leveraging Order Book Analysis for Profit

## Introduction

This repository contains the implementation of the Mahdiable Algorithm, a sophisticated approach to identifying cryptocurrency arbitrage opportunities across different exchanges. 
By analyzing limit order books, this algorithm provides a more accurate assessment of potential profits and risks associated with arbitrage trades.
The time complexity of this algorith is O(nlogn) where n is the number of orders in the order book.

## Features

- Detailed analysis of limit order books from multiple exchanges
- Consideration of withdrawal fees and trading volumes
- Ranking of cryptocurrencies based on arbitrage potential
- Modular design for easy extension and customization

## Algorithm Overview

The Mahdiable Algorithm works as follows:

1. Collect order book data from two exchanges for a specific cryptocurrency
2. Clean the order books to remove potential outliers
3. Compare prices to determine the source and destination exchanges
4. Match sell orders from the source with buy orders from the destination
5. Calculate potential profit, considering withdrawal fees
6. Compute total trading volume, spent money, earned money, and fees paid
7. Assign a score to each cryptocurrency and rank them by profitability


Make sure to update the `exchanges` and `withdrawal_fees` dictionaries in the `mahdiable_algorithm.py` file with real data from the exchanges you're interested in.

## Algorithm Complexity
The overal time complexity of this algorithm is O(nlogn) where n is the number of orders in the order book. This is due to the sorting of the orders based on their prices.
For more details on the time complexity of the algorithm, please refer to the [mahdiable-algorithm-complexity](docs/tmahdiable-algorithm-complexity.md) file.
In case you can try to optimize the algorithm to reduce the time complexity, please feel free to submit a pull request.
In the case of big data, the algorithm can be optimized by using parallel processing or distributed computing. 
The final calculate_symbol_profit_mahiable() function can be applied to a dataframe as an dataframe.apply() function to calculate the profit for all the symbols in the dataframe.
## Configuration

You can customize the algorithm by modifying the following parameters:

- `clean_order_book()`: Implement your own logic for cleaning the order book
- Scoring formula in `evaluate_symbols()`: Adjust how the arbitrage opportunities are scored
- Add additional exchanges in the `exchanges` dictionary

## Contributing

Contributions to improve the algorithm or extend its functionality are welcome. Please feel free to submit pull requests or open issues to discuss potential improvements.

## Disclaimer

This software is for educational purposes only. Cryptocurrency trading carries a high level of risk, and may not be suitable for all investors. Before deciding to trade cryptocurrency, you should carefully consider your investment objectives, level of experience, and risk appetite.

## License

This project is licensed under the MIT License - see the [LICENSE](docs/LICENSE.md) file for details.

## Contact

For any queries regarding this project, please open an issue on this GitHub repository.

---

Remember to star this repository if you find it useful!