# BotConnector
Connect your Minecraft server with the bot program via WebSocket  
通过WebSocket与Bot程序联动  

## Config 配置
```yml
# WebSocket Address WebSocket地址
url: 'ws://example.com'
# Server's Name 服务器名称
name: 'server'
# Authentication token 认证token
token: 'ffffffff-ffff-ffff-ffff-ffffffffffff'
# enable for true, disable for false true启用, false禁用
# Console Log Forward 控制台日志转发
ConsoleLogForward:
  enable: false
  filter:
    enable: true
    # blacklist 黑名单
    list:
      - 'WebSocketWrite'
      - 'WebSocketRead'
# Chat Message Forward 聊天消息转发
ChatEvent: false
# Player Login Event 玩家登录事件
PlayerLoginEvent: false
# Player Logout Event 玩家登出事件
PlayerLogoutEvent: false
# Player Command Event 玩家执行指令事件
PlayerCommandEvent: false
# Rcon Command Event Rcon执行指令事件
RconCommandEvent: false
```  

## JSON format JSON格式
All data will transfer in json format  
所有数据都将以json格式传输  
### Overview 总览
| key | value |  
| :-: | :-: |  
| `type` | Event type 事件类型 <br> String |  
| `username` | Player's username 玩家用户名 <br> String |  
| `uuid` | Player's uuid 玩家uuid <br> String |  
| `text` | text 文本 <br> String |  
| `command` | command 指令 <br> String |  
| `ip` | Player's ip 玩家ip <br> String |  
| `sn` | serial number 序号 <br> Long Int |  
| `name` | Server's name 服务器名称 <br> String <br> Special content `__ALL__` means all server 特殊内容 `__ALL__` 为全服务器|  
| `version` | Server's version 服务器版本 <br> String |  
| `onlinePlayer` | Server's online player's username 服务器在线玩家用户名 <br> List\<String\> |  
| `log` | log 日志 <br> String |  
| `return` | Remote command result 远程执行指令结果 <br> String |  
### Bot Received Bot程序接收
#### ConsoleLogForward
| key | value |  
| :-: | :-: |  
| `type` | `log` |  
| `log` | log 日志 <br> String |  
#### ChatEvent
| key | value |  
| :-: | :-: |  
| `type` | `Chat` |  
| `username` | Player's username 玩家用户名 <br> String |  
| `uuid` | Player's uuid 玩家uuid <br> String |  
| `text` | text 文本 <br> String |  
#### PlayerCommandEvent
| key | value |  
| :-: | :-: |  
| `type` | `PlayerCommand` |  
| `username` | Player's username 玩家用户名 <br> String |  
| `uuid` | Player's uuid 玩家uuid <br> String |  
| `command` | command 指令 <br> String |  
#### PlayerLoginEvent
| key | value |  
| :-: | :-: |  
| `type` | `Login` |  
| `username` | Player's username 玩家用户名 <br> String |  
| `uuid` | Player's uuid 玩家uuid <br> String |  
| `ip` | Player's ip 玩家ip <br> String |  
#### PlayerLogoutEvent
| key | value |  
| :-: | :-: |  
| `type` | `Chat` |  
| `username` | Player's username 玩家用户名 <br> String |  
| `uuid` | Player's uuid 玩家uuid <br> String |  
#### RconCommandEvent
| key | value |  
| :-: | :-: |  
| `type` | `RconCommand` |  
| `command` | command 指令 <br> String |  
#### Status 状态
| key | value |  
| :-: | :-: |  
| `type` | `status` |  
| `sn` | serial number 序号 <br> Long Int |  
| `version` | Server's version 服务器版本 <br> String |  
| `onlinePlayer` | Server's online player's username 服务器在线玩家用户名 <br> List\<String\> |  
#### Remote Command Return 远程执行指令返回
**Vanilla command can not get results at present, Only return `success` or `failure`**  
**原版指令目前还不能获得返回, 只能返回 `success` 或者 `failure`**  
| key | value |  
| :-: | :-: |  
| `type` | `command` |  
| `sn` | serial number 序号 <br> Long Int |
| `return` | Remote command result 远程执行指令结果 <br> String |  
### Bot Send Bot程序发送
#### Status 状态
| key | value |  
| :-: | :-: |  
| `type` | `status` |  
| `name` | Server's name 服务器名称 <br> String <br> Special content `__ALL__` means all server 特殊内容 `__ALL__` 为全服务器 |  
| `sn` | serial number 序号 <br> Long Int |
#### Remote Command Send 远程指令发送
| key | value |  
| :-: | :-: |  
| `type` | `command` |  
| `name` | Server's name 服务器名称 <br> String <br> Special content `__ALL__` means all server 特殊内容 `__ALL__` 为全服务器 |  
| `sn` | serial number 序号 <br> Long Int |  
| `command` | command 指令 <br> String | 

## Copyright notice 版权说明
Copyright 2021 hank9999  
Reference:
 - MessageInterceptingCommandRunner Class: [here](https://www.spigotmc.org/threads/how-do-i-get-the-output-of-dispatchcommand-command-when-called-by-callsyncmethod.354521/)  
 - How to get console log: [here](https://www.mcbbs.net/thread-1044570-1-1.html)  

## License
MIT License  