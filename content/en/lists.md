---
title: Lists
description: ''
position: 3
---

Twitter Lists allows users to customize, organize and prioritize the Tweets they see in their timeline.

### Methods

#### `create()`
Create a new list on behalf of the authenticated user
###### Auth: OAuth 1.0a User context

 | Argument         | Type   | Description                                             |          |
 |------------------|--------|---------------------------------------------------------|----------|
 | $list_name       | string | The name of the list                                    | required |
 | $list_description| string | Description of the list                                 | optional |
 | $private         | bool   | If the list is private or not. Defaults to false.       | optional |

#### `update()`
Update an existing list on behalf of the authenticated user
###### Auth: OAuth 1.0a User context

 | Argument          | Type   | Description                                       |          |
 |-------------------|--------|---------------------------------------------------|----------|
 | $list_id          | string | The id of the list                                | required |
 | $list_name        | string | The name of the list                              | optional |
 | $list_description | string | Description of the list                           | optional |
 | $private          | bool   | If the list is private or not. Defaults to false. | optional |


#### `delete()`
Delete a list n behalf of the authenticated user
###### Auth: OAuth 1.0a User context

 | Argument          | Type   | Description                                       |          |
 |-------------------|--------|---------------------------------------------------|----------|
 | $list_id          | string | The id of the list                                | required |


#### `members()->add()`
Add a member to a list
###### Auth: OAuth 1.0a User context
 | Argument | Type   | Description        |          |
 |----------|--------|--------------------|----------|
 | $list_id | string | The id of the list | required |
 | $user_name     | string | the twitter user name of the list member           | required|

#### `members()->remove()`
Remove a member from a list
###### Auth: OAuth 1.0a User context
 | Argument   | Type   | Description                               |          |
 |------------|--------|-------------------------------------------|----------|
 | $list_id   | string | The id of the list                        | required |
 | $user_name | string | the twitter user name of the list member | required |

### Reference
- [Twitter API Lists Reference](https://developer.twitter.com/en/docs/twitter-api/lists/manage-lists/api-reference)

### Examples

```php
use Coderjerk\BirdElephant\BirdElephant;

$twitter = new BirdElephant($credentials);

//create a list
$list = $twitter->lists()->create($list_name = 'Cool List', $list_description = 'testing', $private = false);

//update a list
$list = $twitter->lists()->update($list_id, $list_name, $list_description, $private);

//add a member to a list
$member = $twitter->lists()->members()->add($list_id, $user_name);

//remove a member from a list
$dismember = $twitter->lists()->members()->remove($list_id, $user_name);
```
