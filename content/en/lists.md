---
title: Lists
description: ''
position: 3
---
#### Method:  ```lists()```

Twitter Lists allows users to customize, organize and prioritize the Tweets they see in their timeline.

```php
$twitter = new BirdElephant($credentials);

$lists = $twitter->lists()
```
## Manage Lists

### Get List

#### Method: ```get()```

Gets a Twitter list.

```php
$lists->get($list_id, $params);
```
###### Auth: OAuth 2.0 Bearer token

| Argument | Type  | Description  |          |
|----------|-------|------------------------------------------------------------------------------------|----------|
| $list_id  | String | The id of the list | optional |
| $params  | Array | [available query parameters](https://developer.twitter.com/en/docs/twitter-api/lists/list-lookup/api-reference/get-lists-id) | optional |

### Create List
#### Method: ```create()```

Create a new list on behalf of the authenticated user

```php
$lists->create($list_name = 'Cool List', $list_description = 'testing', $private = false);
```

###### Auth: OAuth 1.0a User context

 | Argument         | Type   | Description                                             |          |
 |------------------|--------|---------------------------------------------------------|----------|
 | $list_name       | string | The name of the list                                    | required |
 | $list_description| string | Description of the list                                 | optional |
 | $private         | bool   | If the list is private or not. Defaults to false.       | optional |

### Update List
#### Method: ```update()```

Update an existing list on behalf of the authenticated user

```php
$lists->update($list_id, $list_name, $list_description, $private);
```

###### Auth: OAuth 1.0a User context

 | Argument          | Type   | Description                                       |          |
 |-------------------|--------|---------------------------------------------------|----------|
 | $list_id          | string | The id of the list                                | required |
 | $list_name        | string | The name of the list                              | optional |
 | $list_description | string | Description of the list                           | optional |
 | $private          | bool   | If the list is private or not. Defaults to false. | optional |


### Delete List
#### Method: ```delete()```

Delete a list owned by the authenticated user

```php
$lists()->delete($list_id);
```

###### Auth: OAuth 1.0a User context

 | Argument          | Type   | Description                                       |          |
 |-------------------|--------|---------------------------------------------------|----------|
 | $list_id          | string | The id of the list                                | required |

## List Members
#### Method: ```members()```
```php
$members = $lists->members();
```

### Get List Members
#### Method: ```lookup()```

Gets the members of a given list

```php
$members()->lookup($list_id, $params);
```
###### Auth: OAuth 2.0 Bearer token
 | Argument   | Type   | Description                                    |          |
 |------------|--------|------------------------------------------------|----------|
 | $list_id   | string | The id of the list                             | required |
 | $params    | Array  | see Twitter docs for avilable query parameters | optional |


### Add List Member
#### Method: ```add()```

Add a member to a list

```php
$members->add($list_id, $user_name);
```
###### Auth: OAuth 1.0a User context
 | Argument | Type   | Description        |          |
 |----------|--------|--------------------|----------|
 | $list_id | string | The id of the list | required |
 | $user_name     | string | the twitter user name of the list member           | required|

### Remove List Member
#### Method: ```remove()```

Remove a member from a list

```php
$members->remove($list_id, $user_name);
```

###### Auth: OAuth 1.0a User context
 | Argument   | Type   | Description                               |          |
 |------------|--------|-------------------------------------------|----------|
 | $list_id   | string | The id of the list                        | required |
 | $user_name | string | the twitter user name of the list member  | required |

## List Follows
#### Method: ```follows()```
```php
$follows = $lists->follows();
```

### Get List Follows
#### Method: ```lookup()```

Gets the followers of a given list

```php
$follows->lookup($list_id, $params);
```
###### Auth: OAuth 2.0 Bearer token
 | Argument | Type   | Description                                    |          |
 |----------|--------|------------------------------------------------|----------|
 | $list_id | string | The id of the list                             | required |
 | $params  | Array  | see Twitter docs for avilable query parameters | optional |



## List Tweets
#### Method: ```tweets()```
```php
$tweets = $lists->tweets();
```

### Lookup List Tweets
#### Method: ```lookup()```

Retrieves Tweets from a specified List

```php
$tweets->lookup($list_id, $params);
```
###### Auth: OAuth 2.0 Bearer token
 | Argument | Type   | Description                                    |          |
 |----------|--------|------------------------------------------------|----------|
 | $list_id | string | The id of the list                             | required |
 | $params  | Array  | [see Twitter docs for avilable query parameters](https://developer.twitter.com/en/docs/twitter-api/lists/list-tweets/api-reference/get-lists-id-tweets) | optional |

## Reference
- [Twitter API Lists Reference](https://developer.twitter.com/en/docs/twitter-api/lists/manage-lists/api-reference)

