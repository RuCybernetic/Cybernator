### Параметры
|           name             |                     type                     |Default|                           Information                                |
|:-------------------------:|:-------------------------------------------:|:----------:|:-------------------------------------------------------------------:|
|           ctx             | `discord.Client` `discord.ext.commands.Bot` |            |                                                                     |
|         message           |              `discord.Message`              |            |       Message with your embeds         |
|          embeds           |                    `list`                   |   `None`   |                        List of embeds                              |
|    timeout `<optional>`   |                    `int`                    | `30`seconds |        Paginator timer          |
|   use_more `<optional>`   |                    `bool`                   |   `False`  |            Adding 2/4 reactions (Default 2)                 |
|   use_exit `<optional>`   |                    `bool`                   |   `False`  |            Adding a reaction to disable the paginator                  |
|delete_message `<optional>`|                    `bool`                   |   `False`  |Remove Paginator when the timer expires (if False, it will remove reactions)|
|      only `<optional>`    |              `discord.abc.User`             |   `None`   |    Author using command (ctx.author)   |
|  time_stamp `<optional>`  |                    `bool`                   |   `False`  |                 Adding a command call time ([timestamp](https://discordpy.readthedocs.io/en/latest/api.html#discord.Embed.timestamp))                   |
|    footer `<optional>`    |                    `bool`                   |   `True`   |       On/off [footer](https://discordpy.readthedocs.io/en/latest/api.html#discord.Embed.footer) (Signature Section-Page)                         |
|   reactions `<optional>`  |                    `list`                   |["⬅", "➡"] | You can change the standard emoticons to your own (['👀', '<:bot:673508314008649749>']|
|more_reactions `<optional>`|                    `list`                   |["⬅", "➡", "⏪", "⏩"]|           You can change the standard emoticons to your own    |
| exit_reaction `<optional>`|                    `list`                   |["⏹"]|           You can change the standard emoticons to your own    |
|   language `<optional>`   |                     `str`                   |    `ru`    |                     Language selection (`ru`, `en`)                        |
|     color `<optional>`    |                     `int`                   |   `None`   |      You can set 1 color for all pages, HEX (0x000000)        |
|   footer_icon `<optional>`   |                     `str`                   |    `None`    |  The URL for the footer icon. Supported only HTTP(S).    |
|use_remove_reaction `<optional>`|             `bool`                 |   `True`   |   Disables remove_reaction, the user will remove the rules himself. (It should be set if the bot was denied rights on the server) |

### Examples of using

1. 2 reactions

```py
import discord
from discord.ext import commands
from Cybernator import Paginator

bot = commands.Bot(command_prefix="%")

@bot.command()
async def test(ctx):
    embed1 = discord.Embed(title="Страница 1", description='test 1')
    embed2 = discord.Embed(title="Страница 2", description='test 2')
    embed3 = discord.Embed(title="Страница 3", description='test 3')
    embed4 = discord.Embed(title="Страница 4", description='test 4')
    embeds = [embed1, embed2, embed3, embed4]
    message = await ctx.send(embed=embed1)
    page = Paginator(bot, message, only=ctx.author, use_more=False, embeds=embeds)
    await page.start()

bot.run(token)
```

![2 Реакции](https://github.com/RuCybernetic/myhelp/blob/master/Cybernetori/2reaction.gif)

2. 4 reactions

```py
import discord
from discord.ext import commands
from Cybernator import Paginator

bot = commands.Bot(command_prefix="%")

@bot.command()
async def test(ctx):
    embed1 = discord.Embed(title="Страница 1", description='test 1')
    embed21 = discord.Embed(title="Страница 2.1", description='test 2.1')
    embed22 = discord.Embed(title="Страница 2.2", description='test 2.2')
    embed31 = discord.Embed(title="Страница 3.1", description='test 3.1')
    embed32 = discord.Embed(title="Страница 3.2", description='test 3.2')
    embed33 = discord.Embed(title="Страница 3.3", description='test 3.3')
    embed34 = discord.Embed(title="Страница 3.4", description='test 3.4')
    embeds = [embed1, [embed21, embed22], [embed31, embed32, embed33, embed34]]
    message = await ctx.send(embed=embed1)
    page = Paginator(bot, message, only=ctx.author, use_more=True, embeds=embeds)
    await page.start()

bot.run(token)
```

![4 Реакции](https://github.com/RuCybernetic/myhelp/blob/master/Cybernetori/4reaction.gif)
