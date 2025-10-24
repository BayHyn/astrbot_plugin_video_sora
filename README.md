# ⚡ AstrBot Sora 视频生成插件 ⚡

<div align="center">

![:访问量](https://count.getloli.com/@astrbot_plugin_video_sora?name=astrbot_plugin_video_sora&theme=rule34&padding=7&offset=0&scale=1&pixelated=1&darkmode=auto)


[![License](https://img.shields.io/badge/License-MIT-green.svg)](https://opensource.org/licenses/MIT)
[![Python 3.10+](https://img.shields.io/badge/Python-3.10%2B-blue.svg)](https://www.python.org)
[![AstrBot](https://img.shields.io/badge/AstrBot-4.0%2B-75B9D8.svg)](https://github.com/AstrBotDevs/AstrBot)
[![Sora](https://img.shields.io/badge/OpenAI%20Sora-2-00aaff.svg)](https://sora.com)

</div>

## 介绍
通过调用 OpenAI Sora 的视频生成接口，实现机器人免费生成高质量视频并在聊天平台中发送的功能。支持配置正向代理和反向代理，适应复杂的网络环境。  
本插件适用于 [AstrBot](https://github.com/AstrBotDevs/AstrBot) 框架，[帮助文档](https://astrbot.app)。

## 获取网页鉴权（accessToken）
1. 登录 https://chatgpt.com
2. 打开 https://chatgpt.com/api/auth/session
3. 复制返回内容中的 accessToken 字段填写进插件配置，不需要加 `Bearer ` 前缀。
4. 打开 https://sora.com 检查账号是否有sora的使用权限。注意是新版 Sora。

## 使用说明
生成视频：
- /sora [横屏|竖屏] <提示>
- /生成视频 [横屏|竖屏] <提示>
- /视频生成 [横屏|竖屏] <提示>
- [横屏|竖屏] 参数是可选的

查询与重试：
- /sora查询 <task_id>  
- /sora强制查询 <task_id>  
可用来查询任务状态、重放已生成的视频或重试未完成的任务。强制查询将绕过数据库缓存的任务状态，从官方接口重新查询任务情况。

检测鉴权有效性：
- /sora鉴权检测  
仅管理员可用，一键检查鉴权是否有效。

## 反向代理
提供一个实验性的 <span style="color: #ff69b4;">Zako\~♡Zako\~♡</span> 反向代理，目前属于单节点单IP部署，暂不明确是否存在429等防刷机制。坏了可能来不及修复，请谨慎使用。  
使用方法：  

- 将三个URL输入框（sora_base_url、chatgpt_base_url、speed_down_url）的内容全部改成 https://sora.zakozako.de
- speed_down_url_type 选项选择 <b>替换</b> 即可。  

这个反向代理设置了较严格的访问频率限制和带宽控制，对于几个账号的日常使用应该已经足够了。如果你有更高的使用需求，相信你一定有自行解决网络问题的能力。

## 并发控制与错误提示
- 支持自定义并发数；无可用 token 时会提示并发过多或未配置。
- 任务状态同步更新到sqlite3数据库，可在插件数据目录导出video_data.db文件。

## 故障排查
- 网络相关错误：检查代理或主机网络访问能力，已知部分国家网络无法访问sora，例如新加坡。
- 权限问题：检查账号是否有生成视频的权限，登录 https://sora.com 直接生成一个视频看看。

## 风险提示
- 本插件基于逆向工程技术调用官方接口，存在封号风险，请谨慎使用。
- 如果使用反向代理，请确保反向代理的来源可信，以保证账号安全。
