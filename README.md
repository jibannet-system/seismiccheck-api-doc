### API public

**API_ROOT:** https://api.jibannet.dev/digital-seismic-check/

## 関連する共通APIのリスト
###### 1. [1. csvデータファイルをアップロード](#1-upload-file-csv-data)
###### 2. [新規デジタル耐震チェック書を追加](#2-th%C3%AAm-m%E1%BB%9Bi-seismic)
###### 3. [idによりデジタル耐震チェック書情報を取得](#3-l%E1%BA%A5y-th%C3%B4ng-tin-seismic-theo-id)
###### 4. [デジタル耐震チェック書リストを取得](#4-l%E1%BA%A5y-danh-s%C3%A1ch-seismic)
###### 5. [access tokenを取得](#5-l%E1%BA%A5y-access-token)
***********************

## 1. csvデータファイルをアップロード
* **URL:** [{API_ROOT}/uploadcsv](#)
* **Method:** POST
* **Content Type:** text/plain
* **Reponse Type:** text/plain

### パラメーター:
 -  **my_file[]**.の"csv"ファイルで2ファイルアップロードに転送 

### 戻り値:
 - file_nameのアップロードが成功した後 
 ```
	 {
		"message": "Upload file success!",
		"status": "success",
		"data": [
			"dataTest.csv"
		],
		"path": "20200526163846",
		"code": 1
	}
 ```
 - エラーの場合、通知と500のエラーステータスを返します。
 
 ## 2. 新規デジタル耐震チェック書を追加
* **URL:** [{API_ROOT}/seismic](#)
* **Method:** POST
* **Content Type:** application/json
* **Reponse Type:** text/json

### パラメーター:
```
	{
        "no": "A123",
        "name": "name",
        "address": "address",
        "report_date": "2020-05-26",
        "area_floor_1": "1.0",
        "area_floor_2": "1.0",
        "area_floor_3": "1.0",
        "area_attic": "1.0",
        "area_ph": "1.0",
        "area_balcony_floor_2": "1.0",
        "area_balcony_floor_3": "1.0",
        "area_balcony_floor_top": "1.0",
        "height_division_1": "1.0",
        "height_floor_1": "1.0",
        "height_floor_2": "1.0",
        "height_floor_3": "1.0",
        "height_max": "1.0",
        
        "type_construction": "1",
        "method": "1",
        "type_fireproof": "1",
        "type_roof": "1",
        "type_bearing_wall": "1",
        
        "roof_slope": "1.0",
        "snow_perpendicular": "1.0",
        "avs30": "123",
        "path_file":"20200526164338",
        "user_id": "1"
    }
```

### 戻り値:
```
	{
        "message": "New seismic created!",
        "status": "success",
        "data": {
            "no": "A123",
            "name": "name",
            "address": "address",
            "report_date": "2020-05-26",
            "area_floor_1": "1.0",
            "area_floor_2": "1.0",
            "area_floor_3": "1.0",
            "area_attic": "1.0",
            "area_ph": "1.0",
            "area_balcony_floor_2": "1.0",
            "area_balcony_floor_3": "1.0",
            "area_balcony_floor_top": "1.0",
            "height_division_1": "1.0",
            "height_floor_1": "1.0",
            "height_floor_2": "1.0",
            "height_floor_3": "1.0",
            "height_max": "1.0",
            "type_construction": "1",
            "method": "1",
            "type_fireproof": "1",
            "type_roof": "1",
            "type_bearing_wall": "1",
            "roof_slope": "1.0",
            "snow_perpendicular": "1.0",
            "avs30": "123",
            "path_file": "20200526164338",
            "user_id": "1",
            "id": "1"
        },
        "code": 1
    }
```

## 3.idによりデジタル耐震チェック書情報を取得
* **URL:** [{API_ROOT}/seismic/{id}](#)
* **Method:** GET
* **Content Type:** application/json
* **Reponse Type:** text/json

##### 例: 
		URL: [{API_ROOT}/seismic/{id}
### 戻り値:
    
  ```
	{
        "message": "Seismic details",
        "status": "success",
        "data": {
            "no": "A1234", //物件番号
            "name": "name", //物件名
            "address": "address", //住所
            "report_date": "2020-05-26 00:00:00", //報告書発行日
            "method_name": "軸組壁工法", //工法
            "total_area_floor": "3", //延べ床面積
            "height_max": "1", //最高高さ
            "number_of_floors": "3", //階数
            "type_roof_name": "彩色セメント版", //屋根仕様
            "type_bearing_wall_name": "構造用面材＋筋違", //耐力壁仕様
            "snow_perpendicular": "1", //多雪地積雪量
            
            "type_fireproof": "1",
            "roof_value": "1",

            "calA": 320.8
        },
        "code": 1
    }
  ```

## 4. デジタル耐震チェック書リストを取得 
* **URL:** [{API_ROOT}/seismics}](#)
* **Method:** GET
* **Content Type:** application/json
* **Reponse Type:** text/json

##### 例: 
		URL: [{API_ROOT}/seismics
### 戻り値:
    
  ```
	{
        "message": "Seismic details",
        "status": "success",
        "data": [
            {
                "no": "A1234",
                "name": "name",
                "address": "address",
                "details": [
                    {
                        "id": "8",
                        "userName": "Khoa",
                        "report_date": "2020-05-26 00:00:00"
                    },
                    {
                        "id": "7",
                        "userName": "Khoa",
                        "report_date": "2020-05-28 19:06:54"
                    },
                    ...
                ]
            },
            ...
        ],
        "code": 1
    }
  ```
  
## 5. access tokenを取得
* **URL:** [{API_ROOT}/auth/:key](#)
* **Method:** GET
* **Content Type:** application/json
* **Reponse Type:** text/json

#### Request: 
```
URL: {API_ROOT}/auth/abc123
```
#### Response:
    
  ```
	{
        "status": "success",
        "access_token": 4AS2LdsNCIMhKVXjaABz
    }
  ```
