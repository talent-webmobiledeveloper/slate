---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript
  - shell
  - ruby
  - python  

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/talent-webmobiledeveloper/slate'>Documentation Powered by Vault</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to The Vault App Payment API. Through the API endpoints, Clients have the ability to initiate $ Requests and check $ Request statuses.

# Checkout 

## Checkout via API

> To checkout, use this code:

```javascript
  $.ajax({
    url:"https://api.thevaultapp.com/checkout",
    data:{
      token:{api_key},
      phone:{customer_phone_number},
      amount:{amount to checkout}
    },
    type:"POST"
  })

```

> Make sure to replace `api_key` with your API key.

TVA uses API keys to allow access to the API. You can register a new Vault API key at [https://www.thevaultapp.com/business/api](https://www.thevaultapp.com/business/api).

### HTTP Request

`POST https://api.thevaultapp.com/checkout`

<aside class="notice">
You must replace <code>api_key</code> with your personal API key.
</aside>
### Post Parameters

Parameter | Default | Description | Required
--------- | ------- | ----------- | ----------- 
token | empty | Registered the api key in the business/api.  | true
phone | empty | The customer phone number where the payment request is sent. | true
amount | empty | The payment amount to checkout | true


> The above command returns JSON structured like this:

```json
  {
    "status": "ok",
    "result": {
      "requestid":"829191sfwiwiw2923sf",
      "amount":10.44,
      "phone":"+12402211454",
      "employeeemail":"andrew.lidev@yandex.com",
      "status":"pending"
    },
    "code": 1,
  }
```

## Checkout by posting to The Vault App web server

> To checkout, use this code:

```javascript
  $.ajax({
    url:"https://www.thevaultapp.com/checkout/shopping",
    data:{
      _token:{api_key},
      phone:{customer_phone_number},
      amount:{amount to checkout}
    },
    type:"POST"
  })

```

> Make sure to replace `api_key` with your API key.

TVA uses API keys to allow access to the API. You can register a new Vault API key at [https://www.thevaultapp.com/business/api](https://www.thevaultapp.com/business/api).

<aside class="notice">
You must replace <code>api_key</code> with your personal API key.
</aside>
### Post Parameters

Parameter | Default | Description | Required
--------- | ------- | ----------- | ----------- 
token | empty | Registered the api key in the business/api.  | true
phone | empty | The customer phone number where the payment request is sent. | false
amount | empty | The payment amount to checkout | true


> The above command returns JSON structured like this:

```json
  {
    "status": "ok",
    "result": {
      "requestid":"829191sfwiwiw2923sf",
      "amount":10.44,
      "phone":"+12402211454",
      "employeeemail":"andrew.lidev@yandex.com",
      "status":"pending"
    },
    "code": 1,
  }
```

<aside class="notice">
   If the <code>phone</code> is empty, it will redirect to a TVA web form to input a phone number. After approving or denying the request, the last status page will say the request status.
</aside>

# Query

## Get Status of the payment request


```javascript
  $.ajax({
    url:"https://api.thevaultapp.com/checkout/query/{request_id}",
    data:{
      token:{api_key}
    },
    type:"POST"
  }).done(function(response, status){
    //Process api calling success
  }).fail(function(response, status){
    //Process api calling fail
  })
```

> The above command returns JSON structured like this:

```json
  {
    "status":"ok",
    "result":{
      "id": "9ss023swowflwsow293023",
      "status":"Approved"
    },
    "code":1
  }
```

This endpoint retrieves status of the request.

### HTTP Request

`POST https://api.thevaultapp.com/checkout/query/{request_id}`

### Query Parameters

Parameter | Default | Description | Reuqired 
--------- | ------- | ----------- | ------------
request_id | empty | The request id gotten from the checkout api. | true

### Post Parameters

Parameter | Default | Description | Reuqired 
--------- | ------- | ----------- | ------------
token | empty | Registered the api key in the business/api.  | true


<aside class="success">
Remember — if token is unset, the api would not work properly.
</aside>



