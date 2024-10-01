```python
import pandas as pd
import yfinance as yf
```


```python
link = "https://en.wikipedia.org/wiki/List_of_S%26P_500_companies"

sp500_df = pd.DataFrame()
sp500_df['Ticker'] = pd.read_html(link)[0]['Symbol']
```


```python
sp500_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Ticker</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>MMM</td>
    </tr>
    <tr>
      <th>1</th>
      <td>AOS</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ABT</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ABBV</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ACN</td>
    </tr>
  </tbody>
</table>
</div>




```python
tickers_list = sp500_df['Ticker'].tolist()

try:
    data_download = yf.download(tickers_list, period ='1y')['Adj Close']
except Exception as e:
    print(f"Error downloading data: {e}")
    data_download = pd.DataFrame()

```

    [**********************99%%**********************]  499 of 503 completed

    $BF.B: possibly delisted; No price data found  (period=1y)
    

    [*********************100%%**********************]  503 of 503 completed
    
    5 Failed downloads:
    ['SW']: YFInvalidPeriodError("%ticker%: Period '1y' is invalid, must be one of ['1d', '5d', '1mo', '3mo', 'ytd', 'max']")
    ['BRK.B']: YFChartError('%ticker%: No data found, symbol may be delisted')
    ['SOLV', 'GEV']: YFInvalidPeriodError("%ticker%: Period '1y' is invalid, must be one of ['1d', '5d', '1mo', '3mo', '6mo', 'ytd', 'max']")
    ['BF.B']: YFPricesMissingError('$%ticker%: possibly delisted; No price data found  (period=1y)')
    


```python
data_download
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>Ticker</th>
      <th>A</th>
      <th>AAL</th>
      <th>AAPL</th>
      <th>ABBV</th>
      <th>ABNB</th>
      <th>ABT</th>
      <th>ACGL</th>
      <th>ACN</th>
      <th>ADBE</th>
      <th>ADI</th>
      <th>...</th>
      <th>WTW</th>
      <th>WY</th>
      <th>WYNN</th>
      <th>XEL</th>
      <th>XOM</th>
      <th>XYL</th>
      <th>YUM</th>
      <th>ZBH</th>
      <th>ZBRA</th>
      <th>ZTS</th>
    </tr>
    <tr>
      <th>Date</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2023-08-24</th>
      <td>118.634956</td>
      <td>14.57</td>
      <td>175.482056</td>
      <td>141.175507</td>
      <td>124.720001</td>
      <td>101.636833</td>
      <td>75.410004</td>
      <td>309.146240</td>
      <td>512.429993</td>
      <td>170.572128</td>
      <td>...</td>
      <td>202.288269</td>
      <td>31.846945</td>
      <td>94.432472</td>
      <td>54.872860</td>
      <td>102.747429</td>
      <td>98.458961</td>
      <td>127.065483</td>
      <td>113.379524</td>
      <td>265.920013</td>
      <td>179.775040</td>
    </tr>
    <tr>
      <th>2023-08-25</th>
      <td>118.823601</td>
      <td>14.58</td>
      <td>177.700684</td>
      <td>141.233246</td>
      <td>125.790001</td>
      <td>102.087463</td>
      <td>74.620003</td>
      <td>313.692780</td>
      <td>525.059998</td>
      <td>174.961899</td>
      <td>...</td>
      <td>202.731995</td>
      <td>31.710894</td>
      <td>94.422592</td>
      <td>55.421494</td>
      <td>104.583069</td>
      <td>99.960785</td>
      <td>127.261673</td>
      <td>114.291954</td>
      <td>268.390015</td>
      <td>181.022644</td>
    </tr>
    <tr>
      <th>2023-08-28</th>
      <td>119.061882</td>
      <td>14.73</td>
      <td>179.272644</td>
      <td>141.945724</td>
      <td>126.154999</td>
      <td>100.696388</td>
      <td>74.190002</td>
      <td>315.808624</td>
      <td>529.919983</td>
      <td>177.092941</td>
      <td>...</td>
      <td>203.619446</td>
      <td>31.944128</td>
      <td>95.718071</td>
      <td>55.681370</td>
      <td>105.462234</td>
      <td>100.603020</td>
      <td>127.434120</td>
      <td>116.563110</td>
      <td>269.920013</td>
      <td>185.141739</td>
    </tr>
    <tr>
      <th>2023-08-29</th>
      <td>121.146851</td>
      <td>14.90</td>
      <td>183.182617</td>
      <td>142.099777</td>
      <td>132.250000</td>
      <td>101.754395</td>
      <td>75.750000</td>
      <td>318.308228</td>
      <td>540.570007</td>
      <td>179.282913</td>
      <td>...</td>
      <td>204.733688</td>
      <td>32.080185</td>
      <td>96.983894</td>
      <td>55.777622</td>
      <td>106.090210</td>
      <td>101.067398</td>
      <td>127.030067</td>
      <td>118.249130</td>
      <td>273.489990</td>
      <td>190.874817</td>
    </tr>
    <tr>
      <th>2023-08-30</th>
      <td>121.802139</td>
      <td>14.77</td>
      <td>186.694672</td>
      <td>142.802628</td>
      <td>130.610001</td>
      <td>102.283394</td>
      <td>77.089996</td>
      <td>318.111420</td>
      <td>545.359985</td>
      <td>178.310699</td>
      <td>...</td>
      <td>205.640854</td>
      <td>32.167648</td>
      <td>98.289276</td>
      <td>55.517742</td>
      <td>107.123970</td>
      <td>102.584007</td>
      <td>128.212662</td>
      <td>119.250816</td>
      <td>279.109985</td>
      <td>190.805496</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>2024-08-19</th>
      <td>140.509995</td>
      <td>10.31</td>
      <td>225.889999</td>
      <td>196.869995</td>
      <td>119.139999</td>
      <td>111.900002</td>
      <td>103.000000</td>
      <td>329.440002</td>
      <td>563.119995</td>
      <td>225.949997</td>
      <td>...</td>
      <td>282.399994</td>
      <td>30.180000</td>
      <td>76.599998</td>
      <td>60.150002</td>
      <td>118.529999</td>
      <td>134.380005</td>
      <td>136.690002</td>
      <td>111.769997</td>
      <td>347.019989</td>
      <td>184.479996</td>
    </tr>
    <tr>
      <th>2024-08-20</th>
      <td>139.750000</td>
      <td>10.29</td>
      <td>226.509995</td>
      <td>196.149994</td>
      <td>117.379997</td>
      <td>110.769997</td>
      <td>102.800003</td>
      <td>330.369995</td>
      <td>562.250000</td>
      <td>223.490005</td>
      <td>...</td>
      <td>281.470001</td>
      <td>30.110001</td>
      <td>76.019997</td>
      <td>59.990002</td>
      <td>114.580002</td>
      <td>134.149994</td>
      <td>136.949997</td>
      <td>111.639999</td>
      <td>344.850006</td>
      <td>183.600006</td>
    </tr>
    <tr>
      <th>2024-08-21</th>
      <td>139.990005</td>
      <td>10.40</td>
      <td>226.399994</td>
      <td>196.529999</td>
      <td>117.680000</td>
      <td>111.389999</td>
      <td>104.599998</td>
      <td>333.600006</td>
      <td>565.789978</td>
      <td>227.500000</td>
      <td>...</td>
      <td>283.679993</td>
      <td>30.410000</td>
      <td>77.360001</td>
      <td>59.959999</td>
      <td>113.849998</td>
      <td>135.800003</td>
      <td>137.750000</td>
      <td>112.129997</td>
      <td>345.000000</td>
      <td>182.899994</td>
    </tr>
    <tr>
      <th>2024-08-22</th>
      <td>140.220001</td>
      <td>10.14</td>
      <td>224.529999</td>
      <td>196.369995</td>
      <td>115.449997</td>
      <td>112.099998</td>
      <td>106.510002</td>
      <td>330.570007</td>
      <td>557.440002</td>
      <td>221.910004</td>
      <td>...</td>
      <td>285.140015</td>
      <td>30.260000</td>
      <td>77.089996</td>
      <td>59.919998</td>
      <td>114.730003</td>
      <td>135.419998</td>
      <td>136.759995</td>
      <td>113.419998</td>
      <td>342.160004</td>
      <td>182.169998</td>
    </tr>
    <tr>
      <th>2024-08-23</th>
      <td>140.869995</td>
      <td>10.39</td>
      <td>226.839996</td>
      <td>197.550003</td>
      <td>116.849998</td>
      <td>112.690002</td>
      <td>109.019997</td>
      <td>333.269989</td>
      <td>558.299988</td>
      <td>228.389999</td>
      <td>...</td>
      <td>281.459991</td>
      <td>31.360001</td>
      <td>77.370003</td>
      <td>60.119999</td>
      <td>116.320000</td>
      <td>136.919998</td>
      <td>135.520004</td>
      <td>115.050003</td>
      <td>351.619995</td>
      <td>180.899994</td>
    </tr>
  </tbody>
</table>
<p>252 rows × 503 columns</p>
</div>




```python
sp500_df['Stock Price'] = None
sp500_df['One Year Return'] = None
sp500_df

for t in tickers_list:
    try:
        # To avoid errors
        if t in data_download.columns:
            # Assigning close prices in Stock Price column to the corresponding ticker   
            # in the Ticker column. 
            sp500_df.loc[sp500_df['Ticker'] == t,'Stock Price'] = data_download[t].iloc[-1]
    
            # Calculate one-year return and doing the same
            one_year_return = ((data_download[t].iloc[-1]/data_download[t].iloc[0]) - 1) * 100
            sp500_df.loc[sp500_df['Ticker'] == t, 'One Year Return'] = one_year_return
        else:
            # Assign None to any ticker in ticker's list that isn't in the downloaded 
            # close price dataframe. 
            sp500_df.loc[sp500_df['Ticker'] == t, 'Stock Price'] = None
            sp500_df.loc[sp500_df['Ticker'] == t, 'One Year Return'] = None
    except Exception as e:
        print(f"Error downloading data for ticker {t}: {e}")
```


```python
sp500_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Ticker</th>
      <th>Stock Price</th>
      <th>One Year Return</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>MMM</td>
      <td>130.550003</td>
      <td>64.821166</td>
    </tr>
    <tr>
      <th>1</th>
      <td>AOS</td>
      <td>82.540001</td>
      <td>21.937874</td>
    </tr>
    <tr>
      <th>2</th>
      <td>ABT</td>
      <td>112.690002</td>
      <td>10.875161</td>
    </tr>
    <tr>
      <th>3</th>
      <td>ABBV</td>
      <td>197.550003</td>
      <td>39.932208</td>
    </tr>
    <tr>
      <th>4</th>
      <td>ACN</td>
      <td>333.269989</td>
      <td>7.803345</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Selecting the top 50 best performing stocks
sp500_df.sort_values('One Year Return', ascending=False, inplace=True)
# Slicing syntax df[start:end]
sp500_df = sp500_df[:50].copy()

# Drop the 'index' column and reset index
sp500_df.reset_index(inplace=True, drop=True)
```


```python
sp500_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Ticker</th>
      <th>Stock Price</th>
      <th>One Year Return</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>VST</td>
      <td>85.769997</td>
      <td>190.958329</td>
    </tr>
    <tr>
      <th>1</th>
      <td>NVDA</td>
      <td>129.369995</td>
      <td>174.386125</td>
    </tr>
    <tr>
      <th>2</th>
      <td>SMCI</td>
      <td>613.23999</td>
      <td>133.615234</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NRG</td>
      <td>83.5</td>
      <td>131.977629</td>
    </tr>
    <tr>
      <th>4</th>
      <td>GDDY</td>
      <td>162.449997</td>
      <td>131.509194</td>
    </tr>
    <tr>
      <th>5</th>
      <td>KKR</td>
      <td>122.230003</td>
      <td>106.793081</td>
    </tr>
    <tr>
      <th>6</th>
      <td>FICO</td>
      <td>1745.380005</td>
      <td>106.088021</td>
    </tr>
    <tr>
      <th>7</th>
      <td>HWM</td>
      <td>97.080002</td>
      <td>102.425855</td>
    </tr>
    <tr>
      <th>8</th>
      <td>ANET</td>
      <td>355.130005</td>
      <td>98.186283</td>
    </tr>
    <tr>
      <th>9</th>
      <td>AVGO</td>
      <td>166.360001</td>
      <td>98.1212</td>
    </tr>
    <tr>
      <th>10</th>
      <td>GE</td>
      <td>171.220001</td>
      <td>94.141132</td>
    </tr>
    <tr>
      <th>11</th>
      <td>IRM</td>
      <td>113.349998</td>
      <td>94.007159</td>
    </tr>
    <tr>
      <th>12</th>
      <td>MPWR</td>
      <td>936.289978</td>
      <td>93.257056</td>
    </tr>
    <tr>
      <th>13</th>
      <td>AXON</td>
      <td>370.700012</td>
      <td>89.123015</td>
    </tr>
    <tr>
      <th>14</th>
      <td>DECK</td>
      <td>974.559998</td>
      <td>86.776025</td>
    </tr>
    <tr>
      <th>15</th>
      <td>CRWD</td>
      <td>271.540009</td>
      <td>86.689594</td>
    </tr>
    <tr>
      <th>16</th>
      <td>META</td>
      <td>528.0</td>
      <td>84.510899</td>
    </tr>
    <tr>
      <th>17</th>
      <td>PGR</td>
      <td>241.25</td>
      <td>84.130236</td>
    </tr>
    <tr>
      <th>18</th>
      <td>CEG</td>
      <td>194.990005</td>
      <td>83.773422</td>
    </tr>
    <tr>
      <th>19</th>
      <td>UHS</td>
      <td>233.139999</td>
      <td>80.102106</td>
    </tr>
    <tr>
      <th>20</th>
      <td>NTAP</td>
      <td>133.119995</td>
      <td>80.019912</td>
    </tr>
    <tr>
      <th>21</th>
      <td>GRMN</td>
      <td>179.759995</td>
      <td>79.644866</td>
    </tr>
    <tr>
      <th>22</th>
      <td>TT</td>
      <td>352.910004</td>
      <td>79.280455</td>
    </tr>
    <tr>
      <th>23</th>
      <td>ALL</td>
      <td>180.509995</td>
      <td>75.927363</td>
    </tr>
    <tr>
      <th>24</th>
      <td>TRGP</td>
      <td>144.130005</td>
      <td>75.525569</td>
    </tr>
    <tr>
      <th>25</th>
      <td>LLY</td>
      <td>952.73999</td>
      <td>75.025842</td>
    </tr>
    <tr>
      <th>26</th>
      <td>PHM</td>
      <td>135.130005</td>
      <td>73.722489</td>
    </tr>
    <tr>
      <th>27</th>
      <td>KLAC</td>
      <td>817.840027</td>
      <td>73.193321</td>
    </tr>
    <tr>
      <th>28</th>
      <td>FITB</td>
      <td>42.119999</td>
      <td>71.092699</td>
    </tr>
    <tr>
      <th>29</th>
      <td>ISRG</td>
      <td>486.549988</td>
      <td>70.336775</td>
    </tr>
    <tr>
      <th>30</th>
      <td>COST</td>
      <td>879.210022</td>
      <td>70.189136</td>
    </tr>
    <tr>
      <th>31</th>
      <td>URI</td>
      <td>745.030029</td>
      <td>68.928495</td>
    </tr>
    <tr>
      <th>32</th>
      <td>NFLX</td>
      <td>686.72998</td>
      <td>68.758753</td>
    </tr>
    <tr>
      <th>33</th>
      <td>KEY</td>
      <td>17.07</td>
      <td>67.576445</td>
    </tr>
    <tr>
      <th>34</th>
      <td>CFG</td>
      <td>42.889999</td>
      <td>66.887066</td>
    </tr>
    <tr>
      <th>35</th>
      <td>STX</td>
      <td>104.410004</td>
      <td>66.409291</td>
    </tr>
    <tr>
      <th>36</th>
      <td>UBER</td>
      <td>74.300003</td>
      <td>66.293649</td>
    </tr>
    <tr>
      <th>37</th>
      <td>DHI</td>
      <td>191.789993</td>
      <td>65.692032</td>
    </tr>
    <tr>
      <th>38</th>
      <td>MMM</td>
      <td>130.550003</td>
      <td>64.821166</td>
    </tr>
    <tr>
      <th>39</th>
      <td>RCL</td>
      <td>163.080002</td>
      <td>64.644116</td>
    </tr>
    <tr>
      <th>40</th>
      <td>GS</td>
      <td>509.420013</td>
      <td>63.992997</td>
    </tr>
    <tr>
      <th>41</th>
      <td>MHK</td>
      <td>157.75</td>
      <td>63.641076</td>
    </tr>
    <tr>
      <th>42</th>
      <td>QCOM</td>
      <td>173.5</td>
      <td>63.539937</td>
    </tr>
    <tr>
      <th>43</th>
      <td>CTAS</td>
      <td>788.5</td>
      <td>63.032138</td>
    </tr>
    <tr>
      <th>44</th>
      <td>LDOS</td>
      <td>154.899994</td>
      <td>62.747737</td>
    </tr>
    <tr>
      <th>45</th>
      <td>MU</td>
      <td>102.849998</td>
      <td>62.269457</td>
    </tr>
    <tr>
      <th>46</th>
      <td>LEN</td>
      <td>185.020004</td>
      <td>61.796624</td>
    </tr>
    <tr>
      <th>47</th>
      <td>AXP</td>
      <td>251.300003</td>
      <td>61.409735</td>
    </tr>
    <tr>
      <th>48</th>
      <td>WDC</td>
      <td>64.349998</td>
      <td>61.399549</td>
    </tr>
    <tr>
      <th>49</th>
      <td>TFC</td>
      <td>43.84</td>
      <td>60.900443</td>
    </tr>
  </tbody>
</table>
</div>




```python
def enter_portfolio():
    while True:
        portfolio_size = input("Enter portfolio size: ")
        try:
            portfolio_size = float(portfolio_size)
            return portfolio_size
        except ValueError:
            print(f"The entered value '{portfolio_size}' is not a valid portfolio size. Please enter an integer or float and try again.\n")

portfolio_size = enter_portfolio()
```

    Enter portfolio size:  10000000
    

# Portfolio Allocation and Share Calculation

## 1. Determine Position Size

The **position size** represents the amount of money allocated to each stock. This is calculated by dividing the total portfolio size by the number of stocks.

**Mathematical Formula:**

$$ \text{Position Size} = \frac{\text{Total Portfolio Size}}{\text{Number of Stocks}} $$

**Example Calculation:**

- Total Portfolio Size: \$9,000
- Number of Stocks: 3

$$ \text{Position Size} = \frac{9,000}{3} \approx 3,000 $$

Each stock gets approximately \$3,000 to invest.

## 2. Calculate Number of Shares to Buy

For each stock, you need to determine how many shares can be bought with the allocated position size. This is done by dividing the position size by the stock price and rounding down to the nearest integer.

**Mathematical Formula:**

$$ \text{Number of Shares to Buy} = \left\lfloor \frac{\text{Position Size}}{\text{Stock Price}} \right\rfloor \text{rounded down to the nearest integer.} $$

This approach ensures that you evenly distribute your investment across the stocks in your portfolio and determine how many whole shares you can buy with the allocated funds.mine how many whole shares you can buy with the allocated funds.
mine how many whole shares you can buy with the allocated funds.



```python
import math

position_size = portfolio_size/len(sp500_df.index)
sp500_df['No of shares to buy'] = (position_size/sp500_df['Stock Price']).apply(math.floor)
```


```python
sp500_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Ticker</th>
      <th>Stock Price</th>
      <th>One Year Return</th>
      <th>No of shares to buy</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>VST</td>
      <td>85.769997</td>
      <td>190.958329</td>
      <td>2331</td>
    </tr>
    <tr>
      <th>1</th>
      <td>NVDA</td>
      <td>129.369995</td>
      <td>174.386125</td>
      <td>1545</td>
    </tr>
    <tr>
      <th>2</th>
      <td>SMCI</td>
      <td>613.23999</td>
      <td>133.615234</td>
      <td>326</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NRG</td>
      <td>83.5</td>
      <td>131.977629</td>
      <td>2395</td>
    </tr>
    <tr>
      <th>4</th>
      <td>GDDY</td>
      <td>162.449997</td>
      <td>131.509194</td>
      <td>1231</td>
    </tr>
    <tr>
      <th>5</th>
      <td>KKR</td>
      <td>122.230003</td>
      <td>106.793081</td>
      <td>1636</td>
    </tr>
    <tr>
      <th>6</th>
      <td>FICO</td>
      <td>1745.380005</td>
      <td>106.088021</td>
      <td>114</td>
    </tr>
    <tr>
      <th>7</th>
      <td>HWM</td>
      <td>97.080002</td>
      <td>102.425855</td>
      <td>2060</td>
    </tr>
    <tr>
      <th>8</th>
      <td>ANET</td>
      <td>355.130005</td>
      <td>98.186283</td>
      <td>563</td>
    </tr>
    <tr>
      <th>9</th>
      <td>AVGO</td>
      <td>166.360001</td>
      <td>98.1212</td>
      <td>1202</td>
    </tr>
    <tr>
      <th>10</th>
      <td>GE</td>
      <td>171.220001</td>
      <td>94.141132</td>
      <td>1168</td>
    </tr>
    <tr>
      <th>11</th>
      <td>IRM</td>
      <td>113.349998</td>
      <td>94.007159</td>
      <td>1764</td>
    </tr>
    <tr>
      <th>12</th>
      <td>MPWR</td>
      <td>936.289978</td>
      <td>93.257056</td>
      <td>213</td>
    </tr>
    <tr>
      <th>13</th>
      <td>AXON</td>
      <td>370.700012</td>
      <td>89.123015</td>
      <td>539</td>
    </tr>
    <tr>
      <th>14</th>
      <td>DECK</td>
      <td>974.559998</td>
      <td>86.776025</td>
      <td>205</td>
    </tr>
    <tr>
      <th>15</th>
      <td>CRWD</td>
      <td>271.540009</td>
      <td>86.689594</td>
      <td>736</td>
    </tr>
    <tr>
      <th>16</th>
      <td>META</td>
      <td>528.0</td>
      <td>84.510899</td>
      <td>378</td>
    </tr>
    <tr>
      <th>17</th>
      <td>PGR</td>
      <td>241.25</td>
      <td>84.130236</td>
      <td>829</td>
    </tr>
    <tr>
      <th>18</th>
      <td>CEG</td>
      <td>194.990005</td>
      <td>83.773422</td>
      <td>1025</td>
    </tr>
    <tr>
      <th>19</th>
      <td>UHS</td>
      <td>233.139999</td>
      <td>80.102106</td>
      <td>857</td>
    </tr>
    <tr>
      <th>20</th>
      <td>NTAP</td>
      <td>133.119995</td>
      <td>80.019912</td>
      <td>1502</td>
    </tr>
    <tr>
      <th>21</th>
      <td>GRMN</td>
      <td>179.759995</td>
      <td>79.644866</td>
      <td>1112</td>
    </tr>
    <tr>
      <th>22</th>
      <td>TT</td>
      <td>352.910004</td>
      <td>79.280455</td>
      <td>566</td>
    </tr>
    <tr>
      <th>23</th>
      <td>ALL</td>
      <td>180.509995</td>
      <td>75.927363</td>
      <td>1107</td>
    </tr>
    <tr>
      <th>24</th>
      <td>TRGP</td>
      <td>144.130005</td>
      <td>75.525569</td>
      <td>1387</td>
    </tr>
    <tr>
      <th>25</th>
      <td>LLY</td>
      <td>952.73999</td>
      <td>75.025842</td>
      <td>209</td>
    </tr>
    <tr>
      <th>26</th>
      <td>PHM</td>
      <td>135.130005</td>
      <td>73.722489</td>
      <td>1480</td>
    </tr>
    <tr>
      <th>27</th>
      <td>KLAC</td>
      <td>817.840027</td>
      <td>73.193321</td>
      <td>244</td>
    </tr>
    <tr>
      <th>28</th>
      <td>FITB</td>
      <td>42.119999</td>
      <td>71.092699</td>
      <td>4748</td>
    </tr>
    <tr>
      <th>29</th>
      <td>ISRG</td>
      <td>486.549988</td>
      <td>70.336775</td>
      <td>411</td>
    </tr>
    <tr>
      <th>30</th>
      <td>COST</td>
      <td>879.210022</td>
      <td>70.189136</td>
      <td>227</td>
    </tr>
    <tr>
      <th>31</th>
      <td>URI</td>
      <td>745.030029</td>
      <td>68.928495</td>
      <td>268</td>
    </tr>
    <tr>
      <th>32</th>
      <td>NFLX</td>
      <td>686.72998</td>
      <td>68.758753</td>
      <td>291</td>
    </tr>
    <tr>
      <th>33</th>
      <td>KEY</td>
      <td>17.07</td>
      <td>67.576445</td>
      <td>11716</td>
    </tr>
    <tr>
      <th>34</th>
      <td>CFG</td>
      <td>42.889999</td>
      <td>66.887066</td>
      <td>4663</td>
    </tr>
    <tr>
      <th>35</th>
      <td>STX</td>
      <td>104.410004</td>
      <td>66.409291</td>
      <td>1915</td>
    </tr>
    <tr>
      <th>36</th>
      <td>UBER</td>
      <td>74.300003</td>
      <td>66.293649</td>
      <td>2691</td>
    </tr>
    <tr>
      <th>37</th>
      <td>DHI</td>
      <td>191.789993</td>
      <td>65.692032</td>
      <td>1042</td>
    </tr>
    <tr>
      <th>38</th>
      <td>MMM</td>
      <td>130.550003</td>
      <td>64.821166</td>
      <td>1531</td>
    </tr>
    <tr>
      <th>39</th>
      <td>RCL</td>
      <td>163.080002</td>
      <td>64.644116</td>
      <td>1226</td>
    </tr>
    <tr>
      <th>40</th>
      <td>GS</td>
      <td>509.420013</td>
      <td>63.992997</td>
      <td>392</td>
    </tr>
    <tr>
      <th>41</th>
      <td>MHK</td>
      <td>157.75</td>
      <td>63.641076</td>
      <td>1267</td>
    </tr>
    <tr>
      <th>42</th>
      <td>QCOM</td>
      <td>173.5</td>
      <td>63.539937</td>
      <td>1152</td>
    </tr>
    <tr>
      <th>43</th>
      <td>CTAS</td>
      <td>788.5</td>
      <td>63.032138</td>
      <td>253</td>
    </tr>
    <tr>
      <th>44</th>
      <td>LDOS</td>
      <td>154.899994</td>
      <td>62.747737</td>
      <td>1291</td>
    </tr>
    <tr>
      <th>45</th>
      <td>MU</td>
      <td>102.849998</td>
      <td>62.269457</td>
      <td>1944</td>
    </tr>
    <tr>
      <th>46</th>
      <td>LEN</td>
      <td>185.020004</td>
      <td>61.796624</td>
      <td>1080</td>
    </tr>
    <tr>
      <th>47</th>
      <td>AXP</td>
      <td>251.300003</td>
      <td>61.409735</td>
      <td>795</td>
    </tr>
    <tr>
      <th>48</th>
      <td>WDC</td>
      <td>64.349998</td>
      <td>61.399549</td>
      <td>3108</td>
    </tr>
    <tr>
      <th>49</th>
      <td>TFC</td>
      <td>43.84</td>
      <td>60.900443</td>
      <td>4562</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Initiate an empty list to hold the dictionaries for each ticker
# This list is later converted to the hqm dataframe
data_frames = []

# Take each ticker and populate all required columns
for t in sp500_df['Ticker']:
    if t in data_download.columns:
        # Temporary dataframe for current ticker to calculate returns
        temp_df = data_download[t].dropna()
        
        # Calculate returns
        one_month_return = temp_df.pct_change(periods=21).iloc[-1] * 100
        three_month_return = temp_df.pct_change(periods=63).iloc[-1] * 100
        six_month_return = temp_df.pct_change(periods=126).iloc[-1] * 100

        # Dataframe for current ticker to populate all required columns
        ticker_df = pd.DataFrame([{
            'Ticker':t,
            'Stock Price':sp500_df.loc[sp500_df['Ticker'] == t, 'Stock Price'].iloc[0],
            'No of shares to buy': None,
            'One Year Price Return':sp500_df.loc[sp500_df['Ticker'] == t, 'One Year Return'].iloc[0],
            'Six Month Price Return':six_month_return,
            'Three Month Price Return':three_month_return,
            'One Month Price Return': one_month_return,
            'HQM Score': None
        }])

        # Append the current ticker dataframe to the initiated list
        data_frames.append(ticker_df)
    else:
        print(f"Ticker {t} not found in price data.")
```

### **What is HQM Score?**

The **HQM (High-Quality Momentum) Score** is a metric used in quantitative finance to assess the momentum of a financial asset, such as a stock, over various time periods. Momentum is a measure of the tendency of an asset's price to continue moving in its current direction—either up or down—over time.

#### **How HQM Score Works:**

- **Multiple Time Periods:** The HQM Score aggregates momentum measurements over different time periods, such as one year, six months, three months, and one month. This allows for a more comprehensive view of the asset's performance over time, capturing both short-term and long-term trends.

- **Percentiles:** For each time period, the asset's return is compared to other assets in the same dataset, and a percentile ranking is assigned. For example, if a stock's one-year return is in the 90th percentile, it means it has outperformed 90% of the other assets over that period.

- **Average Percentile:** The HQM Score is typically calculated by taking the average of these percentile rankings across all selected time periods. A higher HQM Score indicates stronger and more consistent momentum across different timeframes.

#### **Use in Investing:**

Investors and analysts use the HQM Score to identify assets that have shown strong performance over multiple time periods, with the expectation that these assets may continue to perform well in the future. It can be particularly useful in momentum-based strategies, where the goal is to invest in assets that are trending upwards.



```python
# Vertically stack each ticker_df appended to a single dataframe
# Each ticker_df forms a new row
hqm_df = pd.concat(data_frames, ignore_index=True) 

# Calculate percentiles for each return periods
def calculate_percentiles(df, column_name):
    return df[column_name].rank(pct=True) * 100

# Compute percentiles for each return period
hqm_df['One Year Return Percentile'] = calculate_percentiles(hqm_df, 'One Year Price Return')
hqm_df['Six Month Return Percentile'] = calculate_percentiles(hqm_df, 'Six Month Price Return')
hqm_df['Three Month Return Percentile'] = calculate_percentiles(hqm_df, 'Three Month Price Return')
hqm_df['One Month Return Percentile'] = calculate_percentiles(hqm_df, 'One Month Price Return')
```


```python
hqm_df = hqm_df[['Ticker','Stock Price','HQM Score','No of shares to buy','One Year Price Return','One Year Return Percentile','Six Month Price Return','Six Month Return Percentile','Three Month Price Return','Three Month Return Percentile','One Month Price Return','One Month Return Percentile']]
hqm_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Ticker</th>
      <th>Stock Price</th>
      <th>HQM Score</th>
      <th>No of shares to buy</th>
      <th>One Year Price Return</th>
      <th>One Year Return Percentile</th>
      <th>Six Month Price Return</th>
      <th>Six Month Return Percentile</th>
      <th>Three Month Price Return</th>
      <th>Three Month Return Percentile</th>
      <th>One Month Price Return</th>
      <th>One Month Return Percentile</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>VST</td>
      <td>85.769997</td>
      <td>None</td>
      <td>None</td>
      <td>190.958329</td>
      <td>100.0</td>
      <td>77.478408</td>
      <td>100.0</td>
      <td>-10.545029</td>
      <td>14.0</td>
      <td>21.867008</td>
      <td>98.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>NVDA</td>
      <td>129.369995</td>
      <td>None</td>
      <td>None</td>
      <td>174.386125</td>
      <td>98.0</td>
      <td>64.160889</td>
      <td>96.0</td>
      <td>24.645337</td>
      <td>82.0</td>
      <td>15.220873</td>
      <td>80.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>SMCI</td>
      <td>613.239990</td>
      <td>None</td>
      <td>None</td>
      <td>133.615234</td>
      <td>96.0</td>
      <td>-28.693854</td>
      <td>2.0</td>
      <td>-27.631053</td>
      <td>2.0</td>
      <td>-11.841405</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NRG</td>
      <td>83.500000</td>
      <td>None</td>
      <td>None</td>
      <td>131.977629</td>
      <td>94.0</td>
      <td>63.766170</td>
      <td>94.0</td>
      <td>3.533962</td>
      <td>16.0</td>
      <td>14.866184</td>
      <td>78.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>GDDY</td>
      <td>162.449997</td>
      <td>None</td>
      <td>None</td>
      <td>131.509194</td>
      <td>92.0</td>
      <td>41.371501</td>
      <td>80.0</td>
      <td>17.241628</td>
      <td>58.0</td>
      <td>13.371488</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>KKR</td>
      <td>122.230003</td>
      <td>None</td>
      <td>None</td>
      <td>106.793081</td>
      <td>90.0</td>
      <td>28.004258</td>
      <td>50.0</td>
      <td>17.732384</td>
      <td>60.0</td>
      <td>4.890878</td>
      <td>32.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>FICO</td>
      <td>1745.380005</td>
      <td>None</td>
      <td>None</td>
      <td>106.088021</td>
      <td>88.0</td>
      <td>36.110055</td>
      <td>70.0</td>
      <td>28.983575</td>
      <td>88.0</td>
      <td>10.682145</td>
      <td>58.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>HWM</td>
      <td>97.080002</td>
      <td>None</td>
      <td>None</td>
      <td>102.425855</td>
      <td>86.0</td>
      <td>47.600165</td>
      <td>86.0</td>
      <td>17.889507</td>
      <td>64.0</td>
      <td>18.004051</td>
      <td>92.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>ANET</td>
      <td>355.130005</td>
      <td>None</td>
      <td>None</td>
      <td>98.186283</td>
      <td>84.0</td>
      <td>32.679519</td>
      <td>64.0</td>
      <td>17.818986</td>
      <td>62.0</td>
      <td>13.055523</td>
      <td>68.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>AVGO</td>
      <td>166.360001</td>
      <td>None</td>
      <td>None</td>
      <td>98.121200</td>
      <td>82.0</td>
      <td>29.283297</td>
      <td>56.0</td>
      <td>19.779980</td>
      <td>72.0</td>
      <td>11.456523</td>
      <td>64.0</td>
    </tr>
    <tr>
      <th>10</th>
      <td>GE</td>
      <td>171.220001</td>
      <td>None</td>
      <td>None</td>
      <td>94.141132</td>
      <td>80.0</td>
      <td>40.405726</td>
      <td>76.0</td>
      <td>3.781810</td>
      <td>20.0</td>
      <td>3.977654</td>
      <td>26.0</td>
    </tr>
    <tr>
      <th>11</th>
      <td>IRM</td>
      <td>113.349998</td>
      <td>None</td>
      <td>None</td>
      <td>94.007159</td>
      <td>78.0</td>
      <td>53.441985</td>
      <td>90.0</td>
      <td>44.037942</td>
      <td>100.0</td>
      <td>16.976261</td>
      <td>88.0</td>
    </tr>
    <tr>
      <th>12</th>
      <td>MPWR</td>
      <td>936.289978</td>
      <td>None</td>
      <td>None</td>
      <td>93.257056</td>
      <td>76.0</td>
      <td>30.281345</td>
      <td>58.0</td>
      <td>25.636169</td>
      <td>84.0</td>
      <td>18.532719</td>
      <td>94.0</td>
    </tr>
    <tr>
      <th>13</th>
      <td>AXON</td>
      <td>370.700012</td>
      <td>None</td>
      <td>None</td>
      <td>89.123015</td>
      <td>74.0</td>
      <td>36.976686</td>
      <td>72.0</td>
      <td>32.397595</td>
      <td>94.0</td>
      <td>19.269012</td>
      <td>96.0</td>
    </tr>
    <tr>
      <th>14</th>
      <td>DECK</td>
      <td>974.559998</td>
      <td>None</td>
      <td>None</td>
      <td>86.776025</td>
      <td>72.0</td>
      <td>10.685083</td>
      <td>10.0</td>
      <td>7.727847</td>
      <td>28.0</td>
      <td>15.812240</td>
      <td>82.0</td>
    </tr>
    <tr>
      <th>15</th>
      <td>CRWD</td>
      <td>271.540009</td>
      <td>None</td>
      <td>None</td>
      <td>86.689594</td>
      <td>70.0</td>
      <td>-12.825446</td>
      <td>4.0</td>
      <td>-20.683510</td>
      <td>4.0</td>
      <td>6.842422</td>
      <td>38.0</td>
    </tr>
    <tr>
      <th>16</th>
      <td>META</td>
      <td>528.000000</td>
      <td>None</td>
      <td>None</td>
      <td>84.510899</td>
      <td>68.0</td>
      <td>9.192454</td>
      <td>8.0</td>
      <td>13.470789</td>
      <td>46.0</td>
      <td>16.450893</td>
      <td>86.0</td>
    </tr>
    <tr>
      <th>17</th>
      <td>PGR</td>
      <td>241.250000</td>
      <td>None</td>
      <td>None</td>
      <td>84.130236</td>
      <td>66.0</td>
      <td>26.230686</td>
      <td>46.0</td>
      <td>18.793352</td>
      <td>68.0</td>
      <td>13.385343</td>
      <td>72.0</td>
    </tr>
    <tr>
      <th>18</th>
      <td>CEG</td>
      <td>194.990005</td>
      <td>None</td>
      <td>None</td>
      <td>83.773422</td>
      <td>64.0</td>
      <td>46.306687</td>
      <td>84.0</td>
      <td>-11.533804</td>
      <td>12.0</td>
      <td>14.623725</td>
      <td>76.0</td>
    </tr>
    <tr>
      <th>19</th>
      <td>UHS</td>
      <td>233.139999</td>
      <td>None</td>
      <td>None</td>
      <td>80.102106</td>
      <td>62.0</td>
      <td>42.215870</td>
      <td>82.0</td>
      <td>31.923533</td>
      <td>92.0</td>
      <td>13.732374</td>
      <td>74.0</td>
    </tr>
    <tr>
      <th>20</th>
      <td>NTAP</td>
      <td>133.119995</td>
      <td>None</td>
      <td>None</td>
      <td>80.019912</td>
      <td>60.0</td>
      <td>53.643131</td>
      <td>92.0</td>
      <td>17.198830</td>
      <td>56.0</td>
      <td>6.021024</td>
      <td>36.0</td>
    </tr>
    <tr>
      <th>21</th>
      <td>GRMN</td>
      <td>179.759995</td>
      <td>None</td>
      <td>None</td>
      <td>79.644866</td>
      <td>58.0</td>
      <td>33.940099</td>
      <td>68.0</td>
      <td>10.986972</td>
      <td>36.0</td>
      <td>3.667821</td>
      <td>24.0</td>
    </tr>
    <tr>
      <th>22</th>
      <td>TT</td>
      <td>352.910004</td>
      <td>None</td>
      <td>None</td>
      <td>79.280455</td>
      <td>56.0</td>
      <td>25.929444</td>
      <td>44.0</td>
      <td>6.284790</td>
      <td>22.0</td>
      <td>9.524549</td>
      <td>54.0</td>
    </tr>
    <tr>
      <th>23</th>
      <td>ALL</td>
      <td>180.509995</td>
      <td>None</td>
      <td>None</td>
      <td>75.927363</td>
      <td>54.0</td>
      <td>14.733369</td>
      <td>16.0</td>
      <td>10.684294</td>
      <td>34.0</td>
      <td>9.135430</td>
      <td>52.0</td>
    </tr>
    <tr>
      <th>24</th>
      <td>TRGP</td>
      <td>144.130005</td>
      <td>None</td>
      <td>None</td>
      <td>75.525569</td>
      <td>52.0</td>
      <td>50.341765</td>
      <td>88.0</td>
      <td>27.308202</td>
      <td>86.0</td>
      <td>9.819963</td>
      <td>56.0</td>
    </tr>
    <tr>
      <th>25</th>
      <td>LLY</td>
      <td>952.739990</td>
      <td>None</td>
      <td>None</td>
      <td>75.025842</td>
      <td>50.0</td>
      <td>24.190751</td>
      <td>38.0</td>
      <td>18.012396</td>
      <td>66.0</td>
      <td>16.181543</td>
      <td>84.0</td>
    </tr>
    <tr>
      <th>26</th>
      <td>PHM</td>
      <td>135.130005</td>
      <td>None</td>
      <td>None</td>
      <td>73.722489</td>
      <td>48.0</td>
      <td>28.242824</td>
      <td>54.0</td>
      <td>20.069757</td>
      <td>74.0</td>
      <td>8.104004</td>
      <td>48.0</td>
    </tr>
    <tr>
      <th>27</th>
      <td>KLAC</td>
      <td>817.840027</td>
      <td>None</td>
      <td>None</td>
      <td>73.193321</td>
      <td>46.0</td>
      <td>22.754029</td>
      <td>32.0</td>
      <td>7.088813</td>
      <td>26.0</td>
      <td>7.410302</td>
      <td>42.0</td>
    </tr>
    <tr>
      <th>28</th>
      <td>FITB</td>
      <td>42.119999</td>
      <td>None</td>
      <td>None</td>
      <td>71.092699</td>
      <td>44.0</td>
      <td>28.139944</td>
      <td>52.0</td>
      <td>15.522182</td>
      <td>50.0</td>
      <td>0.693275</td>
      <td>18.0</td>
    </tr>
    <tr>
      <th>29</th>
      <td>ISRG</td>
      <td>486.549988</td>
      <td>None</td>
      <td>None</td>
      <td>70.336775</td>
      <td>42.0</td>
      <td>24.830028</td>
      <td>40.0</td>
      <td>22.129062</td>
      <td>78.0</td>
      <td>11.404955</td>
      <td>62.0</td>
    </tr>
    <tr>
      <th>30</th>
      <td>COST</td>
      <td>879.210022</td>
      <td>None</td>
      <td>None</td>
      <td>70.189136</td>
      <td>40.0</td>
      <td>19.506574</td>
      <td>24.0</td>
      <td>10.563536</td>
      <td>32.0</td>
      <td>7.906329</td>
      <td>44.0</td>
    </tr>
    <tr>
      <th>31</th>
      <td>URI</td>
      <td>745.030029</td>
      <td>None</td>
      <td>None</td>
      <td>68.928495</td>
      <td>38.0</td>
      <td>13.721157</td>
      <td>14.0</td>
      <td>11.996825</td>
      <td>42.0</td>
      <td>-0.994189</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>32</th>
      <td>NFLX</td>
      <td>686.729980</td>
      <td>None</td>
      <td>None</td>
      <td>68.758753</td>
      <td>36.0</td>
      <td>17.679413</td>
      <td>20.0</td>
      <td>8.032470</td>
      <td>30.0</td>
      <td>8.301653</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>33</th>
      <td>KEY</td>
      <td>17.070000</td>
      <td>None</td>
      <td>None</td>
      <td>67.576445</td>
      <td>34.0</td>
      <td>23.198015</td>
      <td>34.0</td>
      <td>19.747454</td>
      <td>70.0</td>
      <td>5.827654</td>
      <td>34.0</td>
    </tr>
    <tr>
      <th>34</th>
      <td>CFG</td>
      <td>42.889999</td>
      <td>None</td>
      <td>None</td>
      <td>66.887066</td>
      <td>32.0</td>
      <td>40.730115</td>
      <td>78.0</td>
      <td>23.323128</td>
      <td>80.0</td>
      <td>0.164384</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>35</th>
      <td>STX</td>
      <td>104.410004</td>
      <td>None</td>
      <td>None</td>
      <td>66.409291</td>
      <td>30.0</td>
      <td>20.437535</td>
      <td>30.0</td>
      <td>12.458973</td>
      <td>44.0</td>
      <td>0.432863</td>
      <td>14.0</td>
    </tr>
    <tr>
      <th>36</th>
      <td>UBER</td>
      <td>74.300003</td>
      <td>None</td>
      <td>None</td>
      <td>66.293649</td>
      <td>28.0</td>
      <td>-4.987205</td>
      <td>6.0</td>
      <td>16.823907</td>
      <td>54.0</td>
      <td>13.021000</td>
      <td>66.0</td>
    </tr>
    <tr>
      <th>37</th>
      <td>DHI</td>
      <td>191.789993</td>
      <td>None</td>
      <td>None</td>
      <td>65.692032</td>
      <td>26.0</td>
      <td>31.769766</td>
      <td>60.0</td>
      <td>34.512180</td>
      <td>96.0</td>
      <td>11.239322</td>
      <td>60.0</td>
    </tr>
    <tr>
      <th>38</th>
      <td>MMM</td>
      <td>130.550003</td>
      <td>None</td>
      <td>None</td>
      <td>64.821166</td>
      <td>24.0</td>
      <td>69.823064</td>
      <td>98.0</td>
      <td>31.192845</td>
      <td>90.0</td>
      <td>26.269469</td>
      <td>100.0</td>
    </tr>
    <tr>
      <th>39</th>
      <td>RCL</td>
      <td>163.080002</td>
      <td>None</td>
      <td>None</td>
      <td>64.644116</td>
      <td>22.0</td>
      <td>33.770812</td>
      <td>66.0</td>
      <td>11.461967</td>
      <td>38.0</td>
      <td>7.275357</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>40</th>
      <td>GS</td>
      <td>509.420013</td>
      <td>None</td>
      <td>None</td>
      <td>63.992997</td>
      <td>20.0</td>
      <td>31.986890</td>
      <td>62.0</td>
      <td>11.863550</td>
      <td>40.0</td>
      <td>3.601721</td>
      <td>22.0</td>
    </tr>
    <tr>
      <th>41</th>
      <td>MHK</td>
      <td>157.750000</td>
      <td>None</td>
      <td>None</td>
      <td>63.641076</td>
      <td>18.0</td>
      <td>37.245516</td>
      <td>74.0</td>
      <td>36.273322</td>
      <td>98.0</td>
      <td>17.286245</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th>42</th>
      <td>QCOM</td>
      <td>173.500000</td>
      <td>None</td>
      <td>None</td>
      <td>63.539937</td>
      <td>16.0</td>
      <td>13.030732</td>
      <td>12.0</td>
      <td>-13.654324</td>
      <td>8.0</td>
      <td>-1.077598</td>
      <td>8.0</td>
    </tr>
    <tr>
      <th>43</th>
      <td>CTAS</td>
      <td>788.500000</td>
      <td>None</td>
      <td>None</td>
      <td>63.032138</td>
      <td>14.0</td>
      <td>25.045616</td>
      <td>42.0</td>
      <td>13.510866</td>
      <td>48.0</td>
      <td>4.673190</td>
      <td>30.0</td>
    </tr>
    <tr>
      <th>44</th>
      <td>LDOS</td>
      <td>154.899994</td>
      <td>None</td>
      <td>None</td>
      <td>62.747737</td>
      <td>12.0</td>
      <td>23.569417</td>
      <td>36.0</td>
      <td>3.698614</td>
      <td>18.0</td>
      <td>1.894481</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>45</th>
      <td>MU</td>
      <td>102.849998</td>
      <td>None</td>
      <td>None</td>
      <td>62.269457</td>
      <td>10.0</td>
      <td>19.813161</td>
      <td>26.0</td>
      <td>-18.476315</td>
      <td>6.0</td>
      <td>-4.281060</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>46</th>
      <td>LEN</td>
      <td>185.020004</td>
      <td>None</td>
      <td>None</td>
      <td>61.796624</td>
      <td>8.0</td>
      <td>20.120223</td>
      <td>28.0</td>
      <td>20.157861</td>
      <td>76.0</td>
      <td>8.021956</td>
      <td>46.0</td>
    </tr>
    <tr>
      <th>47</th>
      <td>AXP</td>
      <td>251.300003</td>
      <td>None</td>
      <td>None</td>
      <td>61.409735</td>
      <td>6.0</td>
      <td>17.836248</td>
      <td>22.0</td>
      <td>7.045149</td>
      <td>24.0</td>
      <td>4.629865</td>
      <td>28.0</td>
    </tr>
    <tr>
      <th>48</th>
      <td>WDC</td>
      <td>64.349998</td>
      <td>None</td>
      <td>None</td>
      <td>61.399549</td>
      <td>4.0</td>
      <td>14.787722</td>
      <td>18.0</td>
      <td>-13.228162</td>
      <td>10.0</td>
      <td>-3.218528</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>49</th>
      <td>TFC</td>
      <td>43.840000</td>
      <td>None</td>
      <td>None</td>
      <td>60.900443</td>
      <td>2.0</td>
      <td>27.646097</td>
      <td>48.0</td>
      <td>16.079126</td>
      <td>52.0</td>
      <td>0.608929</td>
      <td>16.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
from statistics import mean

time_periods = [
    'One Year',
    'Six Month',
    'Three Month',
    'One Month'
]

# Populate HQM score for each ticker row
for row in hqm_df.index:
    # Collect return percentile for each time period for each ticker row. 
    # HQM score is the mean of these percentiles. 
    momentum_percentiles = []
    for t in time_periods:
        momentum_percentiles.append(hqm_df.loc[row,f'{t} Return Percentile'])
    hqm_df.loc[row,'HQM Score'] = mean(momentum_percentiles)
```


```python
hqm_df.sort_values(by='HQM Score', ascending=False)
hqm_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Ticker</th>
      <th>Stock Price</th>
      <th>HQM Score</th>
      <th>No of shares to buy</th>
      <th>One Year Price Return</th>
      <th>One Year Return Percentile</th>
      <th>Six Month Price Return</th>
      <th>Six Month Return Percentile</th>
      <th>Three Month Price Return</th>
      <th>Three Month Return Percentile</th>
      <th>One Month Price Return</th>
      <th>One Month Return Percentile</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>VST</td>
      <td>85.769997</td>
      <td>78.0</td>
      <td>None</td>
      <td>190.958329</td>
      <td>100.0</td>
      <td>77.478408</td>
      <td>100.0</td>
      <td>-10.545029</td>
      <td>14.0</td>
      <td>21.867008</td>
      <td>98.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>NVDA</td>
      <td>129.369995</td>
      <td>89.0</td>
      <td>None</td>
      <td>174.386125</td>
      <td>98.0</td>
      <td>64.160889</td>
      <td>96.0</td>
      <td>24.645337</td>
      <td>82.0</td>
      <td>15.220873</td>
      <td>80.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>SMCI</td>
      <td>613.239990</td>
      <td>25.5</td>
      <td>None</td>
      <td>133.615234</td>
      <td>96.0</td>
      <td>-28.693854</td>
      <td>2.0</td>
      <td>-27.631053</td>
      <td>2.0</td>
      <td>-11.841405</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NRG</td>
      <td>83.500000</td>
      <td>70.5</td>
      <td>None</td>
      <td>131.977629</td>
      <td>94.0</td>
      <td>63.766170</td>
      <td>94.0</td>
      <td>3.533962</td>
      <td>16.0</td>
      <td>14.866184</td>
      <td>78.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>GDDY</td>
      <td>162.449997</td>
      <td>75.0</td>
      <td>None</td>
      <td>131.509194</td>
      <td>92.0</td>
      <td>41.371501</td>
      <td>80.0</td>
      <td>17.241628</td>
      <td>58.0</td>
      <td>13.371488</td>
      <td>70.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
# No of shares to Buy
position_size = portfolio_size/len(hqm_df.index)
hqm_df['No of shares to buy'] = (position_size/hqm_df['Stock Price']).apply(math.floor)
```


```python
hqm_df
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Ticker</th>
      <th>Stock Price</th>
      <th>HQM Score</th>
      <th>No of shares to buy</th>
      <th>One Year Price Return</th>
      <th>One Year Return Percentile</th>
      <th>Six Month Price Return</th>
      <th>Six Month Return Percentile</th>
      <th>Three Month Price Return</th>
      <th>Three Month Return Percentile</th>
      <th>One Month Price Return</th>
      <th>One Month Return Percentile</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>VST</td>
      <td>85.769997</td>
      <td>78.0</td>
      <td>2331</td>
      <td>190.958329</td>
      <td>100.0</td>
      <td>77.478408</td>
      <td>100.0</td>
      <td>-10.545029</td>
      <td>14.0</td>
      <td>21.867008</td>
      <td>98.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>NVDA</td>
      <td>129.369995</td>
      <td>89.0</td>
      <td>1545</td>
      <td>174.386125</td>
      <td>98.0</td>
      <td>64.160889</td>
      <td>96.0</td>
      <td>24.645337</td>
      <td>82.0</td>
      <td>15.220873</td>
      <td>80.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>SMCI</td>
      <td>613.239990</td>
      <td>25.5</td>
      <td>326</td>
      <td>133.615234</td>
      <td>96.0</td>
      <td>-28.693854</td>
      <td>2.0</td>
      <td>-27.631053</td>
      <td>2.0</td>
      <td>-11.841405</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NRG</td>
      <td>83.500000</td>
      <td>70.5</td>
      <td>2395</td>
      <td>131.977629</td>
      <td>94.0</td>
      <td>63.766170</td>
      <td>94.0</td>
      <td>3.533962</td>
      <td>16.0</td>
      <td>14.866184</td>
      <td>78.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>GDDY</td>
      <td>162.449997</td>
      <td>75.0</td>
      <td>1231</td>
      <td>131.509194</td>
      <td>92.0</td>
      <td>41.371501</td>
      <td>80.0</td>
      <td>17.241628</td>
      <td>58.0</td>
      <td>13.371488</td>
      <td>70.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>KKR</td>
      <td>122.230003</td>
      <td>58.0</td>
      <td>1636</td>
      <td>106.793081</td>
      <td>90.0</td>
      <td>28.004258</td>
      <td>50.0</td>
      <td>17.732384</td>
      <td>60.0</td>
      <td>4.890878</td>
      <td>32.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>FICO</td>
      <td>1745.380005</td>
      <td>76.0</td>
      <td>114</td>
      <td>106.088021</td>
      <td>88.0</td>
      <td>36.110055</td>
      <td>70.0</td>
      <td>28.983575</td>
      <td>88.0</td>
      <td>10.682145</td>
      <td>58.0</td>
    </tr>
    <tr>
      <th>7</th>
      <td>HWM</td>
      <td>97.080002</td>
      <td>82.0</td>
      <td>2060</td>
      <td>102.425855</td>
      <td>86.0</td>
      <td>47.600165</td>
      <td>86.0</td>
      <td>17.889507</td>
      <td>64.0</td>
      <td>18.004051</td>
      <td>92.0</td>
    </tr>
    <tr>
      <th>8</th>
      <td>ANET</td>
      <td>355.130005</td>
      <td>69.5</td>
      <td>563</td>
      <td>98.186283</td>
      <td>84.0</td>
      <td>32.679519</td>
      <td>64.0</td>
      <td>17.818986</td>
      <td>62.0</td>
      <td>13.055523</td>
      <td>68.0</td>
    </tr>
    <tr>
      <th>9</th>
      <td>AVGO</td>
      <td>166.360001</td>
      <td>68.5</td>
      <td>1202</td>
      <td>98.121200</td>
      <td>82.0</td>
      <td>29.283297</td>
      <td>56.0</td>
      <td>19.779980</td>
      <td>72.0</td>
      <td>11.456523</td>
      <td>64.0</td>
    </tr>
    <tr>
      <th>10</th>
      <td>GE</td>
      <td>171.220001</td>
      <td>50.5</td>
      <td>1168</td>
      <td>94.141132</td>
      <td>80.0</td>
      <td>40.405726</td>
      <td>76.0</td>
      <td>3.781810</td>
      <td>20.0</td>
      <td>3.977654</td>
      <td>26.0</td>
    </tr>
    <tr>
      <th>11</th>
      <td>IRM</td>
      <td>113.349998</td>
      <td>89.0</td>
      <td>1764</td>
      <td>94.007159</td>
      <td>78.0</td>
      <td>53.441985</td>
      <td>90.0</td>
      <td>44.037942</td>
      <td>100.0</td>
      <td>16.976261</td>
      <td>88.0</td>
    </tr>
    <tr>
      <th>12</th>
      <td>MPWR</td>
      <td>936.289978</td>
      <td>78.0</td>
      <td>213</td>
      <td>93.257056</td>
      <td>76.0</td>
      <td>30.281345</td>
      <td>58.0</td>
      <td>25.636169</td>
      <td>84.0</td>
      <td>18.532719</td>
      <td>94.0</td>
    </tr>
    <tr>
      <th>13</th>
      <td>AXON</td>
      <td>370.700012</td>
      <td>84.0</td>
      <td>539</td>
      <td>89.123015</td>
      <td>74.0</td>
      <td>36.976686</td>
      <td>72.0</td>
      <td>32.397595</td>
      <td>94.0</td>
      <td>19.269012</td>
      <td>96.0</td>
    </tr>
    <tr>
      <th>14</th>
      <td>DECK</td>
      <td>974.559998</td>
      <td>48.0</td>
      <td>205</td>
      <td>86.776025</td>
      <td>72.0</td>
      <td>10.685083</td>
      <td>10.0</td>
      <td>7.727847</td>
      <td>28.0</td>
      <td>15.812240</td>
      <td>82.0</td>
    </tr>
    <tr>
      <th>15</th>
      <td>CRWD</td>
      <td>271.540009</td>
      <td>29.0</td>
      <td>736</td>
      <td>86.689594</td>
      <td>70.0</td>
      <td>-12.825446</td>
      <td>4.0</td>
      <td>-20.683510</td>
      <td>4.0</td>
      <td>6.842422</td>
      <td>38.0</td>
    </tr>
    <tr>
      <th>16</th>
      <td>META</td>
      <td>528.000000</td>
      <td>52.0</td>
      <td>378</td>
      <td>84.510899</td>
      <td>68.0</td>
      <td>9.192454</td>
      <td>8.0</td>
      <td>13.470789</td>
      <td>46.0</td>
      <td>16.450893</td>
      <td>86.0</td>
    </tr>
    <tr>
      <th>17</th>
      <td>PGR</td>
      <td>241.250000</td>
      <td>63.0</td>
      <td>829</td>
      <td>84.130236</td>
      <td>66.0</td>
      <td>26.230686</td>
      <td>46.0</td>
      <td>18.793352</td>
      <td>68.0</td>
      <td>13.385343</td>
      <td>72.0</td>
    </tr>
    <tr>
      <th>18</th>
      <td>CEG</td>
      <td>194.990005</td>
      <td>59.0</td>
      <td>1025</td>
      <td>83.773422</td>
      <td>64.0</td>
      <td>46.306687</td>
      <td>84.0</td>
      <td>-11.533804</td>
      <td>12.0</td>
      <td>14.623725</td>
      <td>76.0</td>
    </tr>
    <tr>
      <th>19</th>
      <td>UHS</td>
      <td>233.139999</td>
      <td>77.5</td>
      <td>857</td>
      <td>80.102106</td>
      <td>62.0</td>
      <td>42.215870</td>
      <td>82.0</td>
      <td>31.923533</td>
      <td>92.0</td>
      <td>13.732374</td>
      <td>74.0</td>
    </tr>
    <tr>
      <th>20</th>
      <td>NTAP</td>
      <td>133.119995</td>
      <td>61.0</td>
      <td>1502</td>
      <td>80.019912</td>
      <td>60.0</td>
      <td>53.643131</td>
      <td>92.0</td>
      <td>17.198830</td>
      <td>56.0</td>
      <td>6.021024</td>
      <td>36.0</td>
    </tr>
    <tr>
      <th>21</th>
      <td>GRMN</td>
      <td>179.759995</td>
      <td>46.5</td>
      <td>1112</td>
      <td>79.644866</td>
      <td>58.0</td>
      <td>33.940099</td>
      <td>68.0</td>
      <td>10.986972</td>
      <td>36.0</td>
      <td>3.667821</td>
      <td>24.0</td>
    </tr>
    <tr>
      <th>22</th>
      <td>TT</td>
      <td>352.910004</td>
      <td>44.0</td>
      <td>566</td>
      <td>79.280455</td>
      <td>56.0</td>
      <td>25.929444</td>
      <td>44.0</td>
      <td>6.284790</td>
      <td>22.0</td>
      <td>9.524549</td>
      <td>54.0</td>
    </tr>
    <tr>
      <th>23</th>
      <td>ALL</td>
      <td>180.509995</td>
      <td>39.0</td>
      <td>1107</td>
      <td>75.927363</td>
      <td>54.0</td>
      <td>14.733369</td>
      <td>16.0</td>
      <td>10.684294</td>
      <td>34.0</td>
      <td>9.135430</td>
      <td>52.0</td>
    </tr>
    <tr>
      <th>24</th>
      <td>TRGP</td>
      <td>144.130005</td>
      <td>70.5</td>
      <td>1387</td>
      <td>75.525569</td>
      <td>52.0</td>
      <td>50.341765</td>
      <td>88.0</td>
      <td>27.308202</td>
      <td>86.0</td>
      <td>9.819963</td>
      <td>56.0</td>
    </tr>
    <tr>
      <th>25</th>
      <td>LLY</td>
      <td>952.739990</td>
      <td>59.5</td>
      <td>209</td>
      <td>75.025842</td>
      <td>50.0</td>
      <td>24.190751</td>
      <td>38.0</td>
      <td>18.012396</td>
      <td>66.0</td>
      <td>16.181543</td>
      <td>84.0</td>
    </tr>
    <tr>
      <th>26</th>
      <td>PHM</td>
      <td>135.130005</td>
      <td>56.0</td>
      <td>1480</td>
      <td>73.722489</td>
      <td>48.0</td>
      <td>28.242824</td>
      <td>54.0</td>
      <td>20.069757</td>
      <td>74.0</td>
      <td>8.104004</td>
      <td>48.0</td>
    </tr>
    <tr>
      <th>27</th>
      <td>KLAC</td>
      <td>817.840027</td>
      <td>36.5</td>
      <td>244</td>
      <td>73.193321</td>
      <td>46.0</td>
      <td>22.754029</td>
      <td>32.0</td>
      <td>7.088813</td>
      <td>26.0</td>
      <td>7.410302</td>
      <td>42.0</td>
    </tr>
    <tr>
      <th>28</th>
      <td>FITB</td>
      <td>42.119999</td>
      <td>41.0</td>
      <td>4748</td>
      <td>71.092699</td>
      <td>44.0</td>
      <td>28.139944</td>
      <td>52.0</td>
      <td>15.522182</td>
      <td>50.0</td>
      <td>0.693275</td>
      <td>18.0</td>
    </tr>
    <tr>
      <th>29</th>
      <td>ISRG</td>
      <td>486.549988</td>
      <td>55.5</td>
      <td>411</td>
      <td>70.336775</td>
      <td>42.0</td>
      <td>24.830028</td>
      <td>40.0</td>
      <td>22.129062</td>
      <td>78.0</td>
      <td>11.404955</td>
      <td>62.0</td>
    </tr>
    <tr>
      <th>30</th>
      <td>COST</td>
      <td>879.210022</td>
      <td>35.0</td>
      <td>227</td>
      <td>70.189136</td>
      <td>40.0</td>
      <td>19.506574</td>
      <td>24.0</td>
      <td>10.563536</td>
      <td>32.0</td>
      <td>7.906329</td>
      <td>44.0</td>
    </tr>
    <tr>
      <th>31</th>
      <td>URI</td>
      <td>745.030029</td>
      <td>26.0</td>
      <td>268</td>
      <td>68.928495</td>
      <td>38.0</td>
      <td>13.721157</td>
      <td>14.0</td>
      <td>11.996825</td>
      <td>42.0</td>
      <td>-0.994189</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th>32</th>
      <td>NFLX</td>
      <td>686.729980</td>
      <td>34.0</td>
      <td>291</td>
      <td>68.758753</td>
      <td>36.0</td>
      <td>17.679413</td>
      <td>20.0</td>
      <td>8.032470</td>
      <td>30.0</td>
      <td>8.301653</td>
      <td>50.0</td>
    </tr>
    <tr>
      <th>33</th>
      <td>KEY</td>
      <td>17.070000</td>
      <td>43.0</td>
      <td>11716</td>
      <td>67.576445</td>
      <td>34.0</td>
      <td>23.198015</td>
      <td>34.0</td>
      <td>19.747454</td>
      <td>70.0</td>
      <td>5.827654</td>
      <td>34.0</td>
    </tr>
    <tr>
      <th>34</th>
      <td>CFG</td>
      <td>42.889999</td>
      <td>50.5</td>
      <td>4663</td>
      <td>66.887066</td>
      <td>32.0</td>
      <td>40.730115</td>
      <td>78.0</td>
      <td>23.323128</td>
      <td>80.0</td>
      <td>0.164384</td>
      <td>12.0</td>
    </tr>
    <tr>
      <th>35</th>
      <td>STX</td>
      <td>104.410004</td>
      <td>29.5</td>
      <td>1915</td>
      <td>66.409291</td>
      <td>30.0</td>
      <td>20.437535</td>
      <td>30.0</td>
      <td>12.458973</td>
      <td>44.0</td>
      <td>0.432863</td>
      <td>14.0</td>
    </tr>
    <tr>
      <th>36</th>
      <td>UBER</td>
      <td>74.300003</td>
      <td>38.5</td>
      <td>2691</td>
      <td>66.293649</td>
      <td>28.0</td>
      <td>-4.987205</td>
      <td>6.0</td>
      <td>16.823907</td>
      <td>54.0</td>
      <td>13.021000</td>
      <td>66.0</td>
    </tr>
    <tr>
      <th>37</th>
      <td>DHI</td>
      <td>191.789993</td>
      <td>60.5</td>
      <td>1042</td>
      <td>65.692032</td>
      <td>26.0</td>
      <td>31.769766</td>
      <td>60.0</td>
      <td>34.512180</td>
      <td>96.0</td>
      <td>11.239322</td>
      <td>60.0</td>
    </tr>
    <tr>
      <th>38</th>
      <td>MMM</td>
      <td>130.550003</td>
      <td>78.0</td>
      <td>1531</td>
      <td>64.821166</td>
      <td>24.0</td>
      <td>69.823064</td>
      <td>98.0</td>
      <td>31.192845</td>
      <td>90.0</td>
      <td>26.269469</td>
      <td>100.0</td>
    </tr>
    <tr>
      <th>39</th>
      <td>RCL</td>
      <td>163.080002</td>
      <td>41.5</td>
      <td>1226</td>
      <td>64.644116</td>
      <td>22.0</td>
      <td>33.770812</td>
      <td>66.0</td>
      <td>11.461967</td>
      <td>38.0</td>
      <td>7.275357</td>
      <td>40.0</td>
    </tr>
    <tr>
      <th>40</th>
      <td>GS</td>
      <td>509.420013</td>
      <td>36.0</td>
      <td>392</td>
      <td>63.992997</td>
      <td>20.0</td>
      <td>31.986890</td>
      <td>62.0</td>
      <td>11.863550</td>
      <td>40.0</td>
      <td>3.601721</td>
      <td>22.0</td>
    </tr>
    <tr>
      <th>41</th>
      <td>MHK</td>
      <td>157.750000</td>
      <td>70.0</td>
      <td>1267</td>
      <td>63.641076</td>
      <td>18.0</td>
      <td>37.245516</td>
      <td>74.0</td>
      <td>36.273322</td>
      <td>98.0</td>
      <td>17.286245</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th>42</th>
      <td>QCOM</td>
      <td>173.500000</td>
      <td>11.0</td>
      <td>1152</td>
      <td>63.539937</td>
      <td>16.0</td>
      <td>13.030732</td>
      <td>12.0</td>
      <td>-13.654324</td>
      <td>8.0</td>
      <td>-1.077598</td>
      <td>8.0</td>
    </tr>
    <tr>
      <th>43</th>
      <td>CTAS</td>
      <td>788.500000</td>
      <td>33.5</td>
      <td>253</td>
      <td>63.032138</td>
      <td>14.0</td>
      <td>25.045616</td>
      <td>42.0</td>
      <td>13.510866</td>
      <td>48.0</td>
      <td>4.673190</td>
      <td>30.0</td>
    </tr>
    <tr>
      <th>44</th>
      <td>LDOS</td>
      <td>154.899994</td>
      <td>21.5</td>
      <td>1291</td>
      <td>62.747737</td>
      <td>12.0</td>
      <td>23.569417</td>
      <td>36.0</td>
      <td>3.698614</td>
      <td>18.0</td>
      <td>1.894481</td>
      <td>20.0</td>
    </tr>
    <tr>
      <th>45</th>
      <td>MU</td>
      <td>102.849998</td>
      <td>11.5</td>
      <td>1944</td>
      <td>62.269457</td>
      <td>10.0</td>
      <td>19.813161</td>
      <td>26.0</td>
      <td>-18.476315</td>
      <td>6.0</td>
      <td>-4.281060</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>46</th>
      <td>LEN</td>
      <td>185.020004</td>
      <td>39.5</td>
      <td>1080</td>
      <td>61.796624</td>
      <td>8.0</td>
      <td>20.120223</td>
      <td>28.0</td>
      <td>20.157861</td>
      <td>76.0</td>
      <td>8.021956</td>
      <td>46.0</td>
    </tr>
    <tr>
      <th>47</th>
      <td>AXP</td>
      <td>251.300003</td>
      <td>20.0</td>
      <td>795</td>
      <td>61.409735</td>
      <td>6.0</td>
      <td>17.836248</td>
      <td>22.0</td>
      <td>7.045149</td>
      <td>24.0</td>
      <td>4.629865</td>
      <td>28.0</td>
    </tr>
    <tr>
      <th>48</th>
      <td>WDC</td>
      <td>64.349998</td>
      <td>9.5</td>
      <td>3108</td>
      <td>61.399549</td>
      <td>4.0</td>
      <td>14.787722</td>
      <td>18.0</td>
      <td>-13.228162</td>
      <td>10.0</td>
      <td>-3.218528</td>
      <td>6.0</td>
    </tr>
    <tr>
      <th>49</th>
      <td>TFC</td>
      <td>43.840000</td>
      <td>29.5</td>
      <td>4562</td>
      <td>60.900443</td>
      <td>2.0</td>
      <td>27.646097</td>
      <td>48.0</td>
      <td>16.079126</td>
      <td>52.0</td>
      <td>0.608929</td>
      <td>16.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
import xlsxwriter

writer = pd.ExcelWriter('momentum_strategy.xlsx')
hqm_df.to_excel(writer, sheet_name='Momentum Strategy', index=False)
writer.close()
```


```python
hqm_df.head(5)
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Ticker</th>
      <th>Stock Price</th>
      <th>HQM Score</th>
      <th>No of shares to buy</th>
      <th>One Year Price Return</th>
      <th>One Year Return Percentile</th>
      <th>Six Month Price Return</th>
      <th>Six Month Return Percentile</th>
      <th>Three Month Price Return</th>
      <th>Three Month Return Percentile</th>
      <th>One Month Price Return</th>
      <th>One Month Return Percentile</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>VST</td>
      <td>85.769997</td>
      <td>78.0</td>
      <td>2331</td>
      <td>190.958329</td>
      <td>100.0</td>
      <td>77.478408</td>
      <td>100.0</td>
      <td>-10.545029</td>
      <td>14.0</td>
      <td>21.867008</td>
      <td>98.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>NVDA</td>
      <td>129.369995</td>
      <td>89.0</td>
      <td>1545</td>
      <td>174.386125</td>
      <td>98.0</td>
      <td>64.160889</td>
      <td>96.0</td>
      <td>24.645337</td>
      <td>82.0</td>
      <td>15.220873</td>
      <td>80.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>SMCI</td>
      <td>613.239990</td>
      <td>25.5</td>
      <td>326</td>
      <td>133.615234</td>
      <td>96.0</td>
      <td>-28.693854</td>
      <td>2.0</td>
      <td>-27.631053</td>
      <td>2.0</td>
      <td>-11.841405</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>NRG</td>
      <td>83.500000</td>
      <td>70.5</td>
      <td>2395</td>
      <td>131.977629</td>
      <td>94.0</td>
      <td>63.766170</td>
      <td>94.0</td>
      <td>3.533962</td>
      <td>16.0</td>
      <td>14.866184</td>
      <td>78.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>GDDY</td>
      <td>162.449997</td>
      <td>75.0</td>
      <td>1231</td>
      <td>131.509194</td>
      <td>92.0</td>
      <td>41.371501</td>
      <td>80.0</td>
      <td>17.241628</td>
      <td>58.0</td>
      <td>13.371488</td>
      <td>70.0</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
