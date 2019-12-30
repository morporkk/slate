# Pagination

For all device requests that return more than a single record pagination is provided. This can be used by sending the following query parameters.
Pagination data and links are in headers, not in response body.

### URL Parameters

Parameter | Description
--------- | -----------
page      | The current page offset. Defaults to 1
per_page  | The total number of objects that can be returned. Defaults to 30
