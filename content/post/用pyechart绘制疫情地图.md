+++
author = "Di Cui"
title = "用pyechart绘制疫情地图"
date = "2023-06-23"
description = "Lorem Ipsum Dolor Si Amet"
tags = [
    "Data Visualization",

]
+++

## 教材 & 课程

[pyechart](https://05x-docs.pyecharts.org/#/zh-cn/)

[数据来源](https://github.com/canghailan/Wuhan-2019-nCoV/blob/master/Data/2020-12-08.json)

[json工具](https://www.bejson.com/)



代码

````
  import json
  from pyecharts.charts import Map
  from pyecharts.options import *

  f =open("/Users/项目存储地址/covid_tracking.json","r",encoding="utf-8-sig")
  data=f.read()

  data_dict=json.loads(data)


  data_list=[]
  for state_data in data_dict:
      province_name = state_data["province"]
      confirmed = state_data["confirmed"]
      data_list.append([province_name,confirmed])

  map =Map()
  map.add("",data_list,"china")\
      .set_series_opts(label_opts=LabelOpts(is_show=False),showLegendSymbol=False) #是否显示地理信息标记，取消红点，取消文字


  map.set_global_opts(
      title_opts=TitleOpts(title="2020-12-08全国疫情地图",pos_left="35%"),
      visualmap_opts=VisualMapOpts(
          is_show=True,
          is_piecewise=True,


          pieces=[
          {"min": 0, "max": 999, "label": "0-999人", "color": "#FFE4B5"},
            {"min":500,"max":4999,"label":"500-4999人","color":"#CD5C5C"},
            {"min":5000,"max":9999,"label":"5000-9999人","color":"＃DC143C"},
            {"min": 10000, "max": 150000, "label": ">=10000", "color": "#8B0000"},]

      ),

  )

  map.render("疫情地图.html")

````


效果：[!img]()

<img src="https://github.com/cuidi1996/cuidi1996.github.io/blob/d54f187b018b18d35e15321a12817e032ecc9490/content/images/2020-12-08%E7%96%AB%E6%83%85%E5%9C%B0%E5%9B%BE.jpg" style="width:500px" />

实现网址： http://localhost:63342/pythonProject/%E7%96%AB%E6%83%85%E5%9C%B0%E5%9B%BE.html?_ijt=s2cmuimuvt4oc0hh7s4rdfsp0i&_ij_reload=RELOAD_ON_SAVE




{{< css.inline >}}

<style>
.canon { background: white; width: 100%; height: auto; }
</style>

{{< /css.inline >}}


