# airport-forecasting
End-to-end project for forecasting passenger flow (arrivals) at Brazilian airports  
<br>  
  
### Link for application
[ACADEMIA.SHINYAPP.IO/AIRPORT-FORECASTING](http://academia.shinyapps.io/airport-forecasting)  
<br>  
  
### Preview
![image](https://github.com/murilogmamaral/airport-forecasting/assets/80144654/66a19f80-742b-4e65-80e5-7a71d57603a9)  
<br>  
  
### Data lifecycle

ANAC updates data monthly.

ETL job searches for new CSV files available and download them.

They are stored in S3 in a landing zone.

Lambda function monitores when new data arrives in landing zone and trigger an ETL job.

ETL job treat new data and save results as parquet in a bronze zone.

CloudWatch rule monitores if the previous ETL job succeeded and triggers a Glue workflow.

Glue workflow runs several ETL jobs for different kinds of aggregation and store results in a gold zone.
