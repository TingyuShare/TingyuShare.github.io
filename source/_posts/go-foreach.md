---
title: go 从一个循环开卷
date: 2022-06-15 14:00:16
tags: language
---
能用 python 就不用 go, 然而大千世界啥都得懂点。所以先搞个循环卷一卷。

## first step of first way
```go
package main

import "fmt"

func main() {
	var keepGoing = true
	answer := ""
	for keepGoing {
		fmt.Println("你不quit我就卷: ")
		fmt.Scan(&answer)
		if answer == "quit" {
			keepGoing = false
		}
	}
	fmt.Println("program exit")

}
```

## go 的三个循环层次
```go
    // 自然卷
    for i := 0; i < 10; i++ {
        
    } 
    // 卷不卷
    for <condition> {
    
    }
    // 踏步卷 
    kvs := map[string]string{"a": "apple", "b": "banana"}
    for k, v := range kvs {
        fmt.Printf("%s -> %s\n", k, v)
    }
```

## go 福利
[go by example](https://gobyexample.com/)