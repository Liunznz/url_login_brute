一款图形化的Web登陆页面弱口令批量爆破工具，指定登陆页面的url即可，支持解析HTML表单字段，支持普通登录与短信验证码登录，提供四种爆破模式、字典编码、表单自动解析等功能。已在多个本地靶场（如 VulHub、Pikachu 等）中验证通过。

# Web 登录页面弱口令爆破工具

> **⚠️ 法律与授权声明**  
> 本工具**仅限本地靶场环境、CTF比赛或已获得明确授权的系统进行安全测试**。严禁用于未授权的入侵、弱口令爆破等非法行为。使用者须自行承担一切法律责任。

---

## 📖 功能特性

- **多目标支持**：单个/批量导入 URL，顺序扫描
- **两种登录类型**：普通登录（用户名+密码）、短信登录（手机号+验证码）
- **字典增强**：
  - 用户名/密码独立选择编码方式（Base64 / URL / Hex / MD5 / SHA-1 / SHA-256）
  - 验证码生成器（4/6位数字，可自定义起始、结束、步长）
- **四种爆破模式**：Cluster bomb / Pitchfork / Sniper / Battering ram（Sniper 模式面板动态显示）
- **智能表单解析**：
  - 从原始 HTTP 请求导入
  - 从目标 URL 列表批量解析 HTML 表单（自动提取字段名、提交地址）
- **灵活的成功判定**：支持字符串、正则、JSON 字段（如 `code=1`、`id=0` 等）
- **实时监控**：每个目标独立进度条、状态、成功计数
- **结果导出**：仅导出成功凭证为 CSV 文件
- **便携性**：单一可执行文件，无需安装任何运行环境

---

## 🚀 快速上手（靶场测试示例）

### 1. 下载
- 从 [Releases]下载最新版 `url_login_brute.exe`

### 2. 使用步骤（以 VulHub 某登录框为例）
1. **添加目标**：输入靶机登录页面 URL（如 `http://192.168.1.100/login.php`）
2. **配置字典**：选择登录类型（普通/短信），导入常用弱口令字典或使用验证码生成器
3. **配置登录参数**：
   - 推荐使用“从 HTML 表单解析” → “批量解析所有目标” 自动提取字段名
   - 或手动指定 `username` / `password` 字段名
4. **选择爆破模式**：一般用 Cluster bomb（全组合）
5. **设置爆破成功/失败规则**：默认已包含 `string:login success`、`json:code=1` 等常用特征，也可以自定义添加
6. **开始扫描**：在“扫描监控”页查看每个目标的实时进度
7. **导出结果**：成功凭证保存为 CSV

### 3. 命令行参数
命令行输入url_login_brute.exe author回车   # 查看作者信息

### 4. 🖼️ 界面预览
目标设置
<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/0b5c94d6-729d-4420-b105-2ec77bd22e38" />
登录配置
<img width="1551" height="824" alt="image" src="https://github.com/user-attachments/assets/79115ac4-cd32-43c8-8976-1868022e08f7" />
字典设置
<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/2a2a1676-28f2-4ef3-aaf7-307fe73bc94f" />
爆破模式与规则
<img width="1920" height="1030" alt="image" src="https://github.com/user-attachments/assets/1ef281da-8353-4013-9c88-87678cb1b67d" />
扫描进度
<img width="1543" height="830" alt="image" src="https://github.com/user-attachments/assets/6314b081-e6e8-44a5-ae6f-e20fd45618ac" />
扫描结果
<img width="1530" height="819" alt="image" src="https://github.com/user-attachments/assets/25354426-bc98-4089-8aa3-b239105120d1" />

⚠️ 安全使用准则

1. 合法授权
   · 本工具仅限本地靶场、CTF 比赛或已获得书面授权的渗透测试项目使用。
   · 严禁对任何未授权的系统进行扫描、爆破或数据窃取。
2. 风险提示
   · 使用前请确保目标系统属于您自己的测试环境或已获得合法授权。
   · 频繁的弱口令攻击可能触发目标系统的安全防护机制，甚至导致账号锁定或 IP 被封。
3. 杀毒软件误报
   · 部分杀毒软件可能误报，请添加信任。
4. 责任豁免
   · 作者不承担任何因滥用本工具造成的一切法律责任。
