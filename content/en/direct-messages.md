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

$dm = (new \Coderjerk\BirdElephant\Compose\DirectMessage)->text($text)
    ->attachments($media->media_id_string);

$dms->message($dm)->sendTo('coderjerk');

```

### Start a new group conversation with named participants.

With an attachment in this example.

```php

    $dms = $twitter->directMessages();

    $media = $dms->upload('./img/chris.png');

    $text = 'Hello To all of My Dear Friends';

    $message = (new \Coderjerk\BirdElephant\Compose\DirectMessage)->text($text)->attachments($media->media_id_string);

    $participants = [
        'spanish__eddie',
        'coderjerk',
        'hank_in_hell'
    ];

    $dms->message($message)->newConversation($participants);

```
