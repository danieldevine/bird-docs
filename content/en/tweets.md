---
title: Tweets
description: ''
position: 1
---


```php
$twitter = new BirdElephant($credentials);

$tweets = $twitter->tweets();
```

### Tweet
Tweets a tweet object, with media or a poll. Can quote retweet and reply to tweets. See [Compose Tweets](/manage-tweets) for full implementation details and examples;

```php
$tweets->tweet($tweet);
```
| Name   | Type   | Description                                                 |          |
|--------|--------|-------------------------------------------------------------|----------|
| $tweet | object | The Tweet object - see [Manage Tweets](/manage-tweets) | required |

### Delete Tweet
Deletes a tweet on behalf of the authenticated user

```php
$tweets->delete($tweet_id);
```

| Name      | Type   | Description      |          |
|-----------|--------|------------------|----------|
| $tweet_id | String | The Tweet id     | required |

### Get Tweet
Gets a tweet

```php
$tweets->get($tweet_id, $params);
```
| Name    | Type   | Description      |          |
|---------|--------|------------------|----------|
| $tweet_id     | String | The Tweet id     | required |
| $params | Array  | Query Parameters | optional |


### Lookup Tweets
Gets multiple tweets

```php
$tweet_ids = [$id1,$id2]
$tweets->lookup($tweet_ids, $params);
```

| Name          | Type   | Description       |          |
|---------------|--------|-------------------|----------|
| $tweet_ids    | Array  | The Tweet ids     | required |
| $params       | Array  | Query Parameters  | optional |


### Count Recent Tweets
Gets  a count of Tweets that match a query in the last 7 days.

```php
$params = [
    'query' => 'Schlager',
];

$tweets->count()->recent($params);
```

| Name    | Type  | Description      |          |
|---------|-------|------------------|----------|
| $params | Array | Query Parameters | required |


### Count All Tweets
Gets a count of Tweets that match a query. Academic track only.

```php
$params = [
    'query' => 'Dieter Thomas Heck',
];

$tweets->count()->all($params);
```


| Name    | Type  | Description      |          |
|---------|-------|------------------|----------|
| $params | Array | Query Parameters | required |


### Search Recent Tweets

Search Tweets that match a query in the last 7 days.

```php
$params = [
    'query' => 'limerick has:images ',
    'tweet.fields' => 'attachments,author_id,created_at',
    'expansions'   => 'attachments.media_keys',
    'media.fields' => 'public_metrics,type,url,width',
    'max_results'  => 10,
];

$tweets->search()->recent($params);
```


| Name    | Type  | Description      |          |
|---------|-------|------------------|----------|
| $params | Array | Query Parameters | required |


### Search All Tweets
Search Tweets that match a query. Academic track only.

```php
$params = [
    'query' => 'Schlager has:images',
];

$tweets->search()->all($params);
```


| Name    | Type  | Description      |          |
|---------|-------|------------------|----------|
| $params | Array | Query Parameters | required |


### Hide Reply
Hide a reply to a tweet

```php
// note: you can't hide your own replies!!
$tweets->reply()->hide($id);
```

| Name    | Type   | Description      |          |
|---------|--------|------------------|----------|
| $id     | String | The Tweet id     | required |


### Unhide Reply
unhide a reply to a tweeet

```php
$tweets->reply()->unhide($id);
```

| Name | Type   | Description  |          |
|------|--------|--------------|----------|
| $id  | String | The Tweet id | required |


### Tweet Likers
Get the users who have liked a given tweet

```php
$tweets->likers($tweet_id, $params);
```


| Name    | Type   | Description      |          |
|---------|--------|------------------|----------|
| $tweet_id     | String | The Tweet id     | required |
| $params | Array  | Query Parameters | optional |


### Tweet Retweeters
Get the users who have liked a given tweet

```php
$tweets->retweeters($tweet_id, $params);
```


| Name    | Type   | Description      |          |
|---------|--------|------------------|----------|
| $tweet_id     | String | The Tweet id     | required |
| $params | Array  | Query Parameters | optional |
