### Параметры
|           Имя             |                     Тип                     |По умолчанию|                           Информация                                |
|:-------------------------:|:-------------------------------------------:|:----------:|:-------------------------------------------------------------------:|
|           ctx             | `discord.Client` `discord.ext.commands.Bot` |            |                                                                     |
|         message           |              `discord.Message`              |            |       Сообщение с вашим embeds        |
|          embeds           |                    `list`                   |   `None`   |                        Список embeds                              |
|    timeout `<optional>`   |                    `int`                    | `30`секунд |        Таймер работы Paginator           |
|   use_more `<optional>`   |                    `bool`                   |   `False`  |            Добавление 2/4 реакций (По умолчанию 2)                  |
|   use_exit `<optional>`   |                    `bool`                   |   `False`  |            Добавление реакции для отключения Paginator                 |
|delete_message `<optional>`|                    `bool`                   |   `False`  |Удалить Paginator по истечении таймера(если False, то уберет реакции)|
|      only `<optional>`    |              `discord.abc.User`             |   `None`   |    Автор использующий команду (ctx.author)   |
|  time_stamp `<optional>`  |                    `bool`                   |   `False`  |                 Добавление времени вызова команды ([timestamp](https://discordpy.readthedocs.io/en/latest/api.html#discord.Embed.timestamp))                  |
|    footer `<optional>`    |                    `bool`                   |   `True`   |      Вкл./откл. [footer](https://discordpy.readthedocs.io/en/latest/api.html#discord.Embed.footer) (Подпись Раздел-Страница)                         |
|   reactions `<optional>`  |                    `list`                   |["⬅", "➡"] | Можно стандартные смайлики поменять на свои (['👀', '<:bot:673508314008649749>']|
|more_reactions `<optional>`|                    `list`                   |["⬅", "➡", "⏪", "⏩"]|           Можно стандартные смайлики поменять на свои    |
| exit_reaction `<optional>`|                    `list`                   |["⏹"]|           Можно стандартный смайлик поменять на свой    |
|   language `<optional>`   |                     `str`                   |    `ru`    |                     Выбор языка (`ru`, `en`)                        |
|     color `<optional>`    |                     `int`                   |   `None`   |      Можно установить 1 цвет на все страницы, HEX (0x000000)        |
|   footer_icon `<optional>`   |                     `str`                   |    `None`    |  URL-адрес значка нижнего колонтитула. Поддерживается только HTTP(S).    |
|use_remove_reaction `<optional>`|             `bool`                 |   `True`   |   Отключает remove_reaction, пользователь будет сам убирать реакции. (Стоит ставить если боту запретили права на сервере) |

### Примеры использования

1. С 2'мя реакциями

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

2. С 4'мя реакциями

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
