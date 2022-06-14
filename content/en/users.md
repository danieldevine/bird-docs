---
title: Users
description: ''
position: 2
---
Returns information about a user or group of users

## Twitter Users
#### Method: ```users()```
Returns information about a group of users

```php
$twitter = new BirdElephant($credentials);

$users = $twitter->users()
```
### Lookup Users
#### Method: ```lookup()```

Looks up multiple twitter users by username

```php
$usernames = ['coderjerk', 'kennyg', 'dril'];

$params = [
    'expansions' => 'pinned_tweet_id',
    'user.fields' =>  'created_at,description,entities,id,location'
];

$users->lookup($usernames, $params);
```
###### Auth: OAuth 2.0 Bearer token
| Argument    | Type  | Description                                    |          |
|-------------|-------|------------------------------------------------|----------|
| $usernames  | Array | array of Twitter usernames                     | required |
| $params     | Array | [available query parameters](https://developer.twitter.com/en/docs/twitter-api/users/lookup/api-reference/get-users-by-username-username) | optional |



## Twitter User
#### Method: ```user()```

Sets up a Twitter user by user name to be used in conjunction with the methods below to perform actions on behalf of and retrieve data about the named user. The named user must be the authenticated user in instances where user context auth is required.

```php
$twitter = new BirdElephant($credentials);

$user = $twitter->user($user_name);
```
###### Auth: OAuth 2.0 Bearer token
| Argument   | Type   | Description                                    |          |
|------------|--------|------------------------------------------------|----------|
| $user_name | String | Twitter username                               | required |

### Get User
#### Method: ```get()```

Gets information about the named Twitter user.

```php
$user->get();
```
###### Auth: OAuth 2.0 Bearer token

| Argument   | Type   | Description                                    |          |
|------------|--------|------------------------------------------------|----------|
| $params    | Array  | [available query parameters](https://developer.twitter.com/en/docs/twitter-api/users/lookup/api-reference/get-users-id)                   | optional |

### Get Followers
#### Method: ```followers()```

Gets a Twitter user's followers

```php
$user->followers();
```
###### Auth: OAuth 2.0 Bearer token
| Argument | Type  | Description                                    |          |
|----------|-------|------------------------------------------------|----------|
| $params  | Array | [available query parameters](https://developer.twitter.com/en/docs/twitter-api/users/follows/api-reference)                            | optional |

### Get Following
#### Method: ```following()```

Gets a Twitter user's followed accounts
```php
$params= [
    'max_results' => 20,
    'user.fields' => 'profile_image_url'
];

$user->following($params);
```
###### Auth: OAuth 2.0 Bearer token
| Argument | Type  | Description                                    |          |
|----------|-------|------------------------------------------------|----------|
| $params  | Array | [available query parameters](https://developer.twitter.com/en/docs/twitter-api/users/follows/api-reference)                            | optional |

### Follow
#### Method: ```follow()```

Follows a given user

```php
$user->follow('coderjerk');
```
###### Auth: OAuth 1.0a User context

| Argument         | Type  | Description                            |          |
|------------------|-------|----------------------------------------|----------|
| $target_username | String| The target twitter username            | required |

### Unfollow
#### Method: ```unfollow()```

Unfollows a given user

```php
$user->unfollow('stefanmross');
```
###### Auth: OAuth 1.0a User context

| Argument         | Type  | Description                 |          |
|------------------|-------|-----------------------------|----------|
| $target_username | String| The target twitter username | required |

### User Tweets
#### Method: ```tweets()```

Gets the tweets of a Twitter user.

```php
$user->tweets();
```
###### Auth: OAuth 2.0 Bearer token

| Argument | Type  | Description                                    |          |
|----------|-------|------------------------------------------------|----------|
| $params  | Array | see Twitter docs for avilable query parameters | optional |

### Mentions
#### Method: ```mentions()```

Gets the mentions of a Twitter user.

```php
$user->mentions();
```
###### Auth: OAuth 2.0 Bearer token

| Argument | Type  | Description                                    |          |
|----------|-------|------------------------------------------------|----------|
| $params  | Array | see Twitter docs for avilable query parameters | optional |

### User Blocks
#### Method: ```blocks()```

Gets the blocked accounts of a Twitter user.

```php
$user->blocks();
```
###### Auth: OAuth 1.0a User context

| Argument | Type  | Description                                    |          |
|----------|-------|------------------------------------------------|----------|
| $params  | Array | see Twitter docs for avilable query parameters | optional |

### Block User
#### Method: ```block()```

Blocks a given user

```php
$user->block('GilbertOSull_');
```
###### Auth: OAuth 1.0a User context
| Argument         | Type  | Description                 |          |
|------------------|-------|-----------------------------|----------|
| $target_username | String| The target twitter username | required |

### Unblock User
#### Method: ```unblock()```

Unblocks a given user

```php
$user->unblock('claydermanmusic');
```
###### Auth: OAuth 1.0a User context

| Argument         | Type  | Description                 |          |
|------------------|-------|-----------------------------|----------|
| $target_username | String| The target twitter username | required |

### User Mutes
#### Method: ```mutes()```

Gets the muted accounts of a Twitter user.

```php
$user->mutes();
```
###### Auth: OAuth 1.0a User context

| Argument | Type  | Description                                    |          |
|----------|-------|------------------------------------------------|----------|
| $params  | Array | see Twitter docs for avilable query parameters | optional |

### Mute User
#### Method: ```mute()```

Mutes a given user

```php
$user->mute('kennyg');
```
###### Auth: OAuth 1.0a User context

| Argument         | Type  | Description                 |          |
|------------------|-------|-----------------------------|----------|
| $target_username | String| The target twitter username | required |

### Unmute User
#### Method: ```unmute()```

Unmutes a given user

```php
$user->unmute('kennyg');
```
###### Auth: OAuth 1.0a User context

| Argument         | Type  | Description                 |          |
|------------------|-------|-----------------------------|----------|
| $target_username | String| The target twitter username | required |

### User Likes
#### Method: ```likes()```

Gets the named user's last 100 likes

```php
$user->likes($params);
```
###### Auth: OAuth 1.0a User context

| Argument | Type  | Description                                    |          |
|----------|-------|------------------------------------------------|----------|
| $params  | Array | see Twitter docs for avilable query parameters | optional |

### Like Tweet
#### Method: ```like()```

Likes a tweet on behalf of the authenticated user

```php
$user->like('1456978214837006343');
```
###### Auth: OAuth 1.0a User context

| Argument | Type  | Description                                    |          |
|----------|-------|------------------------------------------------|----------|
| $tweet_id  | String | the target tweet id | reqired |

### Unlike Tweet
#### Method: ```unlike()```

Unlikes a tweet on behalf of the authenticated user

```php
$user->unlike($tweet_id);
```
###### Auth: OAuth 1.0a User context

| Argument  | Type   | Description         |          |
|-----------|--------|---------------------|----------|
| $tweet_id | String | the target tweet id | required |

### Retweet
#### Method: ```retweet()```

Retweets a tweet on behalf of the authenticated user

```php
$user->retweet('1456978214837006343');
```
###### Auth: OAuth 1.0a User context
| Argument  | Type   | Description         |          |
|-----------|--------|---------------------|----------|
| $tweet_id | String | the target tweet id | required |

### Unretweet
#### Method: ```unretweet()```

Unretweets a tweet on behalf of the authenticated user

```php
$user->unretweet($tweet_id);
```
###### Auth: OAuth 1.0a User context

| Argument  | Type   | Description         |          |
|-----------|--------|---------------------|----------|
| $tweet_id | String | the target tweet id | required |

### User Spaces
#### Method: ```spaces()```

Gets a user's spaces

```php
$user->spaces();
```
###### Auth: OAuth 2.0 Bearer token

| Argument | Type  | Description                                    |          |
|----------|-------|------------------------------------------------|----------|
| $params  | Array | see Twitter docs for avilable query parameters | optional |

## User Lists
#### Method: ```lists()```

Perform actions on lists on behalf of the authenticated user.

```php
$user_lists = $user->lists();
```

### Get Followed Lists
#### Method: ```followed()```

Gets a list of folllowed lists on behalf of the authenticated user

```php
$user_lists->followed($params);
```
###### Auth: OAuth 1.0a User context

| Argument | Type  | Description                                    |          |
|----------|-------|------------------------------------------------|----------|
| $params  | Array | see Twitter docs for avilable query parameters | optional |

### Get Pinned Lists
Gets a list of pinned lists on behalf of the authenticated user

```php
$user_lists->pinned($params);
```
###### Auth: OAuth 1.0a User context

| Argument | Type  | Description                                    |          |
|----------|-------|------------------------------------------------|----------|
| $params  | Array | see Twitter docs for avilable query parameters | optional |

### Get Owned Lists
Gets lists owned by the authenticated user

```php
$user_lists->owned($params);
```
###### Auth: OAuth 1.0a User context

| Argument | Type  | Description                                    |          |
|----------|-------|------------------------------------------------|----------|
| $params  | Array | see Twitter docs for avilable query parameters | optional |

### Follow Lists
Follows a list on behalf of the authenticated user

```php
$user_lists->follow($target_list_id);
```
###### Auth: OAuth 1.0a User context

| Argument         | Type  | Description                 |          |
|------------------|-------|-----------------------------|----------|
| $target_list_id | String | The target list id          | required |

### Unfollow Lists
Unfollows a list on behalf of the authenticated user

```php
$user_lists->unfollow($target_list_id);
```
###### Auth: OAuth 1.0a User context

| Argument        | Type   | Description        |          |
|-----------------|--------|--------------------|----------|
| $target_list_id | String | The target list id | required |

### Pin  Lists
Unpins a list on behalf of the authenticated user

```php
$user_lists->pin($target_list_id);
```
###### Auth: OAuth 1.0a User context

| Argument        | Type   | Description        |          |
|-----------------|--------|--------------------|----------|
| $target_list_id | String | The target list id | required |

### Unpin Lists
Pins a list on behalf of the authenticated user

```php
$user_lists->unpin($target_list_id);
```
###### Auth: OAuth 1.0a User context

| Argument        | Type  | Description         |          |
|-----------------|-------|---------------------|----------|
| $target_list_id | String | The target list id | required |


## Me
#### Method: ```me()```
Get the authenticated user

```php
$twitter = new BirdElephant($credentials);

$me = $twitter->me()
```
#### Method: ```myself()```

Gets information about the authenticated user.

```php

$params = [
    'expansions' => 'pinned_tweet_id',
];

$me->myself($params);
```
###### Auth: OAuth 1.0a User context
| Argument | Type  | Description                                                                                                             |          |
|----------|-------|-------------------------------------------------------------------------------------------------------------------------|----------|
| $params  | Array | [available query parameters](https://developer.twitter.com/en/docs/twitter-api/users/lookup/api-reference/get-users-me) | optional |



## Reference
Refer to the Twitter documentation for details of paramaters, expansions and fields.
- [User Lookup](https://developer.twitter.com/en/docs/twitter-api/users/lookup/api-reference)
- [Follows](https://developer.twitter.com/en/docs/twitter-api/users/follows/api-reference)
- [Blocks](https://developer.twitter.com/en/docs/twitter-api/users/blocks/api-reference)
- [Mutes](https://developer.twitter.com/en/docs/twitter-api/users/mutes/api-reference)
