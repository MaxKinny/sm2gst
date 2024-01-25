![image](https://github.com/MaxKinny/tsg2ms/assets/33459391/a3c37014-0ced-4ff7-a07c-f1a0b486b7ae)

# Table Structure Graph (TSG) to Merging Set (MS)
<img src="https://github.com/MaxKinny/tsg2ms/assets/33459391/48e9e3fa-6960-486b-94a1-dce25773e880" width="800">

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


def get_merging_set(row_adj_matrix, col_adj_matrix, flags):
    # request results
    url = f"http://<is opening soon...>.gz.apigw.tencentcs.com/release/tsg2ms"
    data = {"matrix1": row_adj_matrix, "matrix2": col_adj_matrix, "flags": flags}
    headers = {
        "Content-Type": "application/json",
        "Accept": "*/*",
        "Cache-Control": "no-cache",
        "Host": "<is opening soon...>.gz.apigw.tencentcs.com",
        "Accept-Encoding": "gzip, deflate, br",
        "Connection": "keep-alive",
        "User-Agent": "apifox/1.0.0 (https://www.apifox.cn)",
    }
    r = requests.post(url, headers=headers, data=json.dumps(data))
    json_data = r.json()
    return json_data.get("result")


if __name__ == '__main__':
    ##################### Inputs #############################
    row_adj_matrix = [[0, 1, -9999, -9999],
                      [-9999, 0, -9999, -9999],
                      [-9999, -9999, 0, 1],
                      [-9999, -9999, -9999, 0]]

    col_adj_matrix = [[0, -9999, 1, -9999],
                      [-9999, 0, -9999, 1],
                      [-9999, -9999, 0, -9999],
                      [-9999, -9999, -9999, 0]]

    flags = {'gt_or_prediction': 'gt',
             'isFAS': False,
             'isDeleteConflicts': False,
             'isDetectVacancy': True,
             'isMIP': False,
             'isComputeSL': True}
    ##########################################################

    api_return = get_merging_set(row_adj_matrix, col_adj_matrix, flags)

    # show results
    if api_return["status"] == "failure":
        print("Invalid Table or Graph!", api_return.get("message"))
    elif api_return["status"] == "success":
        print(api_return)
```

# An APP for testing our API
<img src="https://github.com/MaxKinny/tsg2ms/assets/33459391/d90045c5-09c7-4e0d-8168-51f5a1b6a593" width="400">

#### Description:
Draw your table on paper and annotate its TSG using our tool. After that, click the "Merging Set" button, this tool will compute the merging set of your table!

#### Download Links:
**Version 2 (Recommended)**
https://doi.org/10.6084/m9.figshare.24633588.v3

**Version 1 (Deprecated)**
[Google Drive](https://drive.google.com/file/d/1-NRQYTQiAaJEibMXyu_ogzInTh4taogB/view?usp=sharing), [百度网盘](https://pan.baidu.com/s/1xrgwRoFnWUdLB8c11fPQBA?pwd=1234)

#### The demonstration video (with voice):
https://github.com/MaxKinny/app_TableStructureGraph2MergingSet/assets/33459391/677769c7-4028-4d09-a9f9-a6b58c303bf3

# Report Bugs
If you have tables with inconsistent merging sets from the tool, there may be implementation bugs in our API program. Please raise an issue and upload images and JSON data for your examples. Thanks a lot!

<!-- 
# Authorship
```
1. Fan Yang, maxgundam@hotmail.com, https://scholar.google.com/citations?user=MZGxAVcAAAAJ&hl=zh-CN
2. Jiancong Ye, jcye1483@outlook.com, https://scholar.google.com/citations?user=_a19A1EAAAAJ&hl=zh-CN
```

# Author Contributions
```
1. 提出总体的算法思路、提出了拓扑型、提出利用同构比较拓扑型与子图、提出了轨道法用于判别是否存在空缺、提出了轨道法的2个判别条件、提出了轨道法求取的框架(行列优先级拓扑排序+序列跳跃)、提出1阶与2阶行列优先级、提出了倒转行列标签后可重复利用已有代码求另一方向的结果；编写5%的代码。
2. 提出利用垫顶点将图的左右給pad上、提出利用轨道法找出空缺后填入占位顶点这样就能把表格填补为规整的表格、想到了轨道法判别条件1的反例、想到了如何将行列优先级融入拓扑序的算法；编写95%的代码。
```
-->
