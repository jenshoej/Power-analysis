# Tools for fetching and visualizing Danish power system data from Energinet's API.

## Functions

### `load_power_data(start_date, end_date)`

Fetches power generation and consumption data from Energinet's API.

**Parameters:**
- `start_date`: Start date in format `'YYYY-MM-DD'`
- `end_date`: End date in format `'YYYY-MM-DD'`

**Returns:**
A pandas DataFrame with hourly data for different generation types and total load.

**Example:**

```python
df = load_power_data('2024-01-01', '2024-02-01')
```

### plot_power_generation(df, columns_to_plot, scale_factors=None, start=None, end=None, title="Danmarks elsystem", plot_load=True)

Creates a stacked area plot of power generation with optional load curve.

Parameters:
- df: DataFrame from fetch_danish_energy_data
- columns_to_plot: List of generation types to include in plot
- scale_factors: Optional dictionary to scale specific generation types, e.g. {'SolarPower': 1.5}
- start: Start date for plot in format 'YYYY-MM-DD'
- end: End date for plot in format 'YYYY-MM-DD'
- title: Plot title
- plot_load: Boolean to include load curve (default True)"

Example:
```python 
# Plot one week of data
columns = ['SolarPower', 'OnshoreWindPower', 'OffshoreWindPower']
plot_power_generation(df,
                      columns_to_plot=columns,
                      start='2024-01-01',
                      end='2024-01-07',
                      plot_load=True)
```

## Available Data Columns

Generation types that can be plotted:
- SolarPower (Sol)
- OnshoreWindPower (Landvind)
- OffshoreWindPower (Havvind)
- FossilGas (Gas)
- FossilHardCoal (Kul)
- Biomass (Biomasse)
- FossilOil (Olie)

Load can be plotted with TotalLoad

Transmission data is available in the dataframe, but cannot yet be plotted with the here routine (will be available in the future).
The available dataseries are

- ExchangeGreatBritain (England)
- ExchangeNordicCountries (Sverige og Norge)
- ExchangeContinent (Tyskland og Holland)
- ExchangeGreatBelt (Storebælt)


Danish translations are shown in parentheses and will appear in plot legends.

## Requirements
- pandas
- numpy
- matplotlib
- requests
