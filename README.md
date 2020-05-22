# pinyin

[![Build Status](https://travis-ci.com/Chain-Zhang/pinyin.svg?branch=master)](https://travis-ci.com/Chain-Zhang/pinyin)
[![codecov](https://codecov.io/gh/Chain-Zhang/pinyin/branch/master/graph/badge.svg)](https://codecov.io/gh/Chain-Zhang/pinyin)

golang实现中文汉字转拼音

> forked form [chain-zhang/pinyin](chain-zhang/pinyin "chain-zhang/pinyin"), 因为原repo mod文件有错误导致go get出错，已经提交了PR，这里暂时修改module为我的地址作为过渡， 请持续关注[chain-zhang/pinyin](chain-zhang/pinyin "chain-zhang/pinyin")

demo

```go
package main

import(
	"fmt"
	 "github.com/chain-zhang/pinyin"
)

func main()  {
    str, err := pinyin.New("我是中国人").Split("").Mode(InitialsInCapitals).Convert()
	if err != nil {
		// 错误处理
	}else{
		fmt.Println(str)
	}

	str, err = pinyin.New("我是中国人").Split(" ").Mode(pinyin.WithoutTone).Convert()
	if err != nil {
		// 错误处理
    }else{
    	fmt.Println(str)
    }

	str, err = pinyin.New("我是中国人").Split("-").Mode(pinyin.Tone).Convert()
	if err != nil {
		// 错误处理
    }else{
    	fmt.Println(str)
    }

	str, err = pinyin.New("我是中国人").Convert()
	if err != nil {
		// 错误处理
    }else{
    	fmt.Println(str)
    }	
}
```

输出

```bash
WoShiZhongGuoRen
wo shi zhong guo ren
wǒ-shì-zhōng-guó-rén
wo shi zhong guo ren
```

Mode 介绍

* `InitialsInCapitals`: 首字母大写, 不带音调
* `WithoutTone`: 全小写,不带音调
* `Tone`: 全小写带音调

Split 介绍

split 方法是两个汉字之间的分隔符.