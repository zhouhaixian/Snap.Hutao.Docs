---
headerDepth: 2
icon: ask
category: [FAQ]
order: 1
redirectFrom: /advanced/FAQ.html
comment: false
---

# 常见问题

## 如何创建胡桃的桌面快捷方式

::: tip 社区力量
感谢 [CzHUV 提供的解决方案](https://github.com/DGP-Studio/Snap.Hutao.Docs/issues/12)
:::

- `Win+R` 呼出运行窗口，在窗口中输入`shell:AppsFolder`
  ![Run](https://img.alicdn.com/imgextra/i3/1797064093/O1CN01Jj8c6i1g6du728e5A_!!1797064093.png_.webp)
- Windows 会弹出应用程序目录，找到胡桃工具箱
- 右键，点击`创建快捷方式`
- 根据提示操作你就可以获得一个桌面快捷方式了

## 如何添加一个默认以管理员方式运行的快捷方式

::: tip 社区力量
感谢 [Parsifa1 提供的解决方案](https://github.com/DGP-Studio/Snap.Hutao.Docs/issues/17)
:::
基本原理：使用下方的 PowerShell 脚本可以以管理员方式运行胡桃

```PowerShell ts:no-line-numbers
Start-Process shell:AppsFolder\60568DGPStudio.SnapHutao_ebfp3nyc27j86!App -verb runas
```

- 在桌面点击右键，选择`新建` -> `快捷方式`
- 在`请键入对象的位置`中直接输入:

```PowerShell ts:no-line-numbers
  powershell -Command "Start-Process shell:AppsFolder\60568DGPStudio.SnapHutao_ebfp3nyc27j86!App -verb runas
```

- 将快捷方式命名为你需要的名称，比如`Snap Hutao`
- 确认创建，此时你会在桌面得到一个有 PowerShell 图标的快捷方式
- 右键该快捷方式，点击属性
  - 将`运行方式`修改为`最小化`
  - 点击更改图标，选择`浏览`，并填写：`%ProgramFiles%\WindowsApps\60568DGPStudio.SnapHutao_1.6.6.0_x64__ebfp3nyc27j86\Snap.Hutao.exe`，回车确认保存
- 这样你就获得了胡桃工具箱的桌面快捷方式，并且运行它将直接以管理员模式运行
  - 你也可以将固定到任务栏或磁贴区

## 如何让胡桃工具箱开机自动启动

- 请参考如下思路
  - 可以自行创建一个批处理文件，内容参考[此 issue](https://github.com/DGP-Studio/Snap.Hutao/issues/184)中，令胡桃以管理员模式直接运行的命令。
  - 设置一个**计划任务程序**令上述批处理文件开机自启，或将上述批处理文件加入**启动项**中
- 或有其他令胡桃工具箱可开机自启的思路，可自行探索

## 如何通过胡桃工具箱快速地启动游戏

- 在主程序中正确设置高级启动器功能
- 将胡桃工具箱在系统中固定在快速启动栏中
- 在快速启动栏中右键胡桃应用程序

  ![quick-start](https://img.alicdn.com/imgextra/i3/1797064093/O1CN01Uu8QzN1g6du6MRp8h_!!1797064093.png_.webp)

- 选择`启动游戏`即可

## 如何通过网络代理使用胡桃工具箱

参考 [HttpRequestException 错误](exceptions.html#httprequestexception) 文档

## 为什么程序会出现乱码现象

- 当用户在 Windows 10 下使用胡桃且发现有乱码情况时：
  - 可以下载 `Segoe Fluent Icons`字体
  - 安装时选择`为系统所有用户安装`，即可解决问题
- 您可以从 [微软官方](https://aka.ms/SegoeFluentIcons)下载到该字体文件

## 为什么会弹出需要使用新应用以打开的对话框

![uninstall-error](https://img.alicdn.com/imgextra/i3/1797064093/O1CN01b3j0eY1g6duBXLJXg_!!1797064093.jpg_.webp)

如在卸载胡桃工具箱后出现如上图所示的`需要使用新应用以打开此 hutao 链接`，说明没有按文档要求在卸载前清除实时便笺定时任务。
请根据文档在设置中清除定时任务后再卸载胡桃工具箱。

- 如果你在系统定时任务中找不到胡桃的定时任务，但问题仍然出现，请参考[这份文档](https://github.com/DGP-Studio/Snap.Hutao.Docs/issues/18)来解决

## 为什么米游社帐号登录状态经常失效，添加的帐号消失

- 我们通过储存帐号的米游社 Cookie 来维持登录状态。
- 但是当用户在浏览器或其它设备上**注销帐号**后， 维持登录状态的 Cookie 将**失效**。
- 这会导致胡桃工具箱上的米游社帐号在启动后被自动移除。
- 此情况也可能因为网络连接问题导致无法检查 Cookie 有效性，故出现此情况后请优先重启胡桃工具箱。
- 自 2022 年 10 月起，米游社极大地提高了账号被判定为有风险的概率，[账号有风险](exceptions.md#状态1034-验证失败)时亦会令 Cookie 无法被识别为有效状态
- 自 1.4.15 版本起，你可以通过在帐号面板中刷新 Cookie 来刷新登录状态

## 为什么游戏登录状态会失效，导致切换帐号功能无效

- 保存游戏登录状态的要素有两个：网络环境和设备 ID
- 导致该问题的常见原因是：
  - 网络环境频繁变换，如公网 IP 更换
  - 操作失误，导致实际上根本没有保存登录状态（空的登录状态无法避免被胡桃识别）
    - 确认你的帐号已登录后，进入游戏
    - 关闭游戏后，确定游戏进程已关闭
    - 再次进行帐号检测，来添加登录状态

## 为什么程序会提示注册计划任务失败

使用管理员模式使用一次实时便笺后，胡桃的任务计划会被以管理员权限创建。当再次以非管理员模式启动胡桃时，程序在修改计划任务时会缺少权限。
继续使用管理员模式即可解决该问题。

## 使用 MSIX 安装包安装时进度卡在`正在安装所需框架`

- 当用户系统缺少必要依赖环境时，系统会自动安装所需依赖。若用户禁用了 Windows Update 组件或网络条件差时，系统无法完成该步骤。
  - 请确保 Windows Update 已启用；胡桃工具箱升级同样依赖于 Windows Update 组件
  - 你亦可以手动下载并安装[胡桃的相关依赖](https://d.hut.ao/releases/Dependency)

## 无法使用管理员模式启动胡桃工具箱

> 该问题仅存在于 Windows 10 低于 22H2 的版本中

- 当用户系统版本低于 `Windows Build 19045`（即 Windows 10 22H2 版本）时，可能无法通过管理员模式启动胡桃工具箱
  - 该问题属于 Windows 内核级别问题，难以判断具体来源，故建议用户升级至 Windows 10 最新版本

## 转换服务器失败后如何恢复游戏程序

::: info 功能原理说明
胡桃客户端始终只从原神官方服务器下载转换服务器需要的文件，这保证了用户不会下载到被第三方篡改的危险程序。
如果你在转换到某一种目标服务器时频繁因网络问题而转换失败，则意味你的网络到目标的原神官方服务器连接质量差。
你应检查你的互联网连接、联系你的运营商或向专业人士咨询以保证你的正常使用体验。
:::

在转换原神服务器时，如果胡桃客户端意外退出或由于用户侧网络问题会导致转换流程中断并进而导致原神客户端损坏。
此时胡桃工具箱会提示 `游戏路径不正确，前往设置更改游戏路径`，而游戏路径下此时可能不存在任何游戏主程序文件，导致用户无法正确设置。

在这种情况下，用户可以执行下面的步骤**手动将胡桃客户端备份的游戏主程序恢复至原本的游戏目录中**或**直接使用官方启动器修复游戏**。

在开始手动恢复游戏程序之前，你需要知道以下基本知识：

1. 关于游戏客户端
   1. 国服原神客户端目录下有名为 `YuanShen.exe` 的游戏主程序和名为 `YuanShen_Data` 的游戏程序目录
   2. 国际服原神客户端目录下有名为 `GenshinImpact.exe` 的游戏主程序和名为 `GenshinImpact_Data` 的游戏程序目录
2. 关于胡桃客户端转换服务器功能下的备份步骤
   1. 在转换服务器前，胡桃客户端会备份当前游戏客户端的主程序以及国服/国际服客户端专有的一些组件程序，即 `exe` 主程序和 `_Data` 目录
   2. 备份文件储存于当前 Windows 用户下的文档库中的 `Hutao/ServerCache` 目录下，即 `%userprofile%/Documents/Hutao/ServerCache`

手动恢复游戏主程序步骤（此处以国际服转国服为例）：

1. 进入胡桃用于备份游戏主程序的 `ServerCache` 目录，此时该目录下存放着转换前的游戏程序备份文件，即 `GenshinImpact.exe` 和 `GenshinImpact_Data`
2. 进入游戏主程序目录，此时既没有 `YuanShen.exe` 也没有 `GenshinImpact.exe`，并且有一个国服目录 `YuanShen_Data`
3. 手动将游戏主程序目录下的 `YuanShen_Data` 文件夹更名为 `GenshinImpact_Data`
4. 手动将 `Hutao/ServerCache` 下的 `GenshinImpact.exe` 和 `GenshinImpact_Data` 复制回游戏主程序目录中并覆盖当前已有文件
5. 此时你的游戏客户端应已恢复正常
6. 重新进入胡桃客户端的 `游戏启动器` 界面，`游戏路径不正确` 错误应不再出现，且`服务器`设置一栏为空。此时，你可以选择原本的服务器版本（国际服）
   并立刻启动游戏，或选择新的服务器目标（国服）并转换客户端版本。
