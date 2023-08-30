![image](https://github.com/MaxKinny/app_TableStructureGraph2MergingSet/assets/33459391/7248e833-5388-4065-9623-74a4cd72ac69)

# Table Structure Graph (TSG) to Merging Set (MS)
<img src="https://github.com/MaxKinny/tsg2ms/assets/33459391/31449583-0684-43cf-91b7-fc0a7794eb1e" width="800">

# The definition of table structure
### Merging Set (MS):

# The expression of table structure
### Description:
Directed Acyclic Graph (DAG) with 2 kinds of edge labels ("row" and "column"), which is termed as Table Structure Graph (TSG). A vertex refers to a cell in a table, and a row/column edge indicates a horizontal/vertical intersection.

### Diagram:
<img src="https://github.com/MaxKinny/tsg2ms/assets/33459391/118f8b62-c3f5-4ebf-867a-f50fdde2e81b" width="800">

# Web API
```python
import requests
import json

row_adj_matrix = [[...], ...]
col_adj_matrix = [[...], ...]

# request results
url = f"http://<will opening soon...>.gz.apigw.tencentcs.com/release/tsg2ms"
data = {"data1": row_matrix, "data2": col_matrix}
headers = {
  "Content-Type": "application/json",
  "Accept": "*/*",
  "Cache-Control": "no-cache",
  "Host": "<will opening soon...>.gz.apigw.tencentcs.com",
  "Accept-Encoding": "gzip, deflate, br",
  "Connection": "keep-alive",
  "User-Agent": "apifox/1.0.0 (https://www.apifox.cn)",
}
r = requests.post(url, headers=headers, data=json.dumps(data))
json_data = r.json()
if json_data.get("result") is not None:
  json_data = json_data["result"]

# show results
if json_data["status"] == "failure":
  print("Invalid Table or Graph!", json_data.get("message"))
elif json_data["status"] == "success":
  print(json_data)
```

# An APP for testing our API
<img src="https://github.com/MaxKinny/tsg2ms/assets/33459391/ab94549c-6741-4c55-be03-7df4a8b4da7a" width="400">

#### Description:
Draw your table on paper and annotate its TSG using our tool. After that, click the "Merging Set" button, this tool will compute the merging set of your table!

#### Download Links:
[Google Drive](https://drive.google.com/file/d/1-NRQYTQiAaJEibMXyu_ogzInTh4taogB/view?usp=sharing), [百度网盘](https://pan.baidu.com/s/1xrgwRoFnWUdLB8c11fPQBA?pwd=1234)

#### The demonstration video (with voice):
https://github.com/MaxKinny/app_TableStructureGraph2MergingSet/assets/33459391/677769c7-4028-4d09-a9f9-a6b58c303bf3


# Report Bugs
If you have tables with inconsistent merging sets from the tool, there may be implementation bugs in our API program. Please raise an issue and upload images and JSON data for your examples. Thanks a lot!
