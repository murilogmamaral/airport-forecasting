# airport-forecasting
End-to-end project for forecasting passenger flow (arrivals) at Brazilian airports  
<br>  
  
### Link for application
[academia.shinyapp.io/airport-forecasting](http://academia.shinyapps.io/airport-forecasting)  
<br>  
  
### Preview
![image](https://github.com/murilogmamaral/airport-forecasting/assets/80144654/66a19f80-742b-4e65-80e5-7a71d57603a9)  
<br>  

### Data Engineering pipeline (AWS)

> <img src="https://github.com/murilogmamaral/airport-forecasting/assets/80144654/3bfd1d9a-0de2-4ada-a187-a20b2cd15c45" width="20" height="20"> &nbsp;&nbsp;ANAC updates data monthly.  

> <img src="https://github.com/murilogmamaral/airport-forecasting/assets/80144654/98d2449a-4461-4865-9007-a596e15ef215" width="20" height="20"> &nbsp;&nbsp;ETL job searches for new CSV files available and download them.

> <img src="https://github.com/murilogmamaral/airport-forecasting/assets/80144654/57f70101-6cf1-4916-93d3-724844b1fdab" width="20" height="20"> &nbsp;&nbsp;They are stored in S3 in a landing zone.

> <img src="https://github.com/murilogmamaral/airport-forecasting/assets/80144654/2fae7c96-a38d-4c7b-a046-f84c2dd24e50" width="20" height="20"> &nbsp;&nbsp;Lambda function monitores when new data arrives in landing zone and trigger an ETL job.

> <img src="https://github.com/murilogmamaral/airport-forecasting/assets/80144654/98d2449a-4461-4865-9007-a596e15ef215" width="20" height="20"> &nbsp;&nbsp;ETL job treat new data and save results as parquet in a bronze zone.

> <img src="https://github.com/murilogmamaral/airport-forecasting/assets/80144654/86b66693-b41c-4507-b6dd-2f2389e112b2" width="20" height="20"> &nbsp;&nbsp;CloudWatch rule monitores if the previous ETL job succeeded and triggers a Glue workflow.

> <img src="https://github.com/murilogmamaral/airport-forecasting/assets/80144654/98d2449a-4461-4865-9007-a596e15ef215" width="20" height="20"> &nbsp;&nbsp;Glue workflow runs several ETL jobs for different kinds of aggregation and store results in a gold zone partitioned by airports.
<br>  
  
### Data Science & Development  

> Exploratory Data Analysis  

> Data preparation: feature engineering  

> Traning a XGBoost regressor  

> Dashboard development with Shiny  

> Deployment with _shinyapps.io_  
<br>
  
Tools:  
VS Code, Jupyter Notebook, Python  

  
Libraries:  
pandas, numpy, xgboost, matplotlib, plotly, shiny  

  


