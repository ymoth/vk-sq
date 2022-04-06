# vk-sq
VK User-bot: Saint Quarter

Данный юзер-бот написан на Python с использованием асинхронных фреймворков Quart и VKQuick.

```python
# Сторона бота
@default_package.command("ping", "пинг")
async def test_on(context: vkquick.NewMessage):
    return f">> Ответ ~{abs(round(time.time() - context.msg.date.timestamp(), 5))} <3"

# Серверная часть. 
@server.route("/commands")
async def commands_get():
    # Обработка кода с командами в самом HTML-документе `commands.html`
    return await quart.render_template("commands.html", commands=app.commands)
```

### Установка
Windows:
```markdown
vk-sq_venv\Scripts\activate.bat
py -m src.api.server
```

Linux:

```markdown
source vk-sq_venv\Scripts\activate
python3.8 -m src.api.server
```

### Информация
```
Директория бота с командами: src/commands <br>
Директория панели управления: src/api/

После успешной установке, при запуске должно вывести в терминал примерно такой текст:

 * Serving Quart app 'src.api.server_utils'
 * Environment: production
 * Please use an ASGI server (e.g. Hypercorn) directly in production
 * Debug mode: True
 * Running on http://127.0.0.1:5000 (CTRL + C to quit)
[2022-04-05 13:43:14,455] Running on http://127.0.0.1:5000 (CTRL + C to quit)

```


# Заполнение данных
Данные пользователей по аунтетификации хранятся в configurations/auth.json <br>
Данные автоматически заполняются на сайте по url: `http://ip-adress:port/addAccount`
```json
{
     "users_on_long_poll": {
          "517921532": {
               "access_token": "$ACCESS_TOKEN (85)",
               "id": 608732541,
               "first_name": "Igor",
               "last_name": "Nezhivukh",
               "can_access_closed": true,
               "is_closed": true,
               "photo_200": "https://sun9-49.userapi.com/impg/a767sbC5sJS001aXhj82cN3z9OFnyG5U4c07XQ/AZdwEA_O3hc.jpg?size=1458x1458&quality=96&sign=a2e30c9fd5243ceef24bee0d4d28bfb1&type=album"
          }
     },

     "started_sessions_on_ids": [],
     "on_start_ids": [],

     "_description": "Перед изменением IP-Адресов советую обратиться к человеку, который знает что к чему и на какой хост.",
    
     // IP адресс можно заменить для локальной сети и управлять с телефона
     // IPv4 :: Заменять вместе с URL
     "ip": "127.0.0.1",
     "port": 5000,
     "url": "127.0.0.1:5000", 

     "secret_key_api_server_flask": "fURadfkk214IESFInQTIQaDIpUv1rUGYMDZJCSk7b0Lv6nD3Uuiz2sEq7TOSWo"
}
```

# Пример сайта, показ команд
<img src="https://psv4.userapi.com/c236331/u608732541/docs/d55/75d4dda6d541/Snimok_ekrana_2022-04-05_132609.png?extra=lz3im147-tFDKyhSUQ5lNkVeLpQRXPZ6kCOHA2X2VNzpQwMlW_0ufsI4uk3bJVJKscHB1i9Rq8a3bBPdF8Ny4foJjm_FwBZ_aMVGD5nRvF9k-S-qxc_OqQ2B8dB2z_YjzVk8RdusiTYvH7hul675Z-1F">
