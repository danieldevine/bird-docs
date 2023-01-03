---
title: Direct Messages
description: ''
position: 6
---

### Send a text only direct message

```php
$dms = $twitter->directMessages();

$dm = (new \Coderjerk\BirdElephant\Compose\DirectMessage)->text('Hello Buddy');

$dms->message($dm)->sendTo('spanish__eddie');
```

### Send a direct message with a media attachment

Send a DM with image to a named user - this is limited to one image only per message, see the Twitter docs for more about the limitations.

```php
$media = $dms->upload('./img/dth.jpg');

$text = 'Hi Dan, Bird Elephant has improved my life immeasurably. My interpersonal relationships are more fulfilling, my boss has given me a raise and my hair is thickening. I cannot wait to sponsor your project for a large sum of money.';

$message = (new \Coderjerk\BirdElephant\Compose\DirectMessage)->text($text)
    ->attachments($media->media_id_string);

$dm = $dms->message($message)->sendTo('coderjerk');

$conversation_id = $dm->data->dm_conversation_id;

```

`$dm` in this example will return a `data` object which contains `dm_conversation_id` and `dm_event_id`. You might want to store the conversation id to keep the conversation going using the `addToConversation()` method below, for example.

### Start a new group conversation with named participants.

With an attachment in this example.

```php

    $dms = $twitter->directMessages();

    $media = $dms->upload('./img/chris.png');

    $text = 'Hello To all of My Dear Friends, I solemnly pledge not to use this functionality for crypto spamming';

    $message = (new \Coderjerk\BirdElephant\Compose\DirectMessage)->text($text)->attachments($media->media_id_string);

    $participants = [
        'spanish__eddie',
        'coderjerk',
        'hank_in_hell'
    ];

    $dms->message($message)->newConversation($participants);

```

### Add a message to an existing conversation.
use a conversation id to add further messages.

```php
$text = 'While I respect your opinion, Bata Ilic is a far greater artist than Stefan Mross and anyone who believes otherwise needs to get their ears drained.';
$dm = (new \Coderjerk\BirdElephant\Compose\DirectMessage)->text($text);
$dms->message($dm)->addtoConversation($conversation_id);
```
### Retrieve an existing dm conversation by id
```php
$dms = $twitter->directMessages()->conversations()->find($conversation_id);
```
### Retrieve dm conversations with a named user

```php
 $dms = $twitter->directMessages()->conversations()->with('spanish__eddie');
 ```
### Retrieve all dm conversation events for the authenticated user
```php
 $dms = $twitter->directMessages()->conversations()->events();
 ```
