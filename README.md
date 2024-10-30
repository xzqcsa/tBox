# 测试配置链接（未填写夸克cookie）：https://ghp.ci/raw.githubusercontent.com/tBox2010/tBox/refs/heads/main/配置.json
# 建议将配置转存到自己的仓库，本仓库不做规则维护，现有规则仅供学习。

# T-Box App 使用指南

## 概述
T-Box 本身不包含任何配置，安装后需要用户自行在设置中填写配置链接。该应用无任何明广、暗广、后门，下载安装后用户需自行维护好规则，基本上能一直免费使用。请注意，应用本身不排斥科学上网工具，但出现视频列表加载失败的情况可能是由于视频站点本身不支持你的IP。

## 配置链接
配置链接支持以下几种方式：
- **HTTP链接**：直接使用HTTP链接。
- **带私人令牌的Gitee链接**：使用Gitee链接并添加私人令牌，可以有效保护你的配置或Cookie不泄露。例如，玩偶哥哥使用了夸克网盘的Cookie。

### Gitee私人链接配置方式
1. **创建非公开仓库**：在Gitee上创建一个非公开的仓库，然后上传你的配置文件。
2. **获取原始链接**：找到你的配置文件，点击原始链接后获取类似的链接：`https://gitee.com/用户名/t-box/raw/master/348z_xbiu.json`。
3. **添加私人令牌**：在链接后面添加上自己的私人令牌。私人令牌可以在 `https://gitee.com/profile/personal_access_tokens` 获取。获取后加到网址后面，形成一个新的链接：`https://gitee.com/用户名/t-box/raw/master/348z_xbiu.json?access_token=私人令牌`。

## 推荐播放器
- **流畅播放4K画质**：推荐播放器可以流畅播放4K画质视频。
- **手势控制**：
  - 左边上下滑动：调节亮度
  - 右边上下滑动：调节音量
  - 左边双击：快退10秒
  - 右边双击：快进10秒
  - 屏幕上左右滑动：拖动播放的进度条
- **双语切换**：部分双语视频可以自行切换声道。
- **兼容性**：很小一部分视频可能出现有声音没画面的情况，如不想切换其他源的话请在设置中切换至系统播放器。

## 系统播放器
- **播放4K视频**：播放部分4K视频可能稍卡顿，但兼容性高。

## 缓冲区大小
- **设置建议**：在播放视频时，缓冲越大播放越流畅。一般设置128M就够用了，最大可以设置256，但运行内存也会增加。（该设置仅针对推荐播放器）

## 配置类型说明
- `type=0`：苹果CMS影视对应的XML格式
- `type=1`：苹果CMS影视对应的JSON格式
- `type=2`：tvbox对应的xpath规则
- `type=3`：xbiu规则
- `type=4`：xbiubiu规则
- `type=5`：js爬虫脚本（对技术要求稍高）
- `type=6`：soup规则（推荐）

### 规则说明
- **xpath、xbiu、xbiubiu**：参考自tvbox的规则，理论上能跟tvbox对应的规则能直接套娃。（xbiu在解析部分站点的播放列表可能适配性不强，因代码参考自tvbox，不再进行特别优化，推荐使用soup规则）
- **soup规则**：使用起来较简单，能轻松适配大部分影视站点，推荐使用。

### type=5 补充说明
- **js脚本运行环境**：JavascriptCore。可能部分js代码无法直接运行，但是写简单的爬虫一般够用。

## 配置示例
```json
{
    "key": "wogg",  //每个站点的key需独立，不能用同一个key，key用以储存本地配置文件
    "name": "玩偶哥哥",//站点名称（如无特殊情况，不要频繁改动站点名称，涉及到本地历史、收藏记录等）
    "type": 5,
    "searchable": 1, //是否支持搜索 1=支持 0=不支持
    "filterClass": "", //过滤分类名称（多个分类用,逗号隔开）
    "firstClass": "", //将指定分类名称前置（多个分类名称用,逗号隔开）
    "filterPlay": "",  //过滤播放源名称（多个播放源用,逗号隔开）
    "firstPlay": "夸克网盘,夸克网盘2", //将指定播放源名称前置（多个源名称用,逗号隔开）
    "ext": "https://gitee.com/用户名/t-box/raw/master/js/wogg.js?access_token=私人令牌",//配置链接（支持带私人令牌的gitee链接）
    "flagable": 0, //是否需要vip或播放器解析播放 1=需要  0=不需要（youku、qq、iqiyi等需要解析，如网页嗅探视频的话部分网站已内置了vip解析）
    "filterPlayFileKeywords": "", //嗅探网页时过滤的视频链接关键字，过滤掉的链接不会取过来（多个关键字用,逗号隔开）
    "keepPlayFileKeywords": "" //嗅探时采用的视频链接关键字，app已支持大部分视频链接的嗅探，一般不需要特别设置（多个关键字用,逗号隔开）
}
```
