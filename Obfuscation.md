# Obfuscation
Obfuscation is the act of obscuring the hard-coded code and adding security to it by running it in a custom environment so you can monitor, verify, and secure everything being done by the client. This is an exceptionally powerful tool in security and should not be underestimated, or overestimated. While obfuscation is great for the hard-coded aspect, always remember the client has more control than you and can hook *anything*, so always use an extra layer of protection such as anti-hooks.

This is exceptionally great for keeping your code secure, and hard to steal; as everything is hidden in the encrypted VM, and monitored to prevent tampering, spoofing, and deobfuscation.
## Why use a 'VM' obfuscator, and what is it?
Roblox Lua naturally cannot be interpreted by your CPU, which is why a language such as C does the actual computing. This is the natural Lua VM that is used when you run a normal script.

A Lua VM obfuscator recreates this, by being fed a list of instructions to run as they normally would be. It's essentially doing the same thing, except since it's being run in the obfuscator's custom VM, everything can be monitored, checked, and secured.

This is especially useful for macros you may see in an obfuscator, such as Luraph, that allow you to crash the VM; which shuts down everything and re-encrypts the VM, giving you a failsafe for attempted cracks. This is exceptionally powerful for whitelisting and code security.

## Instruction List
Roblox Lua Handicapped obfuscation is a complex and sophisticated task of recreating the VM that Lua runs it. How this works is an interpreter is fed a list of instructions to carry out.

## Specifics
The list of instructions is usually a long and highly encrypted string in more secure obfuscators, but can also be a large dictionary of instructions in a less secure obfuscator. These instructions are typically Lua bytecode.

## Complexity
Each instruction should carry large amounts of specific data so that the VM knows exactly what to do with it. For example, what if you want to print 'Hello world'? Seems simple, right? Well, what if that 'Hello world' is actually in a variable? Well, now it becomes more complicated.

## Luraph
This is where an advanced VM such as Luraph is a great example. Luraph's VM is highly secure with very hard-to-reverse-engineer encryption, as well as extra features such as control flow scrambling.

If you go to Luraph's website, you'll see these keywords being used:
- Virtualization
- Bytecode Mutation
- Control Flow Scrambling
- Encryption
- Compression
- Reliability

Now, unless you have previous experience in obfuscation and Luraph itself, these words will be very confusing and you may not know what they mean. In this brief explanation, we'll go over the more complex ones:

### Control Flow Scrambling
But what is control flow scrambling? Control flow scrambling is changing how the VM interoperates the set of instructions at random intervals; giving attacks yet another layer to figure out before they can crack through the VM.

This is why premium features like control flow scrambling are so important; almost any attacker will take one look at Luraph and give up, and the very few that know what to do would take hours at the very least to make sense of everything and get close to cracking the VM.

### Byte Code Mutation
Byte code mutation is when Luraph removes any information in your script that would allow an attacker to reconstruct it. Essentially, there's going to be tons of information in a script that simply does not need to be there. This is where byte codes mutation steps in.

Information that is not needed or is unimportant can be changed, randomize, or completely removed to minimize unique identifiers attackers can latch onto.

## Vulnerable Obfuscators
- Moonsec v2 [Complete Deobfuscation]
- Moonsec v3 [Complete Deobfuscation]
- AztupBrew [Complete Deobfuscation]
- PSU [Complete Deobfuscation]
- Boronide [Complete Deobfuscation]
- IB2 [Complete Deobfuscation]
- KratoSecurity [Easily Deobfuscated]
- Loadstring Obfuscators [Easily Deobfuscated]

## Security
Obfuscating your code is the absolute foundational step to securing it. And while obfuscating your code is a **huge** step and will improve security drastically, it doesn't offer too much security outside of securing and hiding the hard-coded aspects of your code. Everything can be hooked, snooped on, logged, etc. which is why it's always smart to obfuscate and secure your code with anti-hooks and whitelisting as well.
