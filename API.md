[<img src="https://www.theparadigmdev.com/relay/img/paradigm.png" alt="Logo" width="150" height="150"></img>](https://www.theparadigmdev.com/)
# Relay API

Documentation for the backbone of Paradigm: Relay's API.


## Table of Contents
1. [Index](https://github.com/Paradigm-Dev/docs/blob/master/API.md#index)
2. [Authentication](https://github.com/Paradigm-Dev/docs/blob/master/API.md#authentication)
3. [Broadcast](https://github.com/Paradigm-Dev/docs/blob/master/API.md#broadcast)
4. [Drawer](https://github.com/Paradigm-Dev/docs/blob/master/API.md#drawer)
5. [Flamechat](https://github.com/Paradigm-Dev/docs/blob/master/API.md#flamechat)
6. [Media](https://github.com/Paradigm-Dev/docs/blob/master/API.md#media)
7. [Paradox](https://github.com/Paradigm-Dev/docs/blob/master/API.md#paradox)
8. [People](https://github.com/Paradigm-Dev/docs/blob/master/API.md#people)
9. [Terminal](https://github.com/Paradigm-Dev/docs/blob/master/API.md#terminal)
10. [Transmission](https://github.com/Paradigm-Dev/docs/blob/master/API.md#transmission)
11. [User](https://github.com/Paradigm-Dev/docs/blob/master/API.md#user)
<hr>


## Index
### `GET /`
Serves the main Paradigm website.

### `GET /relay/<url>`
Serves the requested content out of the `/files` folder.
<hr>


## Authentication
### `POST /api/auth/signup`
Creates a new user with the data passed.
```ts
interface {
  username: string
  password: string
  bio: string
  color: string
  invite_code: string
}

return User
```

### `POST /api/auth/signin`
Authenticates an existing user.
```ts
interface {
  username: string
  password: string
}

return User
```

### `GET /api/:uid/auth/signout`
Deauthenticates an existing user, who is already signed in.
```ts
return null
```

### `POST /api/:uid/auth/reset`
Resets a user's password.
```ts
interface {
  current: string
  password: string
}

return User
```

### `GET /api/auth/check/:username`
Checks if a username exists and is logged in.
```ts
return interface {
  exists: boolean
  in: boolean
}
```
<hr>


## Broadcast
### `POST /api/:uid/broadcast`
Creates a new Broadcast post.
```ts
interface {
  content: string
  timestamp: string
  likes: number
  recasts: number
}

return User
```

### `DELETE /api/:uid/broadcast/delete/:id`
Deletes a Broadcast post.
```ts
return User
```

### `GET /api/:uid/broadcast/like/:profile/:id`
Likes another user's Broadcast post.
```ts
return {
  User, // user who likes a post
  User // user whose post was liked
}
```

### `GET /api/:uid/broadcast/unlike/:profile/:id`
Unlikes another user's Broadcast post.
```ts
return {
  User, // user who likes a post
  User // user whose post was liked
}
```
<hr>


## Drawer
### `GET /api/:uid/drawer/download/:id`
Downloads the requested Drawer file.
```ts
return File
```

### `POST /api/:uid/drawer/rename/:id`
Renames a user's file.
```ts
interface {
  name: string
}

return User
```

### `DELETE /api/:uid/drawer/delete/:id`
Deletes a user's file.
```ts
return User
```

### `POST /api/drawer/:uid/upload`
is now `POST /api/:uid/drawer`. Used to upload a user's file.
```ts
type FormData

return User
```
<hr>


## Flamechat
### `POST /api/:uid/flamechat/chatroom`
Creates a new chatroom.
```ts
interface {
  icon: string
  id: string
  name: string
  owner: string
  theme: string
}

return User
```

### `POST /api/:uid/flamechat/chatroom/:id/upload`
Uploads a sent file.
```ts
type FormData

return null
```

### `POST /api/:uid/flamechat/dm/:id/upload`
Uploads a sent file within a direct message.
```ts
type FormData

return null
```

### `DELETE /api/:uid/flamechat/chatroom/:id`
Deletes a chatroom.
```ts
return null
```

### `GET /api/:uid/flamechat/chatroom/:id/request`
Requests to join a chatroom.
```ts
return User || Error
```

### `GET /api/:uid/flamechat/chatroom/:id/undo-request`
Undos a request to join a chatroom.
```ts
return null
```

### `DELETE /api/:uid/flamechat/chatroom/:id/remove/:user`
Removes a user from a chatroom.
```ts
return null
```

### `GET /api/:uid/flamechat/chatroom/:id/request/:user/approve`
Approves a user's request to join a chatroom.
```ts
return null
```

### `DELETE /api/:uid/flamechat/chatroom/:id/request/:user/reject`
Rejects a user's request to join a chatroom.
```ts
return null
```

### `DELETE /api/:uid/flamechat/chatroom/:id/ban/:user`
Bans a user from a chatroom.
```ts
return null
```

### `GET /api/:uid/flamechat/chatroom/:id/unban/:user`
Unbans a user from a chatroom.
```ts
return null
```

### `DELETE /api/:uid/flamechat/chatroom/:id/purge`
Purges all messages from a chatroom.
```ts
return null
```
<hr>


## Media
### `GET /api/:uid/media/books`
Gets a list of books.
```ts
return Book[]
```

### `POST /api/:uid/media/books/:id`
Updates stored data for a book in a user.
```ts
interface {
  rating: number
  favorite: boolean
}

return User
```

### `GET /api/:uid/media/movies`
Gets a list of movies.
```ts
return Movie[]
```

### `POST /api/:uid/media/movies/:id`
Updates stored data for a movie in a user.
```ts
interface {
  rating: number
  favorite: boolean
}

return User
```

### `GET /api/:uid/media/music`
Gets a list of albums.
```ts
return Music[]
```

### `POST /api/:uid/media/music/:id`
Updates stored data for an album in a user.
```ts
interface {
  rating: number
  favorite: boolean
}

return User
```


### `POST /api/:uid/media/data`
Creates a new media item. This saves the data, not the files. Music is not working at the moment.
```ts
interface Book {
  author: string
  live: boolean
  cover: string
  link: string
  summary: string
  title: string
}

interface Movie {
  genre: string
  live: boolean
  cover: string
  link: string
  summary: string
  title: string
}

return { _id: ObjectId }
```
### `POST /api/:uid/media/create/files/:id/:type`
Uploads files for a newly created media item. Music is not working at the moment.
```ts
type FormData

return null
```
<hr>


## Paradox
### `GET /api/:uid/paradox`
Gets Paradox stories.
```ts
return News[]
```

### `POST /api/:uid/paradox`
Creates a new Paradox story.
```ts
interface {
  author: string
  cover: string
  content: string
  timestamp: string
  title: string
  live: boolean
}

return News[]
```
<hr>


## People
### `GET /api/:uid/people`
Returns a list of all users.
```ts
return User[]
```

### `GET /api/:uid/people/short`
Returns a list of all users, with less data.
```ts
return User[]
```

### `GET /api/:uid/people/request/:user/send`
Sends a friend request to someone else.
```ts
return User
```

### `GET /api/:uid/people/request/:user/approve`
Approves a friend request from someone else.
```ts
return User
```

### `DELETE /api/:uid/people/request/:user/reject`
Rejects/retracts a friend request from someone else.
```ts
return User
```

### `DELETE /api/:uid/people/remove/:user`
Removes a friend.
```ts
return User
```

### `DELETE /api/:uid/people/block/:user`
Blocks another user.
```ts
return User
```

### `DELETE /api/:uid/people/unblock/:user`
Unblocks another user.
```ts
return User
```
<hr>


## Terminal
### `GET /api/:uid/terminal/user/:username/view`
Sends information about a user.
```ts
return interface {
  _id: ObjectId
  username: string
  color: string
  bio: string
  moonrocks: number
  rights: {
    admin: boolean
    author: boolean
    asteroid: boolean
    developer: boolean
    apollo: boolean
  },
  banned: boolean
  strikes: number
  in: boolean
}
```

### `PUT /api/:uid/terminal/user/:username/strike/:count`
Adds/removes strikes from a user.
```ts
return null
```

### `DELETE /api/:uid/terminal/user/:username/delete`
Deletes a user.
```ts
return null
```

### `GET /api/:uid/terminal/list/users`
Gets a list of usernames and IDs.
```ts
return interface [] {
  _id: ObjectId
  username: string
}
```

### `GET /api/:uid/terminal/list/chatrooms`
Gets a list of chatrooms and their IDs.
```ts
return interface [] {
  id: string
  title: string
}
```

### `GET /api/:uid/terminal/list/books`
Gets a list of books and their authors.
```ts
return interface [] {
  title: string
  author: string
}
```

### `GET /api/:uid/terminal/list/movies`
Gets a list of movies
```ts
return string[]
```

### `GET /api/:uid/terminal/list/music`
Gets a list of albums and their artists.
```ts
return interface [] {
  _id: ObjectId
  username: string
}
```
<hr>


## Transmission
*Placeholder*
<hr>


## User
### `POST /api/:uid/user/update`
Updates the user's profile.
```ts
interface {
  username: string
  bio: string
  color: string
}

return User
```

### `GET /api/:uid/user/:user`
Gets information about a user.
```ts
return interface {
  _id: string
  username: string
  color: string
  in: boolean
  bio: string
  pic: string
}
```

### `PUT /api/:uid/user/moonrocks/:count`
Adds/removes moonrocks.
```ts
return User
```

### `POST /api/:uid/user/pic`
Replaces profile pic.
```ts
return User
```

### `DELETE /api/:uid/user`
Deletes a user.
```ts
return null
```
<!-- <hr> -->