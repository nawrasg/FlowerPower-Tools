<h1>CSV-Dump</h1>

<h2>Api-Cloud</h2>
The module `ApiCloud` is a class which communicate whit the web service.
You have to inquire your apiKey and apiSecret and call the methode `.login` before all.
```python
from ApiCloud import ApiCloud

api = ApiCloud("apiKey", "apiSecret")
api.login("username", "password")
```

<h2>Dump-Csv</h2>
Now you can use the `CSVDump` module. The function `dumpAllFlowerPower` will get all your `sensor_serial` from cloud, and for each sensor, create 1 .csv where there will be all samples.
This function need the instance of ApiCloud and a date range (`since` -> `until`)
```python
from CSVDump import *

dumpAllFlowerPower(api, since, until)
```
The date format is: `day-month-year hour:minute:seconde`   
The `since` and `until` parameters are optional:By default:
  * `until`: set to today
  * `since`: is set 1 week befor the `until` date

<h2>Example: main.py</h2>
```python
from ApiCloud import ApiCloud
from CSVDump import *

api = ApiCloud("parrottest.fpwebservice@gmail.com", "cvSjfnONllkHLymF2gEUL73PPXJiMMcVCd1VtZaIXHSGyhaT")
api.login("parrottest.fpwebservice@gmail.com", "Parrot2015FP")

### date: 30-Mar-2015 23:59:59
dumpAllFlowerPower(api)                                                             #true
dumpAllFlowerPower(api, "10-Oct-2015 11:30:00", "29-Oct-2015 11:30:00")             #true
dumpAllFlowerPower(api, since="10-Oct-2015 11:30:00", until="29-Oct-2015 11:30:00") #true

dumpAllFlowerPower(api, since="25-Jun-2015 11:30:00")    #true
dumpAllFlowerPower(api, until="12-Oct-2015 11:30:00")    #true

dumpAllFlowerPower(api, since="29-Jun-2096 11:30:00")   #false (since > until)


```

<h2>Just run it</h2>
Edit `main.py` file and:
```bash
$ python main.py
```
