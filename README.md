# Dynamic Investment Blueprint *by Filip Skotarski*

## Goal
*Call a stock market API to target companies of interest while instantly eradicating any companies that do not pass validation boundaries from our initial investment strategy. This project will serve as a benchmark for future phases which will implement Machine Learning principles for calculating future Margin of Safety and Stock Prices*

## Why? 
Finding new talent to invest in may be tough and time consuming. This program can validate the whole stock market in seconds with real-time stock data. Call it a scanner - much more than that we can retrieve relevant technical data that we can leverage with Machine Learning, and AI.

## This Project
The project that you will read about here is only an illustration of what we can accomplish with my program. This program may be re-used with any technical parameters of interest and will output an analysis that can be used for projections and straight forward visualization diagrams. In this example we will call the API and validate any companies that fit our 'growth' investing scope (boundaries). Growth investing methods look for smaller companies that have potential for high growth in the future. Although this method is prone to possible loss, if we win there is a much better payout. So lets hundred-fold our investment!

## User Experience
This program is currently on phase 0 and can only be altered by coding at the least a programming novice. In future versions, anybody will be able to use it as it will have a graphical user interface (GUI)

## Future
After this process is complete, we can escalate our data into technical data science principles such as Machine Learning for an even higher level of certainty. Stock market investing goes far beyond fundamental analysis which is done by analysts/investors that have a lot of experience within the industry. We want to combine fundamental analysis with reliable technical data that is 'number crunched' instantly by our algorithms.

## Macro Stages of Our Data

-	**Data:** first step, we need to import our metadata from some raw data source. At this point the most reliable place would be to find a stock market API which we can use.
-	**Tools:** second step, cleaning the imported data and migrating it into a readable sheet
-	**Operating Model:** third step, this is where the magic happens, we can use our validation statements to indicate which companies we want to look at on a technical level. This is the point where we can apply analysis and possibly data science principles on a micro level to make future predictions. 
-	**Governance:** final step, visual and written distribution of a company so that an associate can look at the company and evaluate it further. This could be a verification of the company on a macro level with someone who has experience. This is the point where a fundamental analysis can be made with validation metrics such as macro psychology. 

## Technical Analysis Principles
The first rule of investing is to not speculate. To reduce speculation, I have outlined some rules that my program will calculate:
-	Profits annually/quarterly are increasing
-	High cash reserve, low debt owed
-	P/E ratio
-	Price-to-Book ratio
-	Shares in circulation should be low 
-	Company should grow minimum of 25 percent per year

## Fundamental Analysis Principles
Once the technical principles are satisfied, we have the option of looking into the company's social environment. Some rules we can follow are:
-	Capable management
-	Recent social news
-	Understand the company and industry
-	Check if institutions have invested, this is a good source of demand since there will be less outstanding share which drives demand (price) up
-	Check stock cycle by paying attention to the overall stock market momentum

## PART 1: Data Migration

**Procedure**
- This process *lays the foundation* of the whole script. Any stock attributes we would like to work with will be migration to our main dataframe. (Stock attributes are defined in the *'Attribute Bank Directory'* below)

<p align="center">
  <a href="https://imggmi.com" target="_blank"><img src="https://cdn1.imggmi.com/uploads/2019/9/25/3bd3a49cef4555519f635f80328359fc-full.png" border="0"/></a>
</p>

- **Explanation**

1. An API is called to extract JSON data from a URL of a website (data containing stock market attributes)
2. This data is stored into a temporary list
3. By converting the list into a dataframe we will be able to work with any availably data

- The process above will be *iterated multiple times* through different website path's until we have all requested data
- Shown below is this standard process written in **Python**

```python
try:
    # For Python 3.0 and later
    from urllib.request import urlopen
except ImportError:
    # Fall back to Python 2's urllib2
    from urllib2 import urlopen

import json

def get_jsonparsed_data(url):
    """
    Receive the content of ``url``, parse it as JSON and return the object.

    Parameters
    ----------
    url : str

    Returns
    -------
    dict
    """
    
    response = urlopen(url)
    data = response.read().decode("utf-8")
    return json.loads(data)
```
```python
def json_to_empty_dataframe(dictionary):
    columns = ['Company']
    # Create a list of the dictionary keys
    for keys in dictionary:
        columns.append(keys)
    
    # Create a dataframe with the columns
    initial_dataframe = pd.DataFrame(columns=columns)
    
    return initial_dataframe
```

## PART 2: Indicator Analysis Calculator

## PART 3: Margin of Safety Calculator

## PART 4: Data Visualization

### Company Evaluation Principles
-	**Margin of Safety:** one of the most important measurements when investing. This is a measure of asking if the company is still a good investment if the price suddenly drops. When you buy the stock at its current price, will you lose a lot if the price drops suddenly. There are many strategies used to measure this attribute:
  -	Liquidation Value: 
-	**Key Company Measurements:** earnings and recent stock price strength
-	**Capital Appreciation:** profit you keep after you buy a stock and sell it
-	**Stock Splits:** when a company splits the price of each stock, doubling its share volume - a sign that good things are coming for the company
-	**Bonds:** when an investor buys a bond, they are lending money to the corporation and will be paid back with interest
-	**Value Investing:** look for companies that are undervalued in the market
-	**Growth Investment:** look for companies that have potential for high growth potential (x-fold growth)
-	**Fundamental Analysis:** companies health and potential to succeed
-	**Technical Analysis:** predict future stock price based on current and projected market conditions and trading volume
-	**Fiscal Year:** company defined years
-	**Fiscal Quarter:** company define quarter – does not necessarily need to be January-March but it is classified as any three-month period

## Glossary
-	**Current Ratio:** reveals how easily a company can deal with unexpected expenses
-	**Dividend Yield:** tells us that the stock price is rising and may be overvalued
-	**Earnings/Share:** if this increases over fiscal quarters we call it earning momentum
-	**Net Profit Margin:** company profit
-	**Price-to-Book Ratio:** liquidation value of a share. (< 1 indicates stock is undervalued, > 1 indicates stock is overvalued)
- **Book value:** owners' equity
-	**Price/Earnings Ratio:** indicates the dollar amount an investor can expect to invest in a company in order to receive one dollar of that company's earnings
-	**Trailing P/E:** uses earnings from the past 12 months
-	**Forward P/E:** uses projected earnings from an analyst
-	**Price/Sales Ratio:** measure of a companies size to revenue from sales (the lower the better)
-	**Price/Cash-Flow Ratio:** cash flow after everything is paid off
-	**Return on Equity:** profitability in relation to equity (assets - liabilities)
-	**Simple Moving Average:** where the price is heading next
-	**Relative Strength Index:** when a stock price is stretched too far in one direction
-	**Relative Price Strength:** stock price compared to prices of other stocks
-	**Market Capitalization:** company size
  
## Attribute Bank Directory
- When making an HTTP Request for stock market attributes it's important to have a directory reference so you can find what you're looking for. 
- **Program (In-Use)**: Income Statement, Stock Historical Price

Below is a file directory

| File Type                   | Time Stamp    | Attributes                      |
| --------------------------- |:-------------:| -------------------------------:|
|**Profile**                  | Hourly        |price                            |
|                             |               |beta                             |
|                             |               |volAvg                           |
|                             |               |mktCap                           |
|                             |               |lastDiv                          |
|                             |               |range                            |
|                             |               |changes                          |
|                             |               |changesPercentage                |
|                             |               |companyName                      |
|                             |               |exchange                         |
|                             |               |industry                         |
|                             |               |website                          |
|                             |               |description                      |
|                             |               |ceo                              |
|                             |               |sector                           |
|                             |               |                                 |
|**Income Statement**         |Annual/Quarter |date                             |                     
|                             |               |Revenue                          |                     
|                             |               |Revenue Growth                   |                        
|                             |               |Cost of Revenue                  |
|                             |               |Gross Profit                     |
|                             |               |R&D Expenses                     |
|                             |               |SG&A Expenses                    |
|                             |               |Operating Expenses               |
|                             |               |Operating Income                 |
|                             |               |Interest Expense                 |
|                             |               |Earnings before Tax              |
|                             |               |Income Tax Expense               |
|                             |               |Net Income – Non-Controlling int |
|                             |               |Net Income – Discontinued ops    |
|                             |               |Net Income                       |
|                             |               |Preferred Dividends              |
|                             |               |Net Income Com                   |
|                             |               |EPS                              |
|                             |               |EPS Diluted                      |
|                             |               |Weighted Average Shs Out         |
|                             |               |Weighted Average Shs Out (Dil)   |
|                             |               |Dividend per Share               |
|                             |               |Gross Margin                     |
|                             |               |EBITDA Margin                    |
|                             |               |EBIT Margin                      |
|                             |               |Profit Margin                    |
|                             |               |Free Cash Flow margin            |
|                             |               |EBITDA                           |
|                             |               |EBIT                             |
|                             |               |Consolidated Income              |
|                             |               |Earnings Before Tax Margin       |
|                             |               |Net Profit Margin                |
|                             |               |                                 |
|**Balance Sheet Statement**  |Annual/Quarter |date                             |
|                             |               |Cash and cash equivalents        |
|                             |               |Short-term investments           |
|                             |               |Cash and short-term investments  |
|                             |               |Receivables                      |
|                             |               |Inventories                      |
|                             |               |Total current assets             |
|                             |               |Property, Plant & Equipment Net  |
|                             |               |Goodwill and Intangible Assets   |
|                             |               |Long-term investments            |
|                             |               |Tax assets                       |
|                             |               |Total non-current assets         |
|                             |               |Total assets                     |
|                             |               |Payables                         |
|                             |               |Short-term debt                  |
|                             |               |Total current liabilities        |
|                             |               |Long-term debt                   |
|                             |               |Total debt                       |
|                             |               |Deferred revenue                 |
|                             |               |Tax liabilities                  |
|                             |               |Deposit Liabilities              |
|                             |               |Total non-current liabilities    |
|                             |               |Total liabilities                |
|                             |               |Other comprehensive income       |
|                             |               |Retained earnings (deficit)      |
|                             |               |Total shareholders equity        |
|                             |               |Investments                      |
|                             |               |Net Debt                         |
|                             |               |Other Assets                     |
|                             |               |Other Liabilities                |
|                             |               |                                 |
|**Cash Flow Statement**      |Annual/Quarter |date                             |
|                             |               |Depreciation & Amortization      |               
|                             |               |Stock-based compensation         |
|                             |               |Operating Cash Flow              |
|                             |               |Capital Expenditure              |
|                             |               |Acquisitions and disposals       |
|                             |               |Investment purchases and sales   |
|                             |               |Investing Cash flow              |
|                             |               |Issuance (repayment) of debt     |
|                             |               |Issuance (buybacks) of shares    |
|                             |               |Dividend payments                |
|                             |               |Financing Cash Flow              |
|                             |               |Effect of forex changes on cash  |
|                             |               |Net cash flow / Change in cash   |
|                             |               |Free cash flow                   |
|                             |               |Net Cash/Marketcap               |
|                             |               |                                 |
|**Company Financial Ratios** |Annual         |date                             |
|                             |               |investmentValuationRatios {      |
|                             |               |priceBookValueRatio              |
|                             |               |priceToBookRatio                 |
|                             |               |priceToSalesRatio                |
|                             |               |priceEarningsRatio               |
|                             |               |receivablesTurnover              |
|                             |               |priceToFreeCashFlowsRatio        |
|                             |               |priceCashFlowRatio               |
|                             |               |priceEarningsToGrowthRatio       |
|                             |               |priceSalesRatio                  |
|                             |               |dividendYield                    |
|                             |               |enterpriseValueMultiple          |
|                             |               |priceFairValue                   |
|                             |               |                                 |
|**Company Enterprise Value** |Annual/Quarter |date                             |
|                             |               |Stock Price                      |
|                             |               |Number of Shares                 |
|                             |               |Market Capitalization            |
|                             |               |- Cash & Cash Equivalents        |
|                             |               |+ Total Debt                     |
|                             |               |Enterprise Value                 |
|                             |               |                                 |
|**Company Key Metrics**      |Annual/Quarter |date                             |
|                             |               |Revenue per Share                |
|                             |               |Net Income per Share             |
|                             |               |Operating Cash Flow per Share    |
|                             |               |Free Cash Flow per Share         |
|                             |               |Cash per Share                   |
|                             |               |Book Value per Share             |
|                             |               |Tangible Book Value per Share    |
|                             |               |Shareholders Equity per Share    |
|                             |               |Interest Debt per Share          |
|                             |               |Market Cap                       |
|                             |               |Enterprise Value                 |
|                             |               |PE ratio                         |
|                             |               |Price to Sales Ratio             |
|                             |               |POCF ratio                       |
|                             |               |PFCF ratio                       |
|                             |               |PB ratio                         |
|                             |               |PTB ratio                        |
|                             |               |EV to Sales                      |
|                             |               |Enterprise Value over EBITDA     |
|                             |               |EV to Operating cash flow        |
|                             |               |EV to Free cash flow             |
|                             |               |Earnings Yield                   |
|                             |               |Free Cash Flow Yield             |
|                             |               |Debt to Equity                   |
|                             |               |Debt to Assets                   |
|                             |               |Net Debt to EBITDA               |
|                             |               |Current ratio                    |
|                             |               |Interest Coverage                |
|                             |               |Income Quality                   |
|                             |               |Dividend Yield                   |
|                             |               |Payout Ratio                     |
|                             |               |SG&A to Revenue                  |
|                             |               |R&D to Revenue                   |
|                             |               |Intangibles to Total Assets      |
|                             |               |Capex to Operating Cash Flow     |
|                             |               |Capex to Revenue                 |
|                             |               |Capex to Depreciation            |
|                             |               |Stock-based compensation to Revenue|
|                             |               |Graham Number                    |
|                             |               |Graham Net-Net                   |
|                             |               |Working Capital                  |
|                             |               |Tangible Asset Value             |
|                             |               |Net Current Asset Value          |
|                             |               |Invested Capital                 |
|                             |               |Average Receivables              |
|                             |               |Average Payables                 |
|                             |               |Average Inventory                |
|                             |               |Capex per Share                  |
|                             |               |                                 |
|**Company Financial Growth** |Annual/Quarter |date                             |
|                             |               |Gross Profit Growth              |                     
|                             |               |EBIT Growth                      |
|                             |               |Operating Income Growth          |
|                             |               |Net Income Growth                |
|                             |               |EPS Growth                       |
|                             |               |EPS Diluted Growth               |
|                             |               |Weighted Average Shares Growth   |
|                             |               |Weighted Average Shares Diluted Growth|
|                             |               |Dividends per Share Growth       |
|                             |               |Operating Cash Flow growth       |
|                             |               |Free Cash Flow growth            |
|                             |               |Receivables growth               |
|                             |               |Inventory Growth                 |
|                             |               |Asset Growth                     |
|                             |               |Book Value per Share Growth      |
|                             |               |Debt Growth                      |
|                             |               |R&D Expense Growth               |
|                             |               |SG&A Expenses Growth             |


