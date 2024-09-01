# Time Complexity Analysis of the Mahdiable Algorithm

## Overview

The Mahdiable algorithm is designed to evaluate arbitrage opportunities in cryptocurrency markets by analyzing limit order books from two different exchanges. This document provides an analysis of the algorithm's time complexity.

## Algorithm Structure

The algorithm can be broken down into several key steps:

1. Processing order books into stacks
2. Main loop for matching orders
3. Updating withdrawal fees
4. Pushing remaining volumes back to stacks

## Time Complexity Analysis

### 1. Processing Order Books into Stacks

```python
src_sell_stack = StackLob().process_order_book_to_stack(src_sell_order_book_df, price_col, volume_col, is_sell_side=True)
dst_buy_stack = StackLob().process_order_book_to_stack(dst_buy_order_book_df, price_col, volume_col, is_sell_side=False)
```

- Let n be the number of orders in the larger order book.
- Assuming `process_order_book_to_stack` involves sorting the orders (which is typically the case for order book processing), this step has a time complexity of O(n log n) for each order book.

**Time Complexity for this step: O(n log n)**

### 2. Main Loop for Matching Orders

```python
while not src_sell_stack.is_empty() and not dst_buy_stack.is_empty():
    # ... (order matching logic)
```

- In the worst case, this loop will iterate through all orders in both stacks.
- Each iteration involves constant time operations (comparisons, arithmetic operations).
- The loop continues until one of the stacks is empty or no more profitable trades are possible.

**Time Complexity for this step: O(n)**

### 3. Updating Withdrawal Fees

```python
withdrawal_fee_money, rem_w_fee_amount = update_withdrawal_fee_money(src_order[price_col],
                                                                     current_trading_volume,
                                                                     withdrawal_fee_money,
                                                                     rem_w_fee_amount)
```

- This operation is performed in each iteration of the main loop.
- Assuming `update_withdrawal_fee_money` is a constant time operation.

**Time Complexity for this step: O(1) per iteration, O(n) total**

### 4. Pushing Remaining Volumes Back to Stacks

```python
if src_order[volume_col] > 0:
    src_sell_stack.push(src_order)
if dst_order[volume_col] > 0:
    dst_buy_stack.push(dst_order)
```

- These operations are performed in each iteration of the main loop.
- Pushing to a stack is typically an O(1) operation.

**Time Complexity for this step: O(1) per iteration, O(n) total**

## Overall Time Complexity

The overall time complexity of the Mahdiable algorithm is dominated by the initial processing of order books into stacks, which involves sorting.

**Overall Time Complexity: O(n log n)**

Where n is the number of orders in the larger order book.

## Space Complexity

The space complexity is primarily determined by the storage of orders in the stacks:

**Space Complexity: O(n)**

## Optimization Considerations

1. The efficiency of the `process_order_book_to_stack` function is crucial for overall performance. Optimizing this step could potentially improve the algorithm's speed.

2. The main loop's performance is generally efficient (linear time), but it could potentially be optimized further by using more sophisticated data structures for quick order matching.

3. If the order books are already sorted when received, the initial processing step could potentially be reduced to O(n), improving the overall time complexity to O(n).

## Conclusion

The Mahdiable algorithm demonstrates efficient time complexity for processing and matching orders from two different exchanges. Its O(n log n) time complexity makes it suitable for real-time arbitrage opportunity detection, even with large order books. However, as with any algorithm dealing with financial data, the actual performance may also depend on factors such as data retrieval speed and the frequency of updates to the order books.
