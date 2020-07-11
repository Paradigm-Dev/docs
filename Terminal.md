[<img src="https://www.theparadigmdev.com/relay/img/paradigm.png" alt="Logo" width="150" height="150"></img>](https://www.theparadigmdev.com/)
# Terminal

The terminal is the administrative interface to the database. It is only accessible by administrators. To access the Terminal, open the navigation drawer and click the Terminal button, it is in between your username and the log out button. Please do not abuse the Terminal. All Terminal actions are logged. Any abuse of the Terminal system will result in account deletion and IP ban.

## Table of Contents
1. [`set`](https://github.com/Paradigm-Dev/docs/blob/master/Terminal.md#set)
2. [`user`](https://github.com/Paradigm-Dev/docs/blob/master/Terminal.md#user)
3. [`list`](https://github.com/Paradigm-Dev/docs/blob/master/Terminal.md#list)
4. [`me`](https://github.com/Paradigm-Dev/docs/blob/master/Terminal.md#me)
5. [`ipban`](https://github.com/Paradigm-Dev/docs/blob/master/Terminal.md#ipban)
6. [`clear`](https://github.com/Paradigm-Dev/docs/blob/master/Terminal.md#clear)
7. [`nuke`](https://github.com/Paradigm-Dev/docs/blob/master/Terminal.md#nuke)
8. [Dictionary](https://github.com/Paradigm-Dev/docs/blob/master/Terminal.md#dictionary)

## `set`
This command sets configuration entries on the database. It controls every aspect of the user experience.
#### `set sign_up [true/false]`
This enables or disables sign ups.
#### `set reset [true/false]`
This enables or disables password resets. This feature is not available at the moment, so this is always set to `true`.
#### `set shutdown [true/false]`
This enables or disables shutdown. Shutdown closes off the entire website from new users and logs out currently logged in users. Useful in certain scenarios.
#### `set router.[PAGES] [true/false]`
This enables or disables the page entered in the command.

## `user`
This command views or sets configuration entries on the database for a particular user. It controls every aspect of the user's account, except the password.
#### `user [username] view`
This outputs the user's database entry, minus the password (of course).
#### `user [username] ban [true/false]`
This enables or disables the ban screen on login. Banning blocks the user from the site upon login. It is functionally the same as deleting the account, but its recoverable.
#### `user [username] rights.[RIGHTS] [true/false]`
This enables or disables a certain right for the user. Please see the dictionary entry on 'RIGHTS'.
#### `user [username] strike [number]`
This adds or subtracts (by using a negative number) the number of strikes the user has. A total of 3 strikes will result in a ban. The number cannot go lower than 0.
#### `user [username] kick`
If the user is logged in, they are logged out. Otherwise, nothing happens.
#### `user [username] delete`
This deletes the specified user's account.
#### `user [username] rocks [number]`
Adds or subtracts (by using a negative number) a number of Moonrocks to/from the user's account.

## `list`
This command outputs database collections.
#### `list users`
This outputs a list of usernames with accounts.
#### `list chatrooms`
This outputs a list of chatroom names and IDs.
#### `list books`
This outputs a list of book titles with their authors.
#### `list movies`
This outputs a list of movies.
#### `list music`
This outputs a list of album titles and their artists.

## `me`
This command outputs the current user's full JSON string, straight from the database.

## `ipban [ip address]`
This command bans the entered public IP address from accessing any part of Paradigm.

## `clear`
This command clears the console.

## `nuke`
This command should only be used if all else fails. It physically shuts down the database and Relay. The server will have to be manually restarted. No new connections to the website will be able to be established. Existing ones are disconnected.

## Dictionary
This is a list of the various "all-caps" command arguments used above.
#### `true/false`
I hope you know what this means. It simply toggles whether or not the specified thing is visible or not/available or not.
#### `number`
I hope you know what this means. Its literally a number. A kindergardener could handle this one.
#### `username`
This is a unique string that, to other users, identifies them. On the database, however, the user's ID string identifies them.
#### `ip address`
An IP address is a numerical label assigned to each network by their ISP in order to communicate with the rest of the Internet. Within a network, there are Private IP addresses, but this command cannot ban hyperspecific devices.
#### `PAGES`
The individual pages on Paradigm. Possible values:
* `flamechat`
* `satellite`
* `paradox`
* `drawer`
* `media`
* `home`
* `write`
* `people`
* `broadcast`
* `transmission`
#### `RIGHTS`
The individual rights that are toggleable for each user. Possible values:
* `admin`
* `author`
* `asteroid`
* `developer`
* `apollo`
