---
title: React 实现带回调函数的useState
date: 2020-04-24 23:20:53
tags: React
categories: React自定义hooks
---

## 1 useCallbackState 定义
```javaScript
import React, { useEffect, useState, useRef } from "react";

const useCallbackState = (od) => {
    const cbRef = useRef();
    const [data, setData] = useState(od);

    useEffect(() => {
        cbRef.current && cbRef.current(data);
    }, [data]);

    return [data, function (d, callback) {
        cbRef.current = callback;
        setData(d);
    }];
}
export default useCallbackState

```
## 2 useCallbackState 使用
```javaScript
import useCallbackState from "./useCallbackState";
const App = () => {
    const [data, setData] = useCallbackState(1);

    const handleClick = () => {
        setData(data + 1, function (data) {
            console.log("回调", data);
        })
    }
    return (
        <div>
            <button onClick={handleClick}>+1</button>
        </div>
    )
}
export default App
```
