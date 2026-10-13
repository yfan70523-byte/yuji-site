# 玉记本地字体

- 上游：https://github.com/notofonts/noto-cjk
- 固定提交：f8d157532fbfaeda587e826d4cd5b21a49186f7c
- 书册字体：Serif/Variable/TTF/Subset/NotoSerifSC-VF.ttf，保留 400–600 字重。
- 操作字体：Sans/Variable/TTF/Subset/NotoSansSC-VF.ttf，固定 400 字重。
- 授权：SIL Open Font License 1.1，完整原始许可见 OFL.txt。
- 子集修改后的内部字体名称：Yuji Book Subset / Yuji UI Subset。

用 fontTools 提取 index.html、src/*.js 中的字符及 ASCII，保留竖排标点特性，导出 WOFF。字符子集随当前文案重建，最新体积与 SHA-256 见 build.json。使用 WOFF 是为了复用现有 Python 环境，不增加 Brotli 构建依赖。

增加页面或动态文案后，下载上述固定提交的两个 TTF 与 Serif/LICENSE、Sans/LICENSE，按 scripts/build-book-fonts.py 文档重建。生成用的原始 TTF 位于 D 盘工具目录，不属于网站运行文件。scripts/build-book-fonts.py 同时读取 source.json（repo、commit）记录来源。

正文中不在子集内的用户输入由系统宋体回退；控件由系统黑体回退。font-display: swap 确保字体被阻止或下载失败时文字仍然显示。网站运行期间不请求远程字体服务。
