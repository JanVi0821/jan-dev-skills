# jan-dev-skills

`jan-dev-skills` 是一组可独立安装的个人 Agent Skills。每个 skill 都提供明确的触发条件、执行流程和项目规范，可以按需安装到支持 [Agent Skills](https://agentskills.io/) 的编码代理中。

## Skills

### jan-fe-dev

用于创建、搭建、重构或规范化前端项目，覆盖 Astro、React、Vue、Next.js、TypeScript 和 Tailwind CSS。

主要能力：

- 在创建项目前确认项目名称、用途和 SEO 需求。
- 根据项目类型推荐 Astro、React、Vue 或 Next.js，并由用户最终选择。
- 初始化 Git、TypeScript、环境变量文件、Tailwind、状态管理、TanStack Query 和 Zod。
- 根据项目名称生成并应用 `favicon.svg`。
- 统一组件、页面、样式、图标、测试和 Agent 指令文件规范。
- 对现有项目进行增量规范化，保留框架约定和已有有效实现。

查看完整说明：[skills/jan-fe-dev/SKILL.md](./skills/jan-fe-dev/SKILL.md)

## 安装

确保本机已安装 Node.js，并且可以使用 `npx`。

将 `jan-fe-dev` 全局安装到 Codex：

```bash
npx skills add JanVi0821/jan-dev-skills --skill jan-fe-dev --global --agent codex --yes
```

参数说明：

- `--skill jan-fe-dev`：只安装仓库中的 `jan-fe-dev`。
- `--global`：安装到用户级目录，使所有项目都可以使用。
- `--agent codex`：只安装到 Codex。
- `--yes`：跳过交互式确认。

如果希望安装到当前项目，请移除 `--global`：

```bash
npx skills add JanVi0821/jan-dev-skills --skill jan-fe-dev --agent codex --yes
```

安装完成后，在新的 Codex 任务中使用 `$jan-fe-dev`，或直接提出创建、编写、重构及规范化前端项目的请求。

## 查看可用 Skills

```bash
npx skills add JanVi0821/jan-dev-skills --list
```
