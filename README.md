# Discord.pySpambot
simple discord spambot that's written shortly in python thanks to the discord.py library 
Do not use if the owner of the server doesnt allow you to
It is possible to write ur own token where the bots token belongs but this is stricty against discord TOS and I am not responsible what happens to your account!
Do not use outside ur own servers or servers where the owner consents to it!



```python
import discord
import time

client = discord.Client()

global spam
spam = False #variable spam when toggled on bot will send messages
x = False
@client.event
async def on_ready():
    x = True
    print(x) #prints out True when bot is up and running!


@client.event
async def on_message(spammsg):
    if spammsg.content.startswith(".togglespam"): #the command that will send spam to be true
        global spam
        spam = not(spam)
        await spammsg.channel.send(spam)
    elif spammsg.author == client.user and spam == True: #will reply to its own message that said "True" I couldve also used a while loop but this was shorter.
        await spammsg.channel.send("ur message here") #type ur message or link that u wanna spam inside the ""
        time.sleep(1)


client.run('Your Token here')
