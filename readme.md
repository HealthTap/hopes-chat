Rich Text Protocol
===

## Rich Text

### ACTOR
```js
{
    type: "user",
    data: {username: "xxx"}
}
```
```js
{
    type: "system"
}
```
```js
{
    type: "room",
    data: {id: "xxx", tags: ["provider"]}
}
```

### text
```js
{
    "type": "text",
    "payload": {
        "text": "This is a Message",
    },
    "inline": BOOLEAN,
}
```

### image
```js
{
    "type": "image",
    "payload": {
        "name": 'selfie.png',
        "title": 'my selfie',
        "description": 'selfie for myself',
        "size": 10000,
        "thumbnail": 'https://xx.xx.xx/files/thumbnails/selfie.png',
        "url": "https://xx.xx.xx/selfie.png",
    },
}
```

### video
```js
{
    "type": "video",
    "payload": {
        "name": 'yosemite.mp4',
        "title": 'Yosemite',
        "description": 'My trip to Yosemite in 2014',
        "size": 1000000,
        "thumbnail": 'https://xx.xx.xx/files/thumbnails/yosemite.png',
        "url": "https://xx.xx.xx/yosemite.mp4",
    },
}
```

### audio
```js
{
    "type": "audio",
    "payload": {
        "name": 'yosemite.mp3',
        "title": 'voice 2015',
        "description": 'my voice in 2014',
        "trancription": 'I love yosemite', # server might transcribe the audio
        "size": 10000,
        "thumbnail": 'https://xx.xx.xx/files/thumbnails/mp4.png',
        "url": "https://xx.xx.xx/my_voice.mp3",
    },
}
```

### file
```js
{
    "type": "file",
    "payload": {
        "name": 'test.pdf',
        "title": 'my prescription',
        "description": 'prescription issued two days ago',
        "size": 100,
        "thumbnail": 'https://xx.xx.xx/files/thumbnails/pdf.png',
        "url": "https://xx.xx.xx/test.pdf",
    },
}
```
### location
```js
{
    "type": "location",
    "payload": {
        "coordinates": {
            "lat": LAT,
            "long": LONG,
        }
    },
}
```

### sticker
```js
{
    "type": "sticker",
    "payload": {
        "sticker_id": STICKER_ID, # [ThumbUp, FeelGoodMoment, Saved_My_Life]
        "sticker_type": STICKER_TYPE,
    },
}
```

### template
```js
{
    "type": "template",
    "payload": {
        "template_type":TEMPLATE_TYPE,
        "elements": [],
        "buttons":[],
        "text": TEXT,
    },
}
```

#### element
```js
{
    "title":TITLE,
    "subtitle":SUBTITLE,
    "body": BODY,
    "image_url": IMAGE_URL,
    "item_url": ITEM_URL,
    "buttons":[buttons],
}
```

#### button
```js
{
    "type": "web_url",
    "url": "https://www.healthtap.com",
    "title":TITLE,
}
```

### action
```js
{
    "type": "action",
    "payload": {
        "message_type":[start_session, end_session, start_video_posted, peer_unavailable peer_reavailable], # deprecated
    },
}
```

### start_live
```js
{
    "type": "start_live",
    payload: {
        "user": ACTOR,
        "audio_enabled": BOOL,
        "video_enabled": BOOL
    }
}
```

### end_live
```js
{
    "type": "end_live",
    payload: {
        "user": ACTOR,
        "audio_enabled": BOOL,
        "video_enabled": BOOL
    }
}
```

### invite_participant
```js
{
    "type": "invite_participant",
    "payload": {
        user: ACTOR,
        invitee: ACTOR
    }
}
```

### remove_participant
```js
{
    "type": "remove_participant",
    "payload": {
        user: ACTOR,
        removed_user: ACTOR
    }
}
```

### transfer_ownership
```js
{
    "type": "transfer_ownership",
    "payload": {
        user: ACTOR,
        new_owner: ACTOR
    }
}
```

### put_on_hold
```js
{
    "type": "put_on_hold", # expired_at should be set to session target end time
    "payload": {
        "client_id": "CLIENT_ID"
    }
}
```

### cancel_on_hold
```js
{
    "type": "cancel_on_hold", # expired_at should be set to session target end time
    "payload": {
        "client_id": "CLIENT_ID"
    }
}
```

### foreground_app
```js
{
    "type": "foreground_app" # expired_at should be set to session target end time
}
```

### background_app
```js
{
    "type": "background_app" # expired_at should be set to session target end time
}
```

### mute_video
```js
{
    "type": "mute_video",
    "payload": {
        "client_id": "CLIENT_ID"
    }
}
```

### unmute_video
```js
{
    "type": "unmute_video",
    "payload": {
        "client_id": "CLIENT_ID"
    }
}
```

### mute_audio
```js
{
    "type": "mute_audio",
    "payload": {
        "client_id": "CLIENT_ID"
    }
}
```

### unmute_audio
```js
{
    "type": "unmute_audio",
    "payload": {
        "client_id": "CLIENT_ID"
    }
}
```

### start_screen_share
```js
{
    "type": "start_screen_share",
    "payload": {
        "client_id": "CLIENT_ID"
    }
}
```

### stop_screen_share
```js
{
    "type": "stop_screen_share",
    "payload": {
        "client_id": "CLIENT_ID"
    }
}
```

### join_room
```js
{
    "type": "join_room"
}
```

### leave_room
```js
{
    "type": "leave_room"
}
```

### live_call_unsupported
```js
{
    "type": "live_call_unsupported" # expired_at should be set to session target end time
}
```

### metrics_updated
```js
{
    "type": "metrics_updated" # FIXME: find a better name
}
```


### delivery
```js
{
    "type": "delivery", # for webhook
    "payload": {
        "mids": [MESSAGE_ID],
        "watermark": TIMESTAMP,
    },
}
```

### typing_on
```js
{
    "type": "typing_on",
}
```

### typing_off
```js
{
    "type": "typing_off",
}
```

### mark_read
```js
{
    "type": "mark_read",
    "payload": {
        // "mids": [MESSAGE_ID],
        "watermark": TIMESTAMP,
    },
}
```

### presence
```js
{
    "type": "presence_change",
    "payload": {
        "presence": one of [online, offline],
        "manual": true of false # manual change or not,
    },
}
```

## System Message

### create_room
creator is owner of the room

```js
{
    "type": "create_room",
    "payload": {
        "name": ROOMNAME,
        "can_apply_to_join": BOOL,
        "join_action_requires_admin_approval": BOOL,
        "pin_code": ROOMPIN,
    }
}
```

response
```js
{
    "type": "create_room_response",
    "payload": {
        "result": "ok",
        "room_id": ROOMID,

        "result": "error",
        "message": ERROR MESSAGE,
    }
}
```

### join_room
user -> system
```js
{
    "type": "join_room",
    "payload": {
        "room_id": ROOMID,
        "pin_code": ROOMPIN,
        "invite_code": CODE,
    }
}
```

system -> user
```js
{
    "type": "join_room_response",
    "payload": {
        "result": "ok",
        "room_id": ROOMID,

        "result": "request_sent", // ignore it for now

        "result": "error",
        "message": ERROR MEESSAGE,
    }
}
```

system -> room
```js
{
    "type": "join_room",
    "payload": {
        "user": {
            "type": "user",
            "data": {
                "username": USERNAME
            }
        }
    }
}
```

system -> room
```js
{
    "type": "leave_room",
    "payload": {
        "user": {
            "type": "user",
            "data": {
                "username": USERNAME
            }
        }
    }
}
```

### Invite to Join Room
user -> system
```js
{
    "type": "invite_to_join_room",
    "payload": {
        "invitee_username": USERNAME,
        "room_id": ROOM_ID
        "pin_code": ROOMPIN
        "options": OPTIONS
    }
}
```

system -> user(inviter)
```js
{
    "type": "invite_to_join_room_response",
    "payload": {
        "result": "ok",
    }
}
```

system -> user(invitee)
response
```js
{
    "type": "invite_to_join_room",
    "payload": {
        "inviter_username": USERNAME,
        "room_id": ROOM_ID,
        "pin_code": ROOMPIN,
        "options": OPTIONS
    }
}
```

<!-- TODO: for sender -->
### invite_user_to_room
### remove_user_from_room
### process_join_room_request

<!-- TODO: for receiver -->
### user_join_room
### user_leave_room
### unprocessed_request
### get_invitation_to_join_room

<!-- TODO: invite by link -->

## Message for Sender

### Struct

```js
{
    "client_message_id": CLIENT_MESSAGE_ID, // optional, modified flag
    "message": rich_text(),
    "expired_at": TIMESTAMP,    // optional
    "metadata": META_DATA,      // optional
    "quick_replies": [],        // optional
}
```

### Avaliable Type
`text`, `image`, `video`, `audio`, `file`, `location`, `sticker`, `action`, `typing_on`, `typing_off`, `mark_read`

## Message for Receiver

### Struct

```js
{
    "id":        MESSAGE_ID,
    "seq":       SEQ,           // TODO
    "recipient": ACTOR,
    "sender":    ACTOR,
    "message":   rich_text(),
    "created_at": TIMESTAMP,
    "updated_at": TIMESTAMP,
    "expired_at": TIMESTAMP,
    "quick_replies": [],
    "metadata":  META_DATA,
    "client_message_id": CLIENT_MESSAGE_ID,
}
```

### Avaliable Type
`text`, `image`, `video`, `audio`, `file`, `location`, `sticker`, `template`, `action`, `element`, `button`, `typing_on`, `typing_off`, `mark_read`


## Message for Webhook
 `delivery`, `read`

## Mention
#### @all | @here
```
{
    "type": "text",
    "payload": {
        "text": "<!here|@here> This is a Message",
    },
}
```

#### @someone with username
```
{
    "type": "text",
    "payload": {
        "text": "<@username> This is a Message",
    },
}
```
