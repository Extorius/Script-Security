# Script-Security
Cracked Scripts is meant to be a reminder to developers everywhere on how to properly, and unproperly protect what's rightfully theirs from being stolen, reverse engineered, hold ransom, or anything else bad. In this repository, we'll gloss over some basic security while also providing some real examples of scripts that were very poorly protected.

## Chapter 1 - Storage
Storing your code in a file hosting service so that it can be ran using a loadstring is a smart idea. However, it does not, by any means, offer that much security, even if it does block requests made by browsers.

The client can just replace the loadstring with print, or if you added a bit of obfuscation to the request they can just replace the loadstring closure with a print closure, and get the entire raw source of your script.
#### Security Rating
- 1/10
#### Scripts With Vulnerability
- Krato Security (ironic, I know)

## Chapter 2 - Comment Spam
Now, to must this is fairly obviously a poor method to obscure or hide your raw source. However, this isn't as obvious to some unfortunately.
If you are one of those people of whom thought this was a good idea, consider the following being done to your script:
- Someone minifies your code using a [Lua minifier](https://goonlinetools.com/lua-minifier/) to remove the comments
- Then beautifies it with a [Lua beautifier](https://goonlinetools.com/lua-beautifier/) to make it readable again
These *two* steps can be done by *anyone* and does not require any amount of technical or programming knowhow.
In just two steps your entire script's raw source code is completely vulnerable and can be stolen.
#### Security Rating
- 1/10
#### Scripts With Vulnerability
- Krato Security
- MostBlatantMalware#0277's Shit Aimbot

## Chapter 3 - Restricted Access
Keeping your script refined to a small audience of people, or in other words privated, is a pretty bad idea without obfuscation. Anyone in the group that has access can at any point leak the script, which is why this is only a good idea if someone is paying you for this script specifically. Otherwise, it's really not worth the risk unless the script is very low value, or the people who have access can be trusted.
#### Security Rating
- 2/10
#### Scripts With Vulnerability
- None so far

## Chatpter 4 - Free Obfuscators / Loadstring Obfuscators
### Free Known Name Obfuscators
Obfuscation using a free obfuscator is a excellent idea.. for free, low value scripts. If you are considering providing a script that is protected using a free obfuscator, please highly reconsider as it implies the following:
- The obfuscator is either one supported by LD (will be talked about more) and can be deobfuscated, or the obfuscator itself is so bad LD doesn't support it
- The whitelisting is done by yourself, which is generally just not a good idea
To touch more on the first part and talk more about LD, here is a brief summary:
LD is a paid deobfuscation service ($10) that takes a script that's been obfuscated by a brief list of popular obfuscators, and uses a program to automatically deobfuscate it into Lua bytecode; which can then be decompiled and return a very close copy of the original script. This is a MAJOR vulnerability for anyone using the following obfuscators:

- Moonsec v2
- Moonsec v3
- PSU
- Boronide
- IB2
- AztupBrew

However, a free obfuscator for a normal free script is totally fine and endorsed if you can't afford a paid one, or a whitelisting service.
A free obfuscator is more then definitely better then previous methods mentioned, and will boost your security by a lot.

To summarize everything mentioned above, please consider the following points carefully:
- If the script you're providing is paid, chances are one of the buyers has the money to buy a deobfuscation from LD for 10$
- Even if your script isn't paid, if it gets popular enough eventually someone is going to try to crack it, and that someone might have some money to cough up
- If your script is high value (rare script, best script for a game, large game hub, etc.) someone is going to want to know how it works, or know your methods; especially your competition, which is why making the investment for a high quality obfuscator or whitelisting service is a fantastic idea
#### Security Rating
- 5/10
#### Scripts With Vulnerability
- None so far

### Loadstring / Shit Obfuscators
Just... just dont.
#### Security Rating
- 1/10
#### Scripts With Vulnerability
- None so far

### Paid Obfuscators
I recently saw someone in a whitelisting Discord server asking about premium obfuscation since their webhook was spammed. Obfuscation, simplified, hides and protects your code itself. Not what it does. There's a misconception that obfuscation is a great way to protect your script, and to a degree it is. Obfuscation only really hides, protectes, and prevents tampering with the hard-coded code, not what it may do. It does not prevent HTTP sniffing, does not prevent hooking, and will not be perfect for most use cases. Ultimately, obfuscation is only really effectived when combined with premium whitelisting and security. Otherwise, it's only delaying someone cracking your code.

Now, with all of this out of the way, there are some major benefits of investing into a paid obfuscator. While we discuss these, Luraph and solely Luraph is the only obfuscator that is being reffered to; as it's really the only obfuscator you should be looking into.

Luraph's list of features that make it good are hard to fit into one paragraph, but I'll try. To start, there's the VM itself. If you don't know what that means or how it works, here's a brief overview;

The Lua language can't be inteperated by your CPU as Lua. It's typically inteperated as C or a similar language that your CPU can understand. That's the Lua VM. Each instruction you give your Lua script, such as printing 'Hello world!' is a list of instructions being sent to the interprater which is then ran on your CPU. These instructions can be called 'bytecode'. The way a custom VM generated by a obfuscator works, is by being a middle man for all of this. Instead of your code looking something along the lines of:
```lua
local a = 'Hello world!'
print(a)
```
It might look something more like (highly simplified):
```lua
local Constants = {{'a', 'Hello world!'}, {'print', 'a'}} -- the instructions being sent to the VM will be a lot more sophisticated then this, and a lot more information packed
getgenv()[Constants[1][1]] = Constants[1][2] -- obviously, not all instructions will be inteperated like this, as some instructions printing might not be printing a variable, and a ton of other possibilities
getgenv()[Constants[2][1]](getgenv()[Constants[2][2]])
```

Now, obviously this is a pretty dumbed down version of what a custom VM obfuscator would look like, but it gives you an idea on how it works, and how a obfuscator can safely manage information going through your client, and be able to shutdown if something doesn't add up.

Now, that's just the first stage of Luraph's security. The next is bytecode mutation. Some parts of your code don't really need to be there, or can be randomized or changed without impacting the actual functionality of your code. That's where bytecode mutation steps in. Luraph will filter out the parts of your code that can be removed, and remove them, and filter out the parts that can be changed or randomized, and you guessed it, change or randomize it. This makes it extra hard for an attack attempting to reconstruct your script to do so, as parts of it don't add up to what you'd expect.

Next, is control flow scrambling. If the custom VM sounded complicated, that's because it is. It's the founding aspect of pretty much any half decent obfuscator, and is a very *very* complicated thing to code. But, Luraph takes it to another level by having this control flow, or VM, randomize and change at random points; making it even harder for someone to reverse engineer.

As well, Luraph implements a custom encryption method that encrypts the instructions being sent to the VM. This in of itself is pretty standard, but Luraph is careful with how it's constructed, and you can be sure that anyone trying to decipher or decrypt it would have a very hard time.

All of these premium features of a premium obfuscator (and there's a lot more that I haven't mentioned) essentially guarentee that if someone were to try crack your script, deobfuscating would be a absolute last resort. And they likely won't even be close to successful.
#### Security Rating
- 7/10
#### Scripts With Vulnerability
- None so far

## Basic Whitelisting
Now, whitelisting in of itself can be a very complex and tedious process if you intend to keep it secure, hard to reverse-engineer, and hard to bypass or crack.
Premium whitelisting services will always incoporate a premium obfuscator such as Luraph, as well as top of the line, and often private methods, of preventing common and effective attacks seen in not just Lua.

The client-server relationship of a whitelisting service is what keeps it so secure (if done properly). Essentially, what you want to do is first prove that the client is legitamely the client, and does not contain tinted functions (hooked, spoofed, or sniffed). After that, you can prove that the server is the server, typically done by sending it a unique number, and checking if the number sent back is the one you expected through some complicated equations. As well, confirming that the handshake from the client to the server is an important step in ensuring that the entire client-server relationship isn't just a hooked function that replicates the information being sent to the server, and the information sent back.

This is the very bare bones of a more premium whitelisting system, and many more security features can be found in most. All in all, a whitelisting service with added code security is about as secure as you can get. If you're interested in this option, here's a few whitelisting services you should check, ranked in security and other features:

Service | Speed | Stability | Security
--- | --- | --- | ---
Luarmor | 10/10 | 7/10 | 10/10
luaGuard | 8/10 | 9/10 | 8/10

#### Security Rating
- 8-10/10
#### Scripts With Vulnerability
- None so far

## Summary - What's secure?
### Storage
A good storage option that can block requests made in browser is a good idea. It won't *really* add much security, but it can be a good warning for potential attackers, and most people won't go much further.

### Obfuscation
Always. Use. Luraph. Aren't really sure if it's that secure? We have a seperate explanation on why Luraph is the best option if you value security.

### Whitelisting
Although your script might not need the actual whitelisting aspect, premium whitelisting systems such as luaGuard or Luarmor both offer free for all modes with the exact same amount of real code security, and is **highly** recommended to use, especially if your script is making requests to an external server or endpoint.
