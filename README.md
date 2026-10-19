# Engineering Simulation Software Matrix

工程仿真软件与程序库的静态目录，包含交互式技术立方体、可搜索和筛选的软件卡片、本机提交表单，以及 JSON 导入 / 导出功能。界面与目录数据分开维护，支持独立部署到 GitHub Pages 或其他静态托管服务。

## 直接打开或本地运行

可以直接双击打开项目根目录的 `index.html`。页面内嵌了一份目录快照，因此在 `file://` 模式下也能显示软件数据；浏览器不允许此模式读取旁边的 JSON 文件。需要看到最新的 `data/software.json` 时，推荐在项目根目录启动静态 HTTP 服务：

```bash
python -m http.server 8000
```

然后访问 <http://localhost:8000>。HTTP 模式会从 `data/software.json` 加载最新数据；如果请求失败，页面会回退到内嵌目录快照。项目不需要 npm、构建步骤或后端服务。

## 数据格式

主数据文件为 `data/software.json`，顶层是软件记录数组。记录包含名称、链接、类别、许可证、六层功能覆盖、行业、案例、开发定位和备注。`layers6` 顺序固定为：

1. CAD / Geometry
2. Engineering Model
3. Material Model
4. Load Model
5. Analysis Solver
6. Results Analysis

`industries` 与 `useCases` 应使用字符串数组。旧记录中的单个字符串行业会在页面加载时自动兼容。覆盖标记：`●` 原生核心，`◐` 部分支持，`↗` 外部工具或自研，`—` 非核心，`?` 或“待核实”表示尚未确认。

当修改 `data/software.json` 后，请同步更新 `index.html` 中的内嵌目录快照，确保双击打开时也能看到相同数据。内嵌快照位于 `id="embeddedData"` 的 JSON 脚本块中。

## 浏览器内功能与数据保存

- 搜索软件名称、描述、行业和案例；按功能角色、许可证与开发定位筛选。
- 在立方体中旋转视图并选择软件查看详情；在软件目录中浏览完整卡片。
- 在“提交新软件 / 库”页录入、导出单条记录，或生成预填内容的 GitHub Issue。
- 导入或导出整个 JSON 目录。
- 表单修改保存在当前浏览器的本机存储中，不会自动写入仓库，也不会同步给其他访问者。清除浏览器网站数据会移除这些本机修改。

GitHub Pages 等静态托管不能替页面写入仓库。审核后的目录变更需要由维护者更新 `data/software.json` 和内嵌快照，再提交部署。GitHub Issue 功能只打开预填表单，不需要在网页中配置访问令牌。

## 数据质量说明

目录内容是工程软件调研草案。使用前请核实软件版本、许可证、功能覆盖、官方链接和案例适用性；页面展示不构成技术或采购建议。

## 发布到 GitHub Pages

仓库已包含 `.github/workflows/deploy-pages.yml` 自动部署工作流。将项目提交到 GitHub 仓库的 `main` 分支后，在仓库设置中打开 **Settings → Pages**，把 **Build and deployment → Source** 设为 **GitHub Actions**。之后每次推送到 `main` 都会自动发布；也可以在 **Actions** 页面手动运行 `Deploy GitHub Pages`。首次部署完成后，Pages 设置页会显示访问地址。

这是项目站点，访问地址通常为 `https://<用户名>.github.io/<仓库名>/`。若使用用户站点仓库 `<用户名>.github.io`，地址则为 `https://<用户名>.github.io/`。
