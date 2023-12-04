# airport-forecasting
End-to-end project for forecasting passenger flow (arrivals) at Brazilian airports  
<br>  
  
### Link for application
[ACADEMIA.SHINYAPP.IO/AIRPORT-FORECASTING](http://academia.shinyapps.io/airport-forecasting)  
<br>  
  
### Preview
![image](https://github.com/murilogmamaral/airport-forecasting/assets/80144654/66a19f80-742b-4e65-80e5-7a71d57603a9)  
<br>  

### AWS data lifecycle
<img src="https://github.com/murilogmamaral/airport-forecasting/assets/80144654/3bfd1d9a-0de2-4ada-a187-a20b2cd15c45" width="20" height="20">
ANAC updates data monthly.  
<br><br>  

<img src="https://github.com/murilogmamaral/airport-forecasting/assets/80144654/98d2449a-4461-4865-9007-a596e15ef215" width="20" height="20">
ETL job searches for new CSV files available and download them.
<br><br>  

<img src="https://github.com/murilogmamaral/airport-forecasting/assets/80144654/57f70101-6cf1-4916-93d3-724844b1fdab" width="20" height="20">
They are stored in S3 in a landing zone.
<br><br>  

<img src="https://github.com/murilogmamaral/airport-forecasting/assets/80144654/2fae7c96-a38d-4c7b-a046-f84c2dd24e50" width="20" height="20">
Lambda function monitores when new data arrives in landing zone and trigger an ETL job.
<br><br>  

<img src="https://github.com/murilogmamaral/airport-forecasting/assets/80144654/98d2449a-4461-4865-9007-a596e15ef215" width="20" height="20">
ETL job treat new data and save results as parquet in a bronze zone.
<br><br>  

CloudWatch rule monitores if the previous ETL job succeeded and triggers a Glue workflow.

Glue workflow runs several ETL jobs for different kinds of aggregation and store results in a gold zone partitioned by airports.
