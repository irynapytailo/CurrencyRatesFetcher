# CurrencyRatesFetcher
A windows service that fetches currency rates at specified intervals
Installation and uninstallation:

Before install, ensure that the following files are present in the folder:
1. CurrencyRatesFetcher.exe
2. currenciesDEV.txt
3. cacert.pem (you should create one and place it in the same folder where exe is);

1. Run the following command in cmd, having changed binPath to the path where exe is. You must have admin rights.
sc create RatesFetcher binPath= "C:\Users\iryna\source\repos\CurrencyRatesFetcher\x64\Debug\CurrencyRatesFetcher.exe  -c usd -c aud -c cad -f 1 -s csv -r y" type= own start= auto DisplayName= "Currency Rates Fetching Service"

2. Run the following command in cmd. You must have admin rights.

sc start RatesFetcher


Parameters to be set: 
-c - currency [usd, aud, cad] and so on
-s - format of output file [xml, csv, json]
-f - frequency of fetching currency rates, in days [1, 2, 3, 4] and so on
-r - if output file is updated or written anew [y, n]


Currency rates are fetched at a specified interval at 9:00 am local time.
Dependencies and any external libraries used

1. libcurl with openSSL - for http requests;
2. nlohmann/json - for reading and writing json
3. tinyxml2 - for reading and writing xml


Logging: 

Program queries are logged in log.txt.
