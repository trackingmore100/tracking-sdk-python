Trackingmore-Python-sdk
=================

The Python SDK of Trackingmore API
## Official document

[Document](https://www.trackingmore.com/v3/api-index)

##Init

```
    apiKey = "you api Key"
    tracker = trackApi.TrackingApi(apiKey)
```

Quick Start
--------------
- Put your ApiKey in the constructor of the Api class
- All returns are in Json format.
- After instantiating the Api class, you can use its interface methods
- You can set the sandbox of the Api instance to true to turn on the sandbox mode: <code>tracker.sandbox=true;</code>
- Most Api params receive multiple tracking numbers

**Get a list of the couriers in Trackingmore**

	result = tracker.doRequest("carriers")
    print(json.loads(result.decode('utf-8')))

**Detect which couriers defined in your account match a tracking number**

	post = { "tracking_number": 'EA152563254CN' }
    postData = json.dumps(postData)
    result = tracker.doRequest("detect", post, "POST")
    print(json.loads(result.decode('utf-8')))


**Post trackings to your account**

    //Create single tracking numbers
    post_data  = {"tracking_number": "EA152563254CN", "courier": "china-ems"}
    //Create multiple tracking numbers
    postData = [{"tracking_number": "EA152563254CN", "courier": "china-ems"}, {"tracking_number": "EA152563254CN", "courier": "china-ems"}]
    postData = json.dumps(postData)
    result = tracker.doRequest("create", postData, "POST")
    print(json.loads(result.decode('utf-8')))

**Summary of Connection API Methods with all the api and Methods**

         # tracker.sandbox = True
    postData = [{"tracking_number": "EA152563254CN", "courier": "china-ems"}, {"tracking_number": "EA152563254CN", "courier": "china-ems"}]
    postData = json.dumps(postData)
    # Get realtime tracking results of a single tracking
    # post = {"tracking_number": "UB209300714LV", "courier": "cainiao"}
    # result = tracker.doRequest("realtime", json.dumps(post), "POST")
    # print(json.loads(result.decode('utf-8')))

    # count
    # count = "count?courier=1&limit=100&created_at_min=1521314361&created_at_max=1541314361"
    # result = tracker.doRequest(count)
    # print(json.loads(result.decode('utf-8')))

    # # Get tracking results of a  tracking or List all trackings
    # get = "get?page=1&limit=100&created_at_min=1521314361&created_at_max=1541314361"
    # result = tracker.doRequest(get)
    # print(json.loads(result.decode('utf-8')))

    # # Update Tracking item
    # result = tracker.doRequest("modifyinfo", postData, "PUT")
    # print(json.loads(result.decode('utf-8')))

    # # archive
    # result = tracker.doRequest("archive", postData, "POST")
    # print(json.loads(result.decode('utf-8')))

    # # Delete tracking item
    # result = tracker.doRequest("delete", postData, "DELETE")
    # print(json.loads(result.decode('utf-8')))

    # # create  tracking number
    # result = tracker.doRequest("create", postData, "POST")
    # print(json.loads(result.decode('utf-8')))

    # # manual update
    # result = tracker.doRequest("manualupdate", postData, "POST")
    # print(json.loads(result.decode('utf-8')))

    # # remote tracking
    # result = tracker.doRequest("remote", postData, "POST")
    # print(json.loads(result.decode('utf-8')))

    # # Get cost time iterm results
    # result = tracker.doRequest("transittime", postData, "POST")
    # print(json.loads(result.decode('utf-8')))

    # # detect a carriers by tracking number
    # post = { "tracking_number": 'EA152563254CN' }
    # post = json.dumps(post)
    # result = tracker.doRequest("detect", post, "POST")
    # print(json.loads(result.decode('utf-8')))

    # # get all carriers
    # result = tracker.doRequest("carriers")
    # print(json.loads(result.decode('utf-8')))

    # # Get status number
    # status = "status?tracking_number=EA152563254CN"
    # result = tracker.doRequest(status)
    # print(json.loads(result.decode('utf-8')))

    # # Set number not update
    # result = tracker.doRequest("notupdate", postData, "POST")
    # print(json.loads(result.decode('utf-8')))

    # # Modify courier code
    # post = {"tracking_number": "EA152563254CN", "courier": "china-ems", "new_express": "china-post"}
    # post = json.dumps(post)
    # result = tracker.doRequest("modifycourier", post, "PUT")
    # print(json.loads(result.decode('utf-8')))

## Typical Server Responses

We will respond with one of the following status codes.

Code|Type | Message
----|--------------|-------------------------------
200    | <code>Success</code>|    Request response is successful
203    | <code>PaymentRequired</code>|  API service is only available for paid account Please subscribe paid plan to unlock API services                                                             ul
204    | <code>No Content</code>|    Request was successful, but no data returned Tracking NO. or target data possibly do not exist
400    | <code>Bad Request</code>| Request type error Please check the API documentation for the request type of this API
401    | <code>Unauthorized</code>|    Authentication failed or has no permission Please check and ensure your API Key is correct
403    | <code>Bad Request</code>|    Page does not exist Please check and ensure your link is correct                                                                                             ul
404    | <code>Not Found</code>|    Page does not exist Please check and ensure your link is correct
408    | <code>Time Out</code>|    Request timeout The official website did not return data, please try again later
411    | <code>Bad Request</code>|    Specified request parameter length exceeds length limit Please check and ensure that the request parameters are of the required length
412    | <code>Bad Request</code>|    Specified request parameter format doesn't meet requirements Please check and ensure that the request parameters are in the required format
413    | <code>Out limited</code>|    The number of request parameters exceeds the limit Please check the API documentation for the limit of this API
417    | <code>Bad Request</code>|    Missing request parameters or request parameters cannot be parsed Please check and ensure that the request parameters are complete and correctly formatted
421    | <code>Bad Request</code>|    Some of required parameters are empty Some couriers need special parameters to track logistics information (Special Couriers)
422    | <code>Bad Request</code>|    Unidentifiable courier code Please check and ensure that the courier code are correct(Courier code)
423    | <code>Bad Request</code>|    Tracking No. already exists
424    | <code>Bad Request</code>|    Tracking No. no exists Please use 「Create trckings」 API first to create trackings
429    | <code>Bad Request</code>|    Exceeded API request limits, please try again later Please check the API documentation for the limit of this API
511    | <code>Server Error</code>|    Server error Please contact us: service@trackingmore.org.
512    | <code>Server Error</code>|    Server error Please contact us: service@trackingmore.org.
513    | <code>Server Error</code>|    Server error Please contact us: service@trackingmore.org.        