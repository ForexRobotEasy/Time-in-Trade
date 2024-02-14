# Time in Trade

Time in Trade is a Forex trading software developed by Forex Robot Easy Team. For detailed reviews and trading results of this product, please visit [this link](https://forexroboteasy.com/forex-robot-review/time-in-trade-forex-software-unbiased-review-real-results/). Please note that ForexRobotEasy is not the official developer of this product. We are only providing a sample code that can work as described in this product. To find the official developer of this product, please refer to MQL5.

## Description

Time in Trade is an expert advisor (EA) that automates the process of opening pending orders at specific times. It allows traders to define the order type, lot size, maximum slippage, and whether to adjust for daylight saving time. The EA calculates the current time and checks if it's time to place a pending order. If it is, it calculates the expiration time for the pending order and places it. The EA also keeps track of the last time a pending order was placed and calculates the next time to place a pending order.

## Input Parameters

- **OrderType:** Specifies the order type. It can be either OP_BUY for a buy order or OP_SELL for a sell order.
- **LotSize:** Sets the lot size for pending orders.
- **Slippage:** Defines the maximum allowed slippage in pips.
- **AdjustForDST:** Determines whether to adjust for daylight saving time. If enabled, the EA will adjust the next time to place a pending order based on the DST status.
 
## Global Variables

- **lastTime:** Stores the last time a pending order was placed.
- **nextTime:** Stores the next time to place a pending order.

## Trading Functions

### OpenPendingOrders()

This function is responsible for opening pending orders. It calculates the current time and checks if it's time to place a pending order. If it is, it calculates the expiration time for the pending order and calls the `OrderSend()` function to place the pending order. If the pending order is successfully placed, it updates the `lastTime` variable with the current time. If there is an error while placing the pending order, it prints the error code using the `GetLastError()` function. Finally, it calculates the next time to place a pending order by adding the period of 5 minutes to the current time.

### OnInit()

This function is executed during the initialization of the EA. It adjusts the next time to place a pending order based on the DST status if the `AdjustForDST` input parameter is enabled. If DST is active, it adds the period of 5 minutes to the local time. If DST is not active, it subtracts 1 hour from the local time. If `AdjustForDST` is disabled, it simply adds the period of 5 minutes to the local time.

### OnTick()

This function is executed on every tick. It checks if it's time to open pending orders by comparing the current time with the next time to place a pending order. If it's time, it calls the `OpenPendingOrders()` function to open pending orders.

### OnDeinit()

This function is executed during the deinitialization of the EA. It prints the reason for deinitialization.

## Disclaimer

Please note that this ReadMe file is only for informational purposes and does not constitute financial advice. Trading in the Forex market involves substantial risk and may not be suitable for all investors. Always conduct thorough research and seek professional advice before making any investment decisions.
