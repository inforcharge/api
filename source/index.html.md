---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - ruby
  - python
  - javascript

toc_footers:
  - <a href='https://solmate.cc'>Solmate Home</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Solmate API! You can use our API to access Solmate API endpoints, which can CRUD orders, webhook in our database.

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
    # Request
    # GET https://echo.paw.cloud/

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

> Make sure to replace `Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl` with your API key.

Solmate uses HTTP Basic Auth to allow access to the API.

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
            "network" => "VIESHOW",
            "model" => "CPM",
            "total_budget" => "20000",
            "daily_budget" => "2000",
            "material_url" => "https://cdn.solmate.cc/uploads/ad/display_file/886/4e144283de.mp4"
            "click_url" => "https://cdn.solmate.cc/uploads/ad/trigger_file/886/cc68227be5.jpg",
            "display_time" => "30",
            "gender" => "",
            "districts" => ["台北信義市府", "台北士林天母"],
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
                "network": "VIESHOW",
                "total_budget": "20000",
                "daily_budget": "2000",
                "material_url": "https://cdn.solmate.cc/uploads/ad/display_file/886/4e144283de.mp4"
                "click_url": "https://cdn.solmate.cc/uploads/ad/trigger_file/886/cc68227be5.jpg",
                "model": "CPM",
                "display_time": "30",
                "gender": "",
                "districts": ["台北信義市府", "台北士林天母"],
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
  "network": "VIESHOW",
  "model": "CPM",
  "total_budget": "20000",
  "daily_budget": "2000",
  "material_url": "https://cdn.solmate.cc/uploads/ad/display_file/886/4e144283de.mp4"
  "click_url": "https://cdn.solmate.cc/uploads/ad/trigger_file/886/cc68227be5.jpg",
  "display_time": "30",
  "gender": "",
  "districts": ["台北信義市府", "台北士林天母"],
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
        "network": "VIESHOW",
        "model": "CPM",
        "total_budget": "20000",
        "daily_budget": "2000",
        "material_url": "https://cdn.solmate.cc/uploads/ad/display_file/886/4e144283de.mp4"
        "click_url": "https://cdn.solmate.cc/uploads/ad/trigger_file/886/cc68227be5.jpg",
        "display_time": "30",
        "gender": "",
        "districts": ["台北信義市府", "台北士林天母"],
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

> The above command returns JSON structured like this:

```json
{
  "status": "ok",
  "id": "102341285566",
}

{
  "status": "failed",
  "message": "model should not be empty",
}
```

This endpoint creates a new order.

### HTTP Request

`POST https://api.solmate.cc/v2/orders`

### POST Parameters

Parameter | Default | Description
--------- | ------- | -----------
title | (must have) | AD title
network | (must have) | `VIESHOW`, `SALON`, `COFFEE_RESTAURANT`
model | (must have) | `CPM`, `CPV`
total_budget | (must have) | must larger than 0
daily_budget | (must have) | must larger than 0
material_url | (must have) | material url link like, https://cdn.solmate.cc/uploads/ad/display_file/886/4e144283de.mp4
click_url | (must have) | click material url link like, https://cdn.solmate.cc/uploads/ad/trigger_file/886/cc68227be5.jpg
display_time | (optional) | default is 30 seconds.
gender | (optional) | Empty string is no limit. `MALE`, `FEMALE`
districts | (optional) | Empty array is no limit. <ul><li>台北中山大同</li><li>台北信義安和</li><li>台北信義市府</li><li>台北南京八德</li><li>台北士林天母</li><li>台北大直內湖</li><li>台北師大公館</li><li>台北忠孝東路</li><li>台北木柵政大</li><li>台北東門永康</li><li>台北松江南京</li><li>台北民生民權</li><li>台北永春南港</li><li>台北西門艋舺</li><li>新北三重蘆洲</li><li>新北中和永和</li><li>新北新莊泰山</li><li>新北板橋土城</li><li>新北汐止車站</li><li>桃園中壢市區</li><li>新竹市區</li><li>台中市區</li><li>台南市區</li><li>高雄市區</li><li>台北景美新店</li><li>新竹車站市區</li><li>苗栗頭份市區</li><li>桃園車站市區</li><li>台北中正站前</li><li>宜蘭車站市區</li><li>屏東市區</li><li>其他</li></ul>


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
            "model" => "CPM",
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
                "model": "CPM",
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
  "model": "CPM",
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
        "model": "CPM",
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

> The above command returns JSON structured like this:

```json
{
  "status": "ok",
  "id": "102341285566",
}

{
  "status": "failed",
  "message": "model should not be empty",
}
```

This endpoint update a specific order.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`PUT https://api.solmate.cc/v2/orders/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the order to retrieve

### Available Change Parameters

Parameter | Default | Description
--------- | ------- | -----------
total_budget | (must have) | must larger than 0
daily_budget | (must have) | must larger than 0
material_url | (must have) | material url link like, https://cdn.solmate.cc/uploads/ad/display_file/886/4e144283de.mp4
click_url | (must have) | click material url link like, https://cdn.solmate.cc/uploads/ad/trigger_file/886/cc68227be5.jpg
display_time | (optional) | default is 30 seconds.
gender | (optional) | Empty string is no limit. `MALE`, `FEMALE`
districts | (optional) | Empty array is no limit. <ul><li>台北中山大同</li><li>台北信義安和</li><li>台北信義市府</li><li>台北南京八德</li><li>台北士林天母</li><li>台北大直內湖</li><li>台北師大公館</li><li>台北忠孝東路</li><li>台北木柵政大</li><li>台北東門永康</li><li>台北松江南京</li><li>台北民生民權</li><li>台北永春南港</li><li>台北西門艋舺</li><li>新北三重蘆洲</li><li>新北中和永和</li><li>新北新莊泰山</li><li>新北板橋土城</li><li>新北汐止車站</li><li>桃園中壢市區</li><li>新竹市區</li><li>台中市區</li><li>台南市區</li><li>高雄市區</li><li>台北景美新店</li><li>新竹車站市區</li><li>苗栗頭份市區</li><li>桃園車站市區</li><li>台北中正站前</li><li>宜蘭車站市區</li><li>屏東市區</li><li>其他</li></ul>


## Get Order Status



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
            "action" => "pause"
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
                "action": "pause"
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
  "action": "pause"
}'
```

```javascript
jQuery.ajax({
    url: "https://api.solmate.cc/v2/orders/102341285566/status",
    type: "PUT",
    headers: {
        "Authorization": "Basic YXBpQHNvbG1hdGUuY2M6SWxvdmVzb2xtYXRl",
        "Content-Type": "application/json; charset=utf-8",
        "Cookie": "__cfduid=d75037cf56267b659fb34c09ccac7009d1533181575",
    },
    contentType: "application/json",
    data: JSON.stringify({
        "action": "pause"
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

> The above command returns JSON structured like this:

```json
{
  "status" : "ok"
}

{
  "status" : "failed",
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
action | (must have) | `pause`, `resume`

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

> The above command returns JSON structured like this:

```json
{
  "status" : "ok"
}

{
  "status" : "failed",
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
