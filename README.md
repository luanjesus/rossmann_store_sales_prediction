# Rossmann's stores sales forecast
![Rossmann logo](https://github.com/luanjesus/rossmann_store_sales_prediction/blob/main/img/rossmann-mein-drogeriemarkt-logo-vector.png)

**Dirk Rossmann GmbH** is one of the largest drug store chains in Europe with around 56,200 employees and more than 4000 stores. 

The company was founded in 1972 by Dirk Rossmann with its headquarters in Burgwedel near Hanover in Germany. In 2019 Rossmann had more than €10 billion turnover in Germany, Poland, Hungary, the Czech Republic, Turkey, Albania, Kosovo and Spain.

Rossmann has a wide product range that includes up to 21,700 items and can vary depending on store size and location. In addition to drugstore products focusing on skin, hair, body, baby and health, Rossmann also offers promotional items ("World of Ideas"), pet food, photo service and a wide variety of natural foods, wines and others. [Rossmann (company) ](https://en.wikipedia.org/wiki/Rossmann_%28company%29#cite_note-1)

# 1. Business Problem

In order to attract more customers and further increase the company's profits, Rossmann's CEO is thinking about renovating its stores with the inclusion of more technologies that facilitate and speed up the purchase process for its customers.

For the renovation of each store to be carried out, the CEO needs to know how many resources he will have available in the next six weeks.  Therefore, Rossmann's data science team was asked to forecast future sales for the requested period.

_**Main objective: Forecast the sales value of each store for the next six weeks.**_

# 2. Data
## **2. 1 Data Extraction**

Project data was extracted from Kaggle's "[Rossmann Store Sales](https://www.kaggle.com/competitions/rossmann-store-sales/data)" competition.

## **2. 2 Data Description**
The data refer to the historical sales periods of 1,115 Rossmann stores. The task will be to predict the "Sales" column.
### Files
-   **train.csv** - historical data including Sales
- **store.csv** - supplemental information about the stores

### Data fields

Most of the fields are self-explanatory. The following are descriptions for those that aren't.

-   **Id** - an Id that represents a (Store, Date) duple within the test set
-   **Store** - a unique Id for each store
-   **Sales** - the turnover for any given day (this is what you are predicting)
-   **Customers** - the number of customers on a given day
-   **Open** - an indicator for whether the store was open: 0 = closed, 1 = open
-   **StateHoliday** - indicates a state holiday. Normally all stores, with few exceptions, are closed on state holidays. Note that all schools are closed on public holidays and weekends. a = public holiday, b = Easter holiday, c = Christmas, 0 = None
-   **SchoolHoliday** - indicates if the (Store, Date) was affected by the closure of public schools
-   **StoreType** - differentiates between 4 different store models: a, b, c, d
-   **Assortment** - describes an assortment level: a = basic, b = extra, c = extended
-   **CompetitionDistance** - distance in meters to the nearest competitor store
-   **CompetitionOpenSince[Month/Year]** - gives the approximate year and month of the time the nearest competitor was opened
-   **Promo** - indicates whether a store is running a promo on that day
-   **Promo2** - Promo2 is a continuing and consecutive promotion for some stores: 0 = store is not participating, 1 = store is participating
-   **Promo2Since[Year/Week]** - describes the year and calendar week when the store started participating in Promo2
-   **PromoInterval** - describes the consecutive intervals Promo2 is started, naming the months the promotion is started anew. E.g. "Feb,May,Aug,Nov" means each round starts in February, May, August, November of any given year for that store

## 3 Assumptions

 1. **Variable Open:** There are some stores in the dataset that were temporarily closed for refurbishment. So, rows with these stores (open column equal 1) have been removed from the dataset.
 2. **Variable CompetitionDistance:** This column has 2642 NAN rows, to correct these cases I assumed the stores would be too far away from the furthest store in the dataset (75800). For this, I put the value of 227400 that represents three times the value of the farthest store.

