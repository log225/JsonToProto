# JsonToProto
a tool make json file to java proto buffer files
## Info
You only need three files
```
protoc
cable
config.json
```
The way to start:
* open config.json
* modify the path 
* excute ```./cable```
```
[
  {
    //the input json
    "Input":"/Users/cable/workspace/work/haha/test.json",
    //outPut path
    "OutPut": "/Users/cable/workspace/work/haha",
    "PackageName": "com.tencent.log",
    "ClassName": "NormalSetting",
    "Enable": true,
    //the way to judge same class
    "SameNumber": 4,
    //the way to judge same class
    "DiffNumber": 4,
    "CamelName": false
  }
]
```
## Attention
* only support mac now.
* only generate java now.
* auto merge "seems like" struct
## example
input json 
```
{
    "one":1,
    "two":1.0,
    "three":"123",
    "four_game":123123123,
    "lala":{
        "why":"haha",
        "test":123,
        "ssv":"baidu",
        "http":"shit",
        "woca":123
    },
    "lala2":{
        "why":"haha",
        "test":123,
        "ssv":"baidu",
        "http":"shit",
        "woca":123
    },
    "lala3":{
        "why":"haha",
        "test":123,
        "ssv":"baidu",
        "http":"shit",
        "woca2":456
    },
    "papa":[
        {
            "why":"123",
            "not":false,
            "vvv":999
        }
    ]
}
```
The outPut is 
```
syntax = "proto3";
package com.tencent.log;

message lala {
	string why = 1;
	float test = 2;
	string ssv = 3;
	string http = 4;
	float woca2 = 5;
	float woca = 6;
}

message papa {
	string why = 1;
	bool not = 2;
	float vvv = 3;
}

message NormalSetting {
	lala lala2 = 1;
	lala lala3 = 2;
	repeated papa papa = 3;
	int32 one = 4;
	int32 two = 5;
	string three = 6;
	float four_game = 7;
	lala lala = 8;
}
```
And will also generate the java class. You can find it in the  repertory.
