---
title: React 实现纯前端生成并导出Excel文件
date: 2020-03-24 23:29:53
tags: React
categories: React第三方库
---

## 安装依赖
npm install js-export-excel
## 直接上代码
```jsx
import ExportJsonExcel from "js-export-excel"
import React, { useState, useEffect } from "react"
import { Table, Button  } from "antd";

const Excel = () =>{
    const [dataTable,setDataTable] = useState(null)
    const columns = [
        {
            title: "名称",
            dataIndex: "name",
        },
        {
            title: "编号",
            dataIndex: "number",
        },
        {
            title: "方案",
            dataIndex: "programme",
        }
    ]
    useEffect(()=>{
        window.fetch("http://localhost:3001/dataTable")
        .then(response=>{
            return response.json()
        })
        .then(res=>{setDataTable(res)})
    },[])
    const downloadFileToExcel = () => {
        let option = {};  //option代表的就是excel文件
        option.fileName = "demo表";  //excel文件名称
        option.datas = [
            {
                sheetData: dataTable,  //excel文件中的数据源
                sheetName: "demo",  //excel文件中sheet页名称
                sheetFilter: ["name", "number", "programme"],  //excel文件中需显示的列数据
                sheetHeader:["名称", "编号", "方案"]  //excel文件中每列的表头名称
            }
        ]
        let toExcel = new ExportJsonExcel(option);  //生成excel文件
        toExcel.saveExcel();  //下载excel文件
    }
    return (
        <div>
            <Table columns={columns} dataSource={dataTable} rowKey={(record)=>record.id}/>
            <Button type="primary" onClick={downloadFileToExcel}>生成Excel</Button>
        </div>
    )
}
export default Excel

```
