---
title: Spaces
description: ''
position: 5
---
#### Method:  ```spaces()```

Spaces allow expression and interaction via live audio conversation.

```php
$twitter = new BirdElephant($credentials);

$spaces = $twitter->spaces()->lookup();
```

### Get a Space
#### Method: `getSpace()`
Lookup a space by id
```php
$spaces->getspace($space_id, $params);
```
| Argument  | Type   | Description                                    |          |
|-----------|--------|------------------------------------------------|----------|
| $space_id | String | The Space Id                                   | required |
| $params   | Array  | see Twitter docs for avilable query parameters | optional |

### Get Multiple Spaces

#### Method: `getSpaces()`
Look up multiple spaces by id
```php
$spaces->getspaces($space_ids, $params);
```
| Argument   | Type  | Description                                    |          |
|------------|-------|------------------------------------------------|----------|
| $space_ids | Array | The Space Ids                                  | required |
| $params    | Array | see Twitter docs for avilable query parameters | optional |

### Discover Spaces

#### Method: `discover()`
lookup live or scheduled Spaces created by the specified user IDs
```php
$spaces->discover($creator_ids, $params);
```
| Argument  | Type  | Description                                    |          |
|-----------|-------|------------------------------------------------|----------|
| $creator_ids | Array | Creator user Ids                                       | required |
| $params   | Array | See Twitter docs for avilable query parameters | optional |

### View Buyers

#### Method: `buyers()`

Returns a list of user who purchased a ticket to the
requested Space. You must authenticate the request using
the Access Token of the creator of the requested Space.

```php
$spaces->buyers($space_id, $params);
```
| Argument  | Type   | Description                                    |          |
|-----------|--------|------------------------------------------------|----------|
| $space_id | String | The Space Id                                   | required |
| $params   | Array  | see Twitter docs for avilable query parameters | optional |


### Examples

```php
use Coderjerk\BirdElephant\BirdElephant;

$twitter = new BirdElephant($credentials);

//lookup a space by space id

$params = [
    'space.fields' => 'creator_id, id,  invited_user_ids, participant_count, speaker_ids',
    'user.fields' => 'description, entities, id, location, name, pinned_tweet_id, profile_image_url'
]

$space = $twitter->spaces()->lookup()->getspace($space_id, $params);

// lookup multiple spaces by id
$space_ids = [
    $space_id_1,
    $space_id_2
];

$spaces = $twitter->spaces()->lookup()->getspaces($space_ids, $params);

// lookup live or scheduled Spaces created by the specified user IDs
$creator_ids = [
    $creator_id_1,
    $creator_id_1
];

$spaces = $twitter->spaces()->lookup()->discover($creator_ids, $params);
```

### Reference
- [Spaces](https://developer.twitter.com/en/docs/twitter-api/spaces/overview)
- [Twitter API Spaces Lookup Reference](https://developer.twitter.com/en/docs/twitter-api/spaces/lookup/api-reference)
- [Twitter API Search Spaces Reference](https://developer.twitter.com/en/docs/twitter-api/spaces/search/api-reference/get-spaces-search)
