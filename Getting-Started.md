This page will guide you on connecting your account to FishingBucket, proxy creation and management, and commonly used commands.  
Before you can use FishingBucket, there is a short setup process.
* If you're a user setting up proxies in FishingBucket for the first time, [click here](#for-users) to jump to the user guide.
* If you're the owner of a Fluxer community and you want to learn how to use FishingBucket in your community, [click here](#inviting-fishingbucket-on-fluxer) to jump to the community owner guide.
* If you're the owner of a Discord server and you want to learn how to use FishingBucket in your server, [click here](#inviting-fishingbucket-on-discord) to jump to the server owner guide.
# For Users
## Proxies and Triggers
You can make your first proxy by using the [Web Dashboard](https://fishingbucket.org/dashboard), or joining a server with FishingBucket and running the command `fish!register`.

The syntax is `fish!register <name: string> <trigger: template>`, where `name` is the name you want to use for the proxy, and `trigger` is the tag you use to activate it. Names that include a space must be surrounded by "double quotes". Triggers are written as the string `{}` surrounded by any sequence of characters.

For instance, to register a proxy named Bob which can be triggered with the message `Bob: Hello, my name is Bob`, the syntax would be:  

`fish!register Bob Bob:{}`

To register a proxy named Proxy McProxyFace which can be triggered with the message `Hello, my name is Proxy McProxyFace -pmp`, the syntax would be:

`fish!register "Proxy McProxyFace" {}-pmp`

When a proxy is registered, FishingBucket will send a confirmation message similar to this one:
> **Proxy McProxyFace (`0x28ebb`)**  
> Proxy **Proxy McProxyFace** is registered with an ID of `0x28ebb`!  
> Say hello with it by typing `hello-pmp`  

The string starting with `0x` is your proxy's ID. You can refer to the proxy in future commands with either its name (`"Proxy McProxyFace"` in this case) or its ID (`0x28ebb` in this case).

## Editing Proxies
Proxies can have several fields of information associated with them. These fields can be edited in the [Web Dashboard](https://fishingbucket.org/dashboard), or using the command `fish!set`.

* To set a proxy's **avatar**, the syntax is `fish!set avatar <proxy: proxy> [url: url]`, where `proxy` is the name or ID of a proxy, and `url` is a link to the image. The image can also be sent as an attachment to the message.
* To update a proxy's **triggers**, the syntax is `fish!set triggers <proxy: proxy> <mode: 'set' OR 'add' OR 'remove'> [trigger: template]`, where `proxy` is the name or ID of a proxy, `mode` is the action to perform, and `trigger` is the trigger template as explained above.

For instance, to _replace_ our proxy Bob's old trigger with the new trigger `{}-Bob`, the syntax would be:

`fish!set triggers Bob set {}-Bob`

To _add a second trigger_ to our proxy Proxy McProxyFace in the format `pmp:{}`, the syntax would be:

`fish!set triggers 0x28ebb add pmp:{}`

To _remove all_ triggers from Proxy McProxyFace, the syntax would be:

`fish!set triggers "Proxy McProxyFace" remove`
* A complete list of fields and their syntax can be found by the command `fish!help proxy_action_commands`.
## Autoproxy and Spotlight
FishingBucket's "autoproxy" is a system for selecting proxies to be automatically triggered when chatting. This prevents having to type the trigger with every message, making fast and casual exchanges more convenient for users. There are four autoproxy settings: latch, proxy, spotlight, and none. The syntax of autoproxy is `fish!autoproxy <setting: 'latch' OR 'spotlight' OR boolean OR proxy> [mode: 'global' OR 'community'] [expiration: 'never' OR duration]`, where `setting` is the desired autoproxy setting, `mode` is the [autoproxy scope](#autoproxy-scope),  and `expiration` is an optional time until autoproxy is disabled.
### Latch Setting
Latch mode automatically proxies all messages as the last proxy triggered. For instance, if you trigger the proxy Bob by sending a message `Bob: Hi everyone!`, then send another message `How are you?`, the second message will be automatically proxied as Bob.

To enable latch mode globally (in all communities), send the command `fish!autoproxy latch`. To enable latch mode in the current community, send the command `fish!autoproxy latch community`. To enable latch mode globally, but automatically disable it after 2 hours, send the command `fish!autoproxy latch global 2h`.
### Proxy Setting
Proxy mode automatically proxies all messages as one specific proxy. For instance, if you set Bob as the autoproxy by running `fish!autoproxy proxy`, then send a message as Proxy McProxyFace `pmp: Hi everyone!`, then send another message `How are you?`, the last message will be automatically proxied as Bob.
### Spotlight Setting
Spotlight mode is an alternative to proxy mode which can be used to quickly change the autoproxy target. Multiple proxies can be in the spotlight at the same time, in which case the first spotlight will always be autoproxied. Plural users can employ multiple spotlights to track [co-fronting](https://pluralpedia.org/w/Co-fronting) status. To use spotlight mode, you have to first set a proxy (or several proxies) as your account's spotlight.
To set a proxy as the spotlight, the syntax would be:

`fish!spot set [proxies: proxy(s)]`

where `proxies` is the name or ID of the proxy to set.

To automatically proxy messages as the spotlight, the syntax would be:

`fish!autoproxy spotlight`
### Autoproxy Scope
## Adding Tags
Tags are a way of organizing and grouping proxies. They can be created and adjusted in the [Web Dashboard](https://fishingbucket.org/dashboard), or using the command `fish!tag`.  
The syntax for adding, editing, and removing tags can be found by the command `fish!help tag_commands`.
## Connecting More Accounts
The same set of FishingBucket proxies and tags can be used by multiple profiles across Fluxer and Discord. To connect another profile to your existing FishingBucket account, start by running the command `fish!link initiate` on the profile with the existing account.

FishingBucket will send you a direct message with a command to execute. You should execute this entire command on the profile you want to connect to the FishingBucket account. The link code expires after some time, so this should be done quickly.  
The profile to be linked must not already be connected to a FishingBucket account. If the target profile already has an account, it _(and all of its existing proxies and tags)_ can be deleted with the command `fish!account delete`.  
To unlink a profile from your FishingBucket account, that profile should run the command `fish!unlink`.
# For Community Owners
## Inviting FishingBucket on Fluxer
Fluxer is FishingBucket's primary platform. The Fluxer support community can be found at [https://fluxer.gg/jpXCwfto](https://fluxer.gg/jpXCwfto), and the bot can be invited to your community [here](https://web.fluxer.app/oauth2/authorize?client_id=1471373152818077943&scope=bot&permissions=137976212560).

## Inviting FishingBucket on Discord
Discord is FishingBucket's secondary platform. The Discord support server can be found at [https://discord.gg/yPJAg4ytaJ](https://discord.gg/yPJAg4ytaJ), and the bot can be invited to your server [here](https://discord.com/oauth2/authorize?client_id=1478252547197108417&permissions=413122554944&integration_type=0&scope=bot).