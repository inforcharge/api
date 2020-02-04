---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript
  - php

toc_footers:
  - <a href='https://solmate.cc'>Solmate Home</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Solmate API! You can use our API to access Solmate AD endpoints.

We have language bindings in Shell, Ruby, Python, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> To authorize, use this code:

```ruby
def send_request
  uri = URI('https://api.solmate.cc/v2/')

  # Create client
  http = Net::HTTP.new(uri.host, uri.port)
  http.use_ssl = true
  http.verify_mode = OpenSSL::SSL::VERIFY_PEER

  # Create Request
  req =  Net::HTTP::Get.new(uri)
  # Add headers
  req.add_field "Authorization", "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl"

  # Fetch Request
  res = http.request(req)
  puts "Response HTTP Status Code: #{res.code}"
  puts "Response HTTP Response Body: #{res.body}"
rescue StandardError => e
  puts "HTTP Request failed (#{e.message})"
end
```

```python
import requests

def send_request():
    try:
        response = requests.get(
            url="https://api.solmate.cc/v2/",
            headers={
                "Authorization": "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl",
            },
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')
```

```shell
# With shell, you can just pass the correct header with each request
curl "https://api.solmate.cc/v2/" \
  -u 'api@solmate.cc:Ilovesolmate'
```

```javascript
jQuery.ajax({
    url: "https://api.solmate.cc/v2/",
    type: "GET",
    headers: {
        "Authorization": "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl",
    },
})
.done(function(data, textStatus, jqXHR) {
    console.log("HTTP Request Succeeded: " + jqXHR.status);
    console.log(data);
})
.fail(function(jqXHR, textStatus, errorThrown) {
    console.log("HTTP Request Failed");
})
.always(function() {
    /* ... */
});
```

```php
<?php

// Include Guzzle. If using Composer:
// require 'vendor/autoload.php';

use GuzzleHttp\Pool;
use GuzzleHttp\Client;
use GuzzleHttp\Psr7\Request;

$client = new Client();

$request = new Request(
        "GET",
        "https://api.solmate.cc/v2/",
        [
            "Authorization" => "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl",
            "Content-Type" => "application/json; charset=utf-8"
        ],
        "{}");

$response = $client->send($request);
echo "Response HTTP : " . $response->getStatusCode() . "
";
```

> Make sure to replace `Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl` with your API key.

Solmate uses HTTP Basic Auth to allow access to the API. We will give you account and password like:

account:**api@solmate.cc**

password:**IloveSolmate**

Solmate expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl"`

<aside class="notice">
You must replace <code>"Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl"</code> with your HTTP Basic Auth.
</aside>

# Orders

## Create new Order

```ruby
require 'net/http'
require 'net/https'
require 'json'

def send_request
  uri = URI('https://api.solmate.cc/v2/orders')

  # Create client
  http = Net::HTTP.new(uri.host, uri.port)
  http.use_ssl = true
  http.verify_mode = OpenSSL::SSL::VERIFY_PEER
  dict = {
            "title" => "淘米-賽爾號星戰再起",
            "network" => "vieshow",
            "model" => "cpm",
            "start_at" => "2019-03-10 13:00",
            "end_at" => "2019-05-10 21:00",
            "total_budget" => "20000",
            "daily_budget" => "2000",
            "material_url" => "https://cdn.solmate.cc/uploads/ad/display_file/886/4e144283de.mp4",
            "click_url" => "https://cdn.solmate.cc/uploads/ad/trigger_file/886/cc68227be5.jpg",
            "sessions" => ["Morning", "Evening"],
            "display_time" => "30",
            "gender" => "",
            "districts" => ["台北信義市府", "台北士林天母"],
            "stores" => ['信義威秀', '中和大潤發', '天母大葉高島屋'],
            "hourly_notification" => "https://notification.clickforce.com.tw/api/solmate",
            "daily_notification" => "",
        }
  body = JSON.dump(dict)

  # Create Request
  req =  Net::HTTP::Post.new(uri)
  # Add headers
  req.add_field "Authorization", "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl"
  # Add headers
  req.add_field "Content-Type", "application/json; charset=utf-8"
  # Set body
  req.body = body

  # Fetch Request
  res = http.request(req)
  puts "Response HTTP Status Code: #{res.code}"
  puts "Response HTTP Response Body: #{res.body}"
rescue StandardError => e
  puts "HTTP Request failed (#{e.message})"
end

```

```python
import requests
import json

def send_request():
    try:
        response = requests.post(
            url="https://api.solmate.cc/v2/orders",
            headers={
                "Authorization": "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl",
                "Content-Type": "application/json; charset=utf-8",
            },
            data=json.dumps({
                "title": "淘米-賽爾號星戰再起",
                "network": "vieshow",
                "model": "cpm",
                "start_at": "2019-03-10 13:00",
                "end_at": "2019-05-10 21:00",
                "total_budget": "20000",
                "daily_budget": "2000",
                "material_url": "https://cdn.solmate.cc/uploads/ad/display_file/886/4e144283de.mp4",
                "click_url": "https://cdn.solmate.cc/uploads/ad/trigger_file/886/cc68227be5.jpg",
                "priority": "3",
                "sessions": ["Morning", "Evening"],
                "display_time": "30",
                "gender": "",
                "districts": ["台北信義市府", "台北士林天母"],
                "stores": ['信義威秀', '中和大潤發', '天母大葉高島屋'],
                "hourly_notification": "https://notification.clickforce.com.tw/api/solmate",
                "daily_notification": "",
            })
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')

```

```shell
curl -X "POST" "https://api.solmate.cc/v2/orders" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -u 'api@solmate.cc:Ilovesolmate' \
     -d $'{
  "title": "淘米-賽爾號星戰再起",
  "network": "vieshow",
  "model": "cpm",
  "start_at": "2019-03-10 13:00",
  "end_at": "2019-05-10 21:00",
  "total_budget": "20000",
  "daily_budget": "2000",
  "material_url": "https://cdn.solmate.cc/uploads/ad/display_file/886/4e144283de.mp4",
  "click_url": "https://cdn.solmate.cc/uploads/ad/trigger_file/886/cc68227be5.jpg",
  "priority": "3",
  "sessions": ["Morning", "Evening"],
  "display_time": "30",
  "gender": "",
  "districts": ["台北信義市府", "台北士林天母"],
  "stores": ["信義威秀", "中和大潤發", "天母大葉高島屋"],
  "hourly_notification": "https://notification.clickforce.com.tw/api/solmate",
  "daily_notification": "",
}'
```

```javascript
jQuery.ajax({
    url: "https://api.solmate.cc/v2/orders",
    type: "POST",
    headers: {
        "Authorization": "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl",
        "Content-Type": "application/json; charset=utf-8",
    },
    contentType: "application/json",
    data: JSON.stringify({
        "title": "淘米-賽爾號星戰再起",
        "network": "vieshow",
        "model": "cpm",
        "start_at": "2019-03-10 13:00",
        "end_at": "2019-05-10 21:00",
        "total_budget": "20000",
        "daily_budget": "2000",
        "material_url": "https://cdn.solmate.cc/uploads/ad/display_file/886/4e144283de.mp4",
        "click_url": "https://cdn.solmate.cc/uploads/ad/trigger_file/886/cc68227be5.jpg",
        "priority": "3",
        "sessions": ["Morning", "Evening"],
        "display_time": "30",
        "gender": "",
        "districts": ["台北信義市府", "台北士林天母"],
        "stores": ['信義威秀', '中和大潤發', '天母大葉高島屋'],
        "hourly_notification": "https://notification.clickforce.com.tw/api/solmate",
        "daily_notification": "",
    })
})
.done(function(data, textStatus, jqXHR) {
    console.log("HTTP Request Succeeded: " + jqXHR.status);
    console.log(data);
})
.fail(function(jqXHR, textStatus, errorThrown) {
    console.log("HTTP Request Failed");
})
.always(function() {
    /* ... */
});
```

```php
<?php

// Include Guzzle. If using Composer:
// require 'vendor/autoload.php';

use GuzzleHttp\Pool;
use GuzzleHttp\Client;
use GuzzleHttp\Psr7\Request;

$client = new Client();

$request = new Request(
        "POST",
        "https://api.solmate.cc/v2/orders",
        [
            "Authorization" => "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl",
            "Content-Type" => "application/json; charset=utf-8"
        ],
        "{\"title\":\"\\u6dd8\\u7c73-\\u8cfd\\u723e\\u865f\\u661f\\u6230\\u518d\\u8d77\",\"network\":\"vieshow\",\"total_budget\":\"20000\",\"daily_budget\":\"2000\",\"material_url\":\"https://cdn.solmate.cc/uploads/ad/display_file/886/4e144283de.mp4\",\"click_url\":\"https://cdn.solmate.cc/uploads/ad/trigger_file/886/cc68227be5.jpg\",\"priority\":\"3\",\"display_time\":\"30\",\"gender\":\"\",\"district\":[\"\\u53f0\\u5317\\u58eb\\u6797\\u5929\\u6bcd\",\"\\u53f0\\u5317\\u4fe1\\u7fa9\\u5e02\\u5e9c\"],\"model\":\"cpm\",\"start_at\":\"2019-03-01 12:00\",\"end_at\":\"2019-06-30 23:59\",\"sessions\":[\"Morning\",\"Evening\"]}");

$response = $client->send($request);
echo "Response HTTP : " . $response->getStatusCode() . "
";
```

> The above command returns JSON structured like this:

> Success response:

```json
{
  "id": "102341285566",
}
```

> Failed response:

```json
{
  "message": "model should not be empty",
}
```

This endpoint creates a new order.

### HTTP Request

`POST https://api.solmate.cc/v2/orders`

### POST Parameters

Parameter | Default | Description
--------- | ------- | -----------
title | required | AD title
network | required | `vieshow`, `salon`, `live`
model | required | `cpm`, `cpv`
start_at | required | We use UTC+8 with ISO 8601 formats like '%Y-%m-%d %H:%M', `2019-05-12 12:10`
end_at | required | We use UTC+8 with ISO 8601 formats like '%Y-%m-%d %H:%M', `2019-06-30 23:59`
total_budget | required | must larger than 0
daily_budget | required | must larger than 0
material_url | required | material url link like, https://cdn.solmate.cc/uploads/ad/display_file/886/4e144283de.mp4
click_url | required | clicks material url link like, https://cdn.solmate.cc/uploads/ad/trigger_file/886/cc68227be5.jpg
priority | optional | `vewshow` default is 2, `salon` and `live` is 1, The largest value is 10.
sessions | optional | Empty array is no limit or you could use multiple selection like `Morning`, `Afternoon`, `Evening`.
display_time | optional | Image default is 30 seconds, Video is auto detected by its length.
gender | optional | Empty string is no limit. `male`, `female`
stores | optional | Empty string is no limit. You could get store list from other API.
districts | optional | Empty array is no limit. <ul><li>台北中山大同</li><li>台北信義安和</li><li>台北信義市府</li><li>台北南京八德</li><li>台北士林天母</li><li>台北大直內湖</li><li>台北師大公館</li><li>台北忠孝東路</li><li>台北木柵政大</li><li>台北東門永康</li><li>台北松江南京</li><li>台北民生民權</li><li>台北永春南港</li><li>台北西門艋舺</li><li>新北三重蘆洲</li><li>新北中和永和</li><li>新北新莊泰山</li><li>新北板橋土城</li><li>新北汐止車站</li><li>桃園中壢市區</li><li>新竹市區</li><li>台中市區</li><li>台南市區</li><li>高雄市區</li><li>台北景美新店</li><li>新竹車站市區</li><li>苗栗頭份市區</li><li>桃園車站市區</li><li>台北中正站前</li><li>宜蘭車站市區</li><li>屏東市區</li><li>其他</li></ul>
hourly_notification | optional | The URL of the webhook endpoint, Solmate will post orders data hourly. More information you could see <a href="#notification">Notification</a>
daily_notification | optional | The URL of the webhook endpoint, Solmate will post orders data daily. More information you could see <a href="#notification">Notification</a>


### Network Parameters
| Name  | Range  |
| ------------ | ------------ |
| vieshow  | 威秀聯播網  |
| salon   | 美髮聯播網  |
| live   | 餐廳咖啡廳聯播網 (包含區域特色店家 etc)  |

### Sessions Parameters
| Name  | Range  |
| ------------ | ------------ |
| Morning  | 07:00 - 12:00  |
| Afternoon   | 12:00 - 18:00  |
| Evening   | 18:00 - 23:00  |


## Get a Specific Order

```ruby
require 'net/http'
require 'net/https'
require 'json'

def send_request
  uri = URI('https://api.solmate.cc/v2/orders/102341285566')

  # Create client
  http = Net::HTTP.new(uri.host, uri.port)
  http.use_ssl = true
  http.verify_mode = OpenSSL::SSL::VERIFY_PEER
  dict = {}
  body = JSON.dump(dict)

  # Create Request
  req =  Net::HTTP::Get.new(uri)
  # Add headers
  req.add_field "Authorization", "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl"
  # Add headers
  req.add_field "Content-Type", "application/json; charset=utf-8"
  # Set body
  req.body = body

  # Fetch Request
  res = http.request(req)
  puts "Response HTTP Status Code: #{res.code}"
  puts "Response HTTP Response Body: #{res.body}"
rescue StandardError => e
  puts "HTTP Request failed (#{e.message})"
end

```

```python
import requests
import json

def send_request():
    try:
        response = requests.get(
            url="https://api.solmate.cc/v2/orders/102341285566",
            headers={
                "Authorization": "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl",
                "Content-Type": "application/json; charset=utf-8",
            },
            data=json.dumps({

            })
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')
```

```shell
curl "https://api.solmate.cc/v2/orders/102341285566" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -u 'api@solmate.cc:Ilovesolmate' \
     -d $'{}'
```

```javascript
jQuery.ajax({
    url: "https://api.solmate.cc/v2/orders/102341285566",
    type: "GET",
    headers: {
        "Authorization": "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl",
        "Content-Type": "application/json; charset=utf-8",
    },
})
.done(function(data, textStatus, jqXHR) {
    console.log("HTTP Request Succeeded: " + jqXHR.status);
    console.log(data);
})
.fail(function(jqXHR, textStatus, errorThrown) {
    console.log("HTTP Request Failed");
})
.always(function() {
    /* ... */
});
```

```php
<?php

// Include Guzzle. If using Composer:
// require 'vendor/autoload.php';

use GuzzleHttp\Pool;
use GuzzleHttp\Client;
use GuzzleHttp\Psr7\Request;

$client = new Client();

$request = new Request(
        "GET",
        "https://api.solmate.cc/v2/orders/102341285566",
        [
            "Authorization" => "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl",
            "Content-Type" => "application/json; charset=utf-8",
        ],
        "{}");

$response = $client->send($request);
echo "Response HTTP : " . $response->getStatusCode() . "
";
```

> The above command returns JSON structured like this:

> Success response:

```json
{
  "id": "102341285566",
  "title": "淘米-賽爾號星戰再起",
  "network": "vieshow",
  "model": "cpm",
  "start_at": "2019-03-10 13:00",
  "end_at": "2019-05-10 21:00",
  "total_budget": "20000",
  "daily_budget": "2000",
  "material_url": "https://cdn.solmate.cc/uploads/ad/display_file/886/4e144283de.mp4",
  "click_url": "https://cdn.solmate.cc/uploads/ad/trigger_file/886/cc68227be5.jpg",
  "priority": "3",
  "sessions": ["Morning", "Evening"],
  "display_time": "30",
  "gender": "",
  "districts": ["台北信義市府", "台北士林天母"],
  "hourly_notification": "https://notification.clickforce.com.tw/api/solmate",
  "daily_notification": "",
}
```

> Failed response:

```json
{
  "message": "AD ID is not found",
}
```

This endpoint update a specific order.

### HTTP Request

`GET https://api.solmate.cc/v2/orders/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the order to retrieve


### Response Parameters

Parameter | Description
--------- | -----------
ID | The ID of the order to retrieve
title |  AD title
network | `vieshow`, `salon`, `live`
model | `cpm`, `cpv`
start_at | We use UTC+8 with ISO 8601 formats like '%Y-%m-%d %H:%M', `2019-05-12 12:10`
end_at | We use UTC+8 with ISO 8601 formats like '%Y-%m-%d %H:%M', `2019-06-30 23:59`
total_budget | must larger than 0
daily_budget | must larger than 0
material_url | material url link like, https://cdn.solmate.cc/uploads/ad/display_file/886/4e144283de.mp4
click_url | clicks material url link like, https://cdn.solmate.cc/uploads/ad/trigger_file/886/cc68227be5.jpg
priority | `vewshow` default is 2, `salon` and `live` is 1, The largest value is 10.
sessions | Empty array is no limit or you could use multiple selection like `Morning`, `Afternoon`, `Evening`.
display_time | Image material default is 30 seconds, Video is auto detected by its length.
gender | Empty string is no limit. `male`, `female`
districts | Empty array is no limit. <ul><li>台北中山大同</li><li>台北信義安和</li><li>台北信義市府</li><li>台北南京八德</li><li>台北士林天母</li><li>台北大直內湖</li><li>台北師大公館</li><li>台北忠孝東路</li><li>台北木柵政大</li><li>台北東門永康</li><li>台北松江南京</li><li>台北民生民權</li><li>台北永春南港</li><li>台北西門艋舺</li><li>新北三重蘆洲</li><li>新北中和永和</li><li>新北新莊泰山</li><li>新北板橋土城</li><li>新北汐止車站</li><li>桃園中壢市區</li><li>新竹市區</li><li>台中市區</li><li>台南市區</li><li>高雄市區</li><li>台北景美新店</li><li>新竹車站市區</li><li>苗栗頭份市區</li><li>桃園車站市區</li><li>台北中正站前</li><li>宜蘭車站市區</li><li>屏東市區</li><li>其他</li></ul>
hourly_notification | The URL of the webhook endpoint, Solmate will post orders data hourly. More information you could see <a href="#notification">Notification</a>
daily_notification | The URL of the webhook endpoint, Solmate will post orders data daily. More information you could see <a href="#notification">Notification</a>



## Update a Specific Order

```ruby
require 'net/http'
require 'net/https'
require 'json'

# update Order (PUT )
def send_request
  uri = URI('https://api.solmate.cc/v2/orders/102341285566')

  http = Net::HTTP.new(uri.host, uri.port)
  http.use_ssl = true
  http.verify_mode = OpenSSL::SSL::VERIFY_PEER
  dict = {
            "gender" => "",
            "district" => [
                "台北士林天母",
                "台北信義市府"
            ],
            "total_budget" => "20000",
            "daily_budget" => "2000",
            "click_url" => "https://cdn.solmate.cc/uploads/ad/trigger_file/886/cc68227be5.jpg",
            "priority" => "2",
            "model" => "cpm",
            "display_time" => "30",
            "material_url" => "https://cdn.solmate.cc/uploads/ad/display_file/886/4e144283de.mp4"
        }
  body = JSON.dump(dict)

  # Create Request
  req =  Net::HTTP::Put.new(uri)
  # Add headers
  req.add_field "Authorization", "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl"
  # Add headers
  req.add_field "Content-Type", "application/json; charset=utf-8"
  # Set body
  req.body = body

  # Fetch Request
  res = http.request(req)
  puts "Response HTTP Status Code: #{res.code}"
  puts "Response HTTP Response Body: #{res.body}"
rescue StandardError => e
  puts "HTTP Request failed (#{e.message})"
end
```

```python
import requests
import json

def send_request():
    try:
        response = requests.put(
            url="https://api.solmate.cc/v2/orders/102341285566",
            headers={
                "Authorization": "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl",
                "Content-Type": "application/json; charset=utf-8",
            },
            data=json.dumps({
                "gender": "",
                "district": [
                    "台北士林天母",
                    "台北信義市府"
                ],
                "total_budget": "20000",
                "daily_budget": "2000",
                "click_url": "https://cdn.solmate.cc/uploads/ad/trigger_file/886/cc68227be5.jpg",
                "priority": "3",
                "model": "cpm",
                "display_time": "30",
                "material_url": "https://cdn.solmate.cc/uploads/ad/display_file/886/4e144283de.mp4"
            })
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')
```

```shell
curl -X "PUT" "https://api.solmate.cc/v2/orders/102341285566" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -u 'api@solmate.cc:Ilovesolmate' \
     -d $'{
  "gender": "",
  "district": [
    "台北士林天母",
    "台北信義市府"
  ],
  "total_budget": "20000",
  "daily_budget": "2000",
  "click_url": "https://cdn.solmate.cc/uploads/ad/trigger_file/886/cc68227be5.jpg",
  "priority": "3",
  "model": "cpm",
  "display_time": "30",
  "material_url": "https://cdn.solmate.cc/uploads/ad/display_file/886/4e144283de.mp4"
}'
```

```javascript
jQuery.ajax({
    url: "https://api.solmate.cc/v2/orders/102341285566",
    type: "PUT",
    headers: {
        "Authorization": "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl",
        "Content-Type": "application/json; charset=utf-8",
    },
    contentType: "application/json",
    data: JSON.stringify({
        "gender": "",
        "district": [
            "台北士林天母",
            "台北信義市府"
        ],
        "total_budget": "20000",
        "daily_budget": "2000",
        "click_url": "https://cdn.solmate.cc/uploads/ad/trigger_file/886/cc68227be5.jpg",
        "priority": "3",
        "model": "cpm",
        "display_time": "30",
        "material_url": "https://cdn.solmate.cc/uploads/ad/display_file/886/4e144283de.mp4"
    })
})
.done(function(data, textStatus, jqXHR) {
    console.log("HTTP Request Succeeded: " + jqXHR.status);
    console.log(data);
})
.fail(function(jqXHR, textStatus, errorThrown) {
    console.log("HTTP Request Failed");
})
.always(function() {
    /* ... */
});
```

```php
<?php

// Include Guzzle. If using Composer:
// require 'vendor/autoload.php';

use GuzzleHttp\Pool;
use GuzzleHttp\Client;
use GuzzleHttp\Psr7\Request;

$client = new Client();

$request = new Request(
        "PUT",
        "https://api.solmate.cc/v2/orders/102341285566",
        [
            "Authorization" => "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl",
            "Content-Type" => "application/json; charset=utf-8"
        ],
        "{\"total_budget\":\"20000\",\"daily_budget\":\"2000\",\"material_url\":\"https://cdn.solmate.cc/uploads/ad/display_file/886/4e144283de.mp4\",\"click_url\":\"https://cdn.solmate.cc/uploads/ad/trigger_file/886/cc68227be5.jpg\",\"priority\":\"3\",\"display_time\":\"30\",\"gender\":\"\",\"district\":[\"\\u53f0\\u5317\\u58eb\\u6797\\u5929\\u6bcd\",\"\\u53f0\\u5317\\u4fe1\\u7fa9\\u5e02\\u5e9c\"],\"model\":\"cpm\"}");

$response = $client->send($request);
echo "Response HTTP : " . $response->getStatusCode() . "
";
```

> The above command returns JSON structured like this:

> Success response:

```json
{
  "id": "102341285566",
}
```

> Failed response:

```json
{
  "message": "model should not be empty",
}
```

This endpoint update a specific order.

### HTTP Request

`PUT https://api.solmate.cc/v2/orders/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the order to retrieve

### Available Change Parameters

Parameter | Default | Description
--------- | ------- | -----------
start_at | required | We use UTC+8 with ISO 8601 formats like '%Y-%m-%d %H:%M', `2019-05-12 12:10`
end_at | required | We use UTC+8 with ISO 8601 formats like '%Y-%m-%d %H:%M', `2019-06-30 23:59`
total_budget | required | must larger than 0
daily_budget | required | must larger than 0
material_url | required | material url link like, https://cdn.solmate.cc/uploads/ad/display_file/886/4e144283de.mp4
click_url | required | clicks material url link like, https://cdn.solmate.cc/uploads/ad/trigger_file/886/cc68227be5.jpg
priority | optional | `vewshow` default is 2, `salon` and `live` is 1, The largest value is 10.
sessions | optional | Empty array is no limit or you could use multiple selection like `Morning`, `Afternoon`, `Evening`.
display_time | optional | default is 30 seconds.
gender | optional | Empty string is no limit. `male`, `female`
districts | optional | Empty array is no limit. <ul><li>台北中山大同</li><li>台北信義安和</li><li>台北信義市府</li><li>台北南京八德</li><li>台北士林天母</li><li>台北大直內湖</li><li>台北師大公館</li><li>台北忠孝東路</li><li>台北木柵政大</li><li>台北東門永康</li><li>台北松江南京</li><li>台北民生民權</li><li>台北永春南港</li><li>台北西門艋舺</li><li>新北三重蘆洲</li><li>新北中和永和</li><li>新北新莊泰山</li><li>新北板橋土城</li><li>新北汐止車站</li><li>桃園中壢市區</li><li>新竹市區</li><li>台中市區</li><li>台南市區</li><li>高雄市區</li><li>台北景美新店</li><li>新竹車站市區</li><li>苗栗頭份市區</li><li>桃園車站市區</li><li>台北中正站前</li><li>宜蘭車站市區</li><li>屏東市區</li><li>其他</li></ul>
hourly_notification | optional | The URL of the webhook endpoint, Solmate will post orders data hourly.
daily_notification | optional | The URL of the webhook endpoint, Solmate will post orders data daily.


## Get Order Status

```ruby
require 'net/http'
require 'net/https'
require 'json'

def send_request
  uri = URI('https://api.solmate.cc/v2/orders/102341285566/status')

  # Create client
  http = Net::HTTP.new(uri.host, uri.port)
  http.use_ssl = true
  http.verify_mode = OpenSSL::SSL::VERIFY_PEER
  dict = {}
  body = JSON.dump(dict)

  # Create Request
  req =  Net::HTTP::Get.new(uri)
  # Add headers
  req.add_field "Authorization", "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl"
  # Add headers
  req.add_field "Content-Type", "application/json; charset=utf-8"
  # Set body
  req.body = body

  # Fetch Request
  res = http.request(req)
  puts "Response HTTP Status Code: #{res.code}"
  puts "Response HTTP Response Body: #{res.body}"
rescue StandardError => e
  puts "HTTP Request failed (#{e.message})"
end
```

```python
import requests
import json

def send_request():
    try:
        response = requests.get(
            url="https://api.solmate.cc/v2/orders/102341285566/status",
            headers={
                "Authorization": "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl",
                "Content-Type": "application/json; charset=utf-8",
            },
            data=json.dumps({

            })
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')
```

```shell
curl "https://api.solmate.cc/v2/orders/102341285566/status" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -u 'api@solmate.cc:Ilovesolmate' \
     -d $'{}'
```

```javascript
jQuery.ajax({
    url: "https://api.solmate.cc/v2/orders/102341285566/status",
    type: "GET",
    headers: {
        "Authorization": "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl",
        "Content-Type": "application/json; charset=utf-8",
    },
})
.done(function(data, textStatus, jqXHR) {
    console.log("HTTP Request Succeeded: " + jqXHR.status);
    console.log(data);
})
.fail(function(jqXHR, textStatus, errorThrown) {
    console.log("HTTP Request Failed");
})
.always(function() {
    /* ... */
});
```

```php
<?php

// Include Guzzle. If using Composer:
// require 'vendor/autoload.php';

use GuzzleHttp\Pool;
use GuzzleHttp\Client;
use GuzzleHttp\Psr7\Request;

$client = new Client();

$request = new Request(
        "GET",
        "https://api.solmate.cc/v2/orders/102341285566/status",
        [
            "Authorization" => "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl",
            "Content-Type" => "application/json; charset=utf-8"
        ],
        "{}");

$response = $client->send($request);
echo "Response HTTP : " . $response->getStatusCode() . "
";
```

> The above command returns JSON structured like this:

> Success response:

```json
{
  "status": "running",
}

{
  "status": "error",
  "message": "time error",
}
```

> Failed response:

```json

{
  "message" : "Wrong AD id",
}
```

This endpoint get a specific order status.

### HTTP Request

`GET https://api.solmate.cc/v2/orders/<ID>/status`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the order


### Response Parameters
Parameter | Description
--------- | -----------
status | <ul><li>running</li><li>waiting</li><li>limit by budget</li><li>error</li><li>stop</li></ul>


### Status Description
Name | Description
--------- | -----------
running | 廣告播放中 (正常播放)
limit by budget | 每日預算已消耗完, 隔天會自動重啟
pending | 等待審核
waiting | 廣告開始時間尚未到
stop | 暫停
error | 廣告設定錯誤, 或是退審


## Get Order Report

```ruby
require 'net/http'
require 'net/https'
require 'json'

# get Order Report (GET )
def send_request
  uri = URI('https://api.solmate.cc/v2/orders/21/reports?start_at=2019-06-11%2013:00:00&report_type=hourly')

  # Create client
  http = Net::HTTP.new(uri.host, uri.port)
  http.use_ssl = true
  http.verify_mode = OpenSSL::SSL::VERIFY_PEER
  dict = {

        }
  body = JSON.dump(dict)

  # Create Request
  req =  Net::HTTP::Get.new(uri)
  # Add headers
  req.add_field "Authorization", "Basic YXBpQGNsaWNrZm9yY2UuY29tLnR3OjU2ZTYxOWRjZDk5MTI1YmUwYWNm"
  # Add headers
  req.add_field "Content-Type", "application/json; charset=utf-8"
  # Set body
  req.body = body

  # Fetch Request
  res = http.request(req)
  puts "Response HTTP Status Code: #{res.code}"
  puts "Response HTTP Response Body: #{res.body}"
rescue StandardError => e
  puts "HTTP Request failed (#{e.message})"
end
```

```python
import requests
import json

def send_request():
    try:
        response = requests.get(
            url="https://api.solmate.cc/v2/orders/21/reports",
            params={
                "start_at": "2019-06-11 13:00:00",
                "report_type": "hourly",
            },
            headers={
                "Authorization": "Basic YXBpQGNsaWNrZm9yY2UuY29tLnR3OjU2ZTYxOWRjZDk5MTI1YmUwYWNm",
                "Content-Type": "application/json; charset=utf-8",
            },
            data=json.dumps({

            })
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')
```

```shell
curl "https://api.solmate.cc/v2/orders/21/reports?start_at=2019-06-11%2013:00:00&report_type=hourly" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -u 'api@clickforce.com.tw:56e619dcd99125be0acf' \
     -d $'{}'
```

```javascript
jQuery.ajax({
    url: "https://api.solmate.cc/v2/orders/21/reports",
    type: "GET",
    data: {
        "start_at": "2019-06-11 13:00:00",
        "report_type": "hourly",
    },
    headers: {
        "Authorization": "Basic YXBpQGNsaWNrZm9yY2UuY29tLnR3OjU2ZTYxOWRjZDk5MTI1YmUwYWNm",
        "Content-Type": "application/json; charset=utf-8",
    },
})
.done(function(data, textStatus, jqXHR) {
    console.log("HTTP Request Succeeded: " + jqXHR.status);
    console.log(data);
})
.fail(function(jqXHR, textStatus, errorThrown) {
    console.log("HTTP Request Failed");
})
.always(function() {
    /* ... */
});
```

```php
<?php

// Include Guzzle. If using Composer:
// require 'vendor/autoload.php';

use GuzzleHttp\Pool;
use GuzzleHttp\Client;
use GuzzleHttp\Psr7\Request;

$client = new Client();

$request = new Request(
        "GET",
        "https://api.solmate.cc/v2/orders/21/reports?start_at=2019-06-11%2013:00:00&report_type=hourly",
        [
            "Authorization" => "Basic YXBpQGNsaWNrZm9yY2UuY29tLnR3OjU2ZTYxOWRjZDk5MTI1YmUwYWNm",
            "Content-Type" => "application/json; charset=utf-8"
        ],
        "{}");

$response = $client->send($request);
echo "Response HTTP : " . $response->getStatusCode() . "
";
```

> The above command returns JSON structured like this:

> Success response:

```json
{
  "id": "102341285566",
  "total_budget": 25000,
  "total_cost": 15566,
  "daily_budget": 2000,
  "cost": 1781,
  "impressions": 30254,
  "clicks": 710,
  "clickthrough_rate": 0.37,
  "views": 8511,
  "view_rate": 0.28,
  "faces": 1939,
  "male": 198,
  "female": 469,
  "unknown": 1272,
  "age_18_24": 322,
  "age_25_34": 297,
  "age_35_44": 36,
  "age_45_54": 11,
  "age_55_64": 1,
  "age_65": 0,
  "face_25": 10,
  "face_26_50": 200,
  "face_51_75": 290,
  "face_76_100": 167,
}
```

> Failed response:

```json
{
  "message" : "ID is not found",
}
```

This endpoint gets a report by specific time. We now temporarily support hourly report.

### HTTP Request

`GET https://api.solmate.cc/v2/orders/<ID>/reports`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the order

### GET Parameters

Parameter | Default | Description
--------- | ------- | -----------
report_type | required | `hourly`, `daily`
start_at | required | We use UTC+8 with ISO 8601 formats like '%Y-%m-%d %H:%M', `2019-05-12 14:00`

### Response Parameters

Attribute Name | Description
--------- | -----------
id | The ID of the order
total_budget | An amount that specify the maximum amount of budget spend over the period in which it runs.
total_cost | An amount that already spend over the period.
daily_budget | An amount that you set for each ad to spend each day.
cost | An amount that you already spent in a specific time.
impressions | How many times your ads were shown to viewers.
clicks | Show you the number of times people clicked on your video.
clickthrough_rate | The number of clicks that your ad receives divided by the number of times your ad is shown.
views | Show the number of times reach people.
view_rate | Show you the number of reach people divided by the number of times your ad is shown
faces | Show the number of times people watched video ad.
male | How many male people watched video ad.
female | How many female people watched video ad.
age_18_24 | How many people age between 18 ~ 24 watched video ad.
age_25_34 | How many people age between 25 ~ 34 watched video ad.
age_35_44 | How many people age between 35 ~ 44 watched video ad.
age_45_54 | How many people age between 45 ~ 54 watched video ad.
age_65 | How many people age over 65 watched video ad.
face_25 | shows how often a video is played to 0% ~ 25% of its length.
face_26_50 | shows how often a video is played to 26% ~ 50% of its length.
face_51_75 | shows how often a video is played to 51% ~ 75% of its length.
face_76_100 | shows how often a video is played to 76% ~ 100% of its length.


## Update Order Status

```ruby
require 'net/http'
require 'net/https'
require 'json'

# update Order Status (PUT )
def send_request
  uri = URI('https://api.solmate.cc/v2/orders/102341285566/status')

  # Create client
  http = Net::HTTP.new(uri.host, uri.port)
  http.use_ssl = true
  http.verify_mode = OpenSSL::SSL::VERIFY_PEER
  dict = {
            "action" => "Pause"
        }
  body = JSON.dump(dict)

  # Create Request
  req =  Net::HTTP::Put.new(uri)
  # Add headers
  req.add_field "Authorization", "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl"
  # Add headers
  req.add_field "Content-Type", "application/json; charset=utf-8"
  # Set body
  req.body = body

  # Fetch Request
  res = http.request(req)
  puts "Response HTTP Status Code: #{res.code}"
  puts "Response HTTP Response Body: #{res.body}"
rescue StandardError => e
  puts "HTTP Request failed (#{e.message})"
end
```

```python
import requests
import json

def send_request():
    try:
        response = requests.put(
            url="https://api.solmate.cc/v2/orders/102341285566/status",
            headers={
                "Authorization": "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl",
                "Content-Type": "application/json; charset=utf-8",
            },
            data=json.dumps({
                "action": "Pause"
            })
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')

```

```shell
curl -X "PUT" "https://api.solmate.cc/v2/orders/102341285566/status" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -u 'api@solmate.cc:Ilovesolmate' \
     -d $'{
  "action": "Pause"
}'
```

```javascript
jQuery.ajax({
    url: "https://api.solmate.cc/v2/orders/102341285566/status",
    type: "PUT",
    headers: {
        "Authorization": "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl",
        "Content-Type": "application/json; charset=utf-8",
    },
    contentType: "application/json",
    data: JSON.stringify({
        "action": "Pause"
    })
})
.done(function(data, textStatus, jqXHR) {
    console.log("HTTP Request Succeeded: " + jqXHR.status);
    console.log(data);
})
.fail(function(jqXHR, textStatus, errorThrown) {
    console.log("HTTP Request Failed");
})
.always(function() {
    /* ... */
});
```

```php
<?php

// Include Guzzle. If using Composer:
// require 'vendor/autoload.php';

use GuzzleHttp\Pool;
use GuzzleHttp\Client;
use GuzzleHttp\Psr7\Request;

$client = new Client();

$request = new Request(
        "PUT",
        "https://api.solmate.cc/v2/orders/102341285566/status",
        [
            "Authorization" => "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl",
            "Content-Type" => "application/json; charset=utf-8",
        ],
        "{\"action\":\"pause\"}");

$response = $client->send($request);
echo "Response HTTP : " . $response->getStatusCode() . "
";
```

> The above command returns JSON structured like this:

> Success response:

```json
{
  "status" : "Stop"
}
```

> Failed response:

```json
{
  "message" : "status can't be changed",
}
```

This endpoint deletes a specific order.

### HTTP Request

`PUT https://api.solmate.cc/v2/orders/<ID>/status`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the order

### PUT Parameters

Parameter | Default | Description
--------- | ------- | -----------
action | required | `Pause`, `Resume`

## Delete a Specific Order

```ruby
require 'net/http'
require 'net/https'
require 'json'

def send_request
  uri = URI('https://api.solmate.cc/v2/orders/102341285566')

  http = Net::HTTP.new(uri.host, uri.port)
  http.use_ssl = true
  http.verify_mode = OpenSSL::SSL::VERIFY_PEER
  dict = {}
  body = JSON.dump(dict)

  # Create Request
  req =  Net::HTTP::Delete.new(uri)
  # Add headers
  req.add_field "Authorization", "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl"
  # Add headers
  req.add_field "Content-Type", "application/json; charset=utf-8"
  # Set body
  req.body = body

  # Fetch Request
  res = http.request(req)
  puts "Response HTTP Status Code: #{res.code}"
  puts "Response HTTP Response Body: #{res.body}"
rescue StandardError => e
  puts "HTTP Request failed (#{e.message})"
end
```

```python
import requests
import json

def send_request():
    try:
        response = requests.delete(
            url="https://api.solmate.cc/v2/orders/102341285566",
            headers={
                "Authorization": "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl",
                "Content-Type": "application/json; charset=utf-8",
            },
            data=json.dumps({})
        )
        print('Response HTTP Status Code: {status_code}'.format(
            status_code=response.status_code))
        print('Response HTTP Response Body: {content}'.format(
            content=response.content))
    except requests.exceptions.RequestException:
        print('HTTP Request failed')
```

```shell
curl -X "DELETE" "https://api.solmate.cc/v2/orders/102341285566" \
     -H 'Content-Type: application/json; charset=utf-8' \
     -u 'api@solmate.cc:Ilovesolmate' \
     -d $'{}'
```

```javascript
jQuery.ajax({
    url: "https://api.solmate.cc/v2/orders/102341285566",
    type: "DELETE",
    headers: {
        "Authorization": "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl",
        "Content-Type": "application/json; charset=utf-8",
    },
    contentType: "application/json",
    data: JSON.stringify({

    })
})
.done(function(data, textStatus, jqXHR) {
    console.log("HTTP Request Succeeded: " + jqXHR.status);
    console.log(data);
})
.fail(function(jqXHR, textStatus, errorThrown) {
    console.log("HTTP Request Failed");
})
.always(function() {
    /* ... */
});
```

```php
<?php

// Include Guzzle. If using Composer:
// require 'vendor/autoload.php';

use GuzzleHttp\Pool;
use GuzzleHttp\Client;
use GuzzleHttp\Psr7\Request;

$client = new Client();

$request = new Request(
        "DELETE",
        "https://api.solmate.cc/v2/orders/102341285566",
        [
            "Authorization" => "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl",
            "Content-Type" => "application/json; charset=utf-8"
        ],
        "{}");

$response = $client->send($request);
echo "Response HTTP : " . $response->getStatusCode() . "
";
```

> The above command returns JSON structured like this:

> Success response:

```json
{
  "id": "102341285566",
  "deleted": true
}
```

> Failed response:

```json
{
  "message" : "ID is not found",
}
```

This endpoint deletes a specific order.

### HTTP Request

`DELETE https://api.solmate.cc/v2/orders/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the order to delete

# Notification

```json
{
  "id": "102341285566",
  "total_budget": 25000,
  "total_cost": 15566,
  "daily_budget": 2000,
  "daily_cost": 1781,
  "impressions": 30254,
  "clicks": 710,
  "clickthrough_rate": 0.37,
  "views": 1939,
  "view_rate": 0.08,
  "faces"
  "male": 198,
  "female": 469,
  "unknown": 1272,
  "age_18_24": 322,
  "age_25_34": 297,
  "age_35_44": 36,
  "age_45_54": 11,
  "age_55_64": 1,
  "age_65": 0,
  "face_25": 10,
  "face_26_50": 200,
  "face_51_75": 290,
  "face_76_100": 167,
}
```

The notification object includes following attributes.

### Notification object attributes

Attribute Name | Description
--------- | -----------
id | The ID of the order
total_budget | An amount that specify the maximum amount of budget spend over the period in which it runs.
total_cost | An amount that already spend over the period.
daily_budget | An amount that you set for each ad to spend each day.
daily_cost | An amount that you already spent each day.
hourly_cost | A
impressions | How many times your ads were shown to viewers.
clicks | Show you the number of times people clicked on your video.
clickthrough_rate | The number of clicks that your ad receives divided by the number of times your ad is shown.
views | Show the number of times people watched video ad.
view_rate | Show you the number of views divided by the number of times your ad is shown
male | How many male people watched video ad.
female | How many female people watched video ad.
age_18_24 | How many people age between 18 ~ 24 watched video ad.
age_25_34 | How many people age between 25 ~ 34 watched video ad.
age_35_44 | How many people age between 35 ~ 44 watched video ad.
age_45_54 | How many people age between 45 ~ 54 watched video ad.
age_65 | How many people age over 65 watched video ad.
0%-25% faces | shows how often a video is played to 0% ~ 25% of its length.
26%-50% views | shows how often a video is played to 26% ~ 50% of its length.
51%-75% views | shows how often a video is played to 51% ~ 75% of its length.
76%-100% views | shows how often a video is played to 76% ~ 100% of its length.
