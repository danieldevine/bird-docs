---
title: Lists
description: ''
position: 3
---

Twitter Lists allows users to customize, organize and prioritize the Tweets they see in their timeline.

### Get List
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
Create a new list on behalf of the authenticated user

```php
use Coderjerk\BirdElephant\BirdElephant;

$twitter = new BirdElephant($credentials);

$twitter->lists()->create($list_name = 'Cool List', $list_description = 'testing', $private = false);
```

###### Auth: OAuth 1.0a User context

 | Argument         | Type   | Description                                             |          |
 |------------------|--------|---------------------------------------------------------|----------|
 | $list_name       | string | The name of the list                                    | required |
 | $list_description| string | Description of the list                                 | optional |
 | $private         | bool   | If the list is private or not. Defaults to false.       | optional |

### Update List
Update an existing list on behalf of the authenticated user

```php
$list = $twitter->lists()->update($list_id, $list_name, $list_description, $private);
```

###### Auth: OAuth 1.0a User context

 | Argument          | Type   | Description                                       |          |
 |-------------------|--------|---------------------------------------------------|----------|
 | $list_id          | string | The id of the list                                | required |
 | $list_name        | string | The name of the list                              | optional |
 | $list_description | string | Description of the list                           | optional |
 | $private          | bool   | If the list is private or not. Defaults to false. | optional |


### Delete List
Delete a list owned by the authenticated user

```php
$member = $twitter->lists()->delete($list_id);
```

###### Auth: OAuth 1.0a User context

 | Argument          | Type   | Description                                       |          |
 |-------------------|--------|---------------------------------------------------|----------|
 | $list_id          | string | The id of the list                                | required |

### Get List Members
Gets the members of a given list

```php
$twitter->lists()->members()->lookup($list_id, $params);
```
###### Auth: OAuth 2.0 Bearer token
 | Argument   | Type   | Description                                    |          |
 |------------|--------|------------------------------------------------|----------|
 | $list_id   | string | The id of the list                             | required |
 | $params    | Array  | see Twitter docs for avilable query parameters | optional |


### Add List Member
Add a member to a list

```php
$member = $twitter->lists()->members()->add($list_id, $user_name);
```
###### Auth: OAuth 1.0a User context
 | Argument | Type   | Description        |          |
 |----------|--------|--------------------|----------|
 | $list_id | string | The id of the list | required |
 | $user_name     | string | the twitter user name of the list member           | required|

### Remove List Member
Remove a member from a list

```php
$dismember = $twitter->lists()->members()->remove($list_id, $user_name);
```

###### Auth: OAuth 1.0a User context
 | Argument   | Type   | Description                               |          |
 |------------|--------|-------------------------------------------|----------|
 | $list_id   | string | The id of the list                        | required |
 | $user_name | string | the twitter user name of the list member  | required |

 ### Get List Follows
Gets the followers of a given list

```php
$twitter->lists()->follows()->lookup($list_id, $params);
```
###### Auth: OAuth 2.0 Bearer token
 | Argument | Type   | Description                                    |          |
 |----------|--------|------------------------------------------------|----------|
 | $list_id | string | The id of the list                             | required |
 | $params  | Array  | see Twitter docs for avilable query parameters | optional |

## Reference
- [Twitter API Lists Reference](https://developer.twitter.com/en/docs/twitter-api/lists/manage-lists/api-reference)



