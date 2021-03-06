# Data Dock Package

#### Introduction
This framework is mainly used for data pair amount in big data.

#### Installation
```ini
pip install DataDocking -i https://pypi.python.org/simple -U
```

#### Uage
1.DataLoadStatic
- This is used to load static data variables, data variables cannot be modified
```python
from DataDocking import DataLoadStatic
class DataLoad(DataLoadStatic):
    temp = 20
    press = 30
    
dl = DataLoad()
# dl.temp.value --> 20
# dl.all_fields --> {'temp': 20, 'press': 30}
```

2.DataParse
- Data analysis process, follow common framework usage：set_up() ->  process() -> teardown()
    - set_up: Data preprocessing
    - process: data processing
    - teardown: Data finishing process
```python
from DataDocking import DataParse
class TempDataParse(DataParse):
    def setup(self):
        pass

    def process(self):
        pass

    def teardown(self):
        pass
```

3.DataSave
- Data storage, incoming ```sql_url_con```, such as ```postgresql+psycopg2://root:123@127.0.0.1:5432/demo```
```python
from DataDocking import DataSave
class TempDataSave(DataSave):
    pass

if __name__ == '__main__':
    sql_url_con = 'postgresql+psycopg2://root:123@127.0.0.1:5432/demo'
    tds = TempDataSave()
    db = tds.db(sql_url_con)
    db.query('your sql')
    tds.save('your save sql')
    
    sql_url_cons = [sql_url_con for _ in range(3)]
    dbs = tds.dbs(sql_url_cons) 
    index_db = dbs[0]
    index_db.query('your sql')
    index_db.save('your save sql')
    
```

#### Connection
- author github: https://github.com/AlitaIcon/DataDocking

- more information: 1906321518@qq.com

