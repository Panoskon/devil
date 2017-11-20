# devil Bot Python
import discord
import random
import discord
import random
import linecache
import re
import shelve
from discord.ext import commands

prefix = '&'

des = 'DevilBot Is A Mod Bot!'
client = commands.Bot(description=des, command_prefix=prefix)


@client.event
async def on_ready():
    print("[]I'm in")
    print('[] Name: {}'.format(client.user.name))
    
    
@client.command(pass_context=True)
async def Owner(ctx):
    """Shows the Owner Who Made The Bot!"""
    await client.say('Owners of the bot are <@348851219621478400> & <@303286549695561729>')

@client.command(pass_context=True)
async def Invite(ctx):
    """Type &Invite Gives you link inv the bot to Your server!"""
    await client.say('https://discordapp.com/oauth2/authorize?client_id=379244671974506496&scope=bot&permissions=1')

@client.command(pass_context = True)
async def kick(ctx, userName: discord.User):
    """Type &Kick @mention"""
    await client.kick(userName)
    await client.say("__**Successfully User Has Been Kicked!**__")

@client.command(pass_context = True)
async def Ban(ctx, userName: discord.User):
    """Type &Ban @mention"""
    await client.ban(userName)
    await client.say("__**Successfully User Has Been Banned!**__")
@client.command(pass_context=True)
async def Say(ctx, member : discord.Member = None, *, message):
    """Type &Say @mention Hello"""
    await client.send_message(member, message)

@client.command(pass_context=True)
async def purge(context, number : int):
	"""Clear a specified number of messages in the chat"""
	deleted = await client.purge_from(context.message.channel, limit=number)
	await client.send_message(context.message.channel, 'Deleted {} message(s)'.format(len(deleted)))
	
@client.event
async def Help (message):
    if message.content.startswith('&Help'):
        await client.send_message(message.author,' ```Devil Bot ``` \n *Written by KFE iAnimeZ#7970 in Python 3 using the discordpy API library !  \n  \n``` Commands```\n &Owner  `Shows who is the Owners of the Devil Bot` \n \n &Invite  `Type &Invite Gives you link inv the bot to Your server!`  \n  \n &Kick   `Type &Kick @mention  `  \n  \n &purge `Type &purge <number>` \n   \n &Ban   `Type &Ban @mention `\n  \n &Say `Type &Say @mention to send to a friend a message`\n   \n ```Join Ur Discord/For Questions/Chilling ``` \n \n Perma Link : https://discord.gg/FS8SMn8 \n')

    
client.run('Mzc5MjQ0NjcxOTc0NTA2NDk2.DOnXSw.LR7HVXEAHGQHwV1BnB0ZrxL22P0')
