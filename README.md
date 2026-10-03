# antigravity_model

Sub2API 反重力模型目录的自维护名单。

Sub2API 把这份名单和社区目录 router-for-me/models 取并集，作为实际生效的模型目录。它决定两件事：哪些模型名可以调用，以及 `/v1/models`、分组候选模型、账号测试下拉里显示哪些模型。社区目录删掉的模型，只要还在这份名单里，就照样可用、照样显示。

## 文件

`models.json`，格式与社区目录相同：

```json
{
  "antigravity": [
    {"id": "模型 ID", "display_name": "显示名"}
  ]
}
```

## 编辑规则

- 必须是合法的 JSON；`antigravity` 是数组，可以为空。
- 每个 `id` 不能为空，名单内部不能重复；和社区目录重复没有关系，会自动去重。
- 文件不合法时，Sub2API 会忽略这次更新，继续使用上一次成功拉到的名单。

## 生效时间

Sub2API 每 3 小时拉取一次下面的地址，实例重启时也会立即拉取。改完推送到 `main` 后，所有实例最迟约 3 小时内生效；需要马上生效可以重启实例。

```text
https://raw.githubusercontent.com/andirtew/antigravity_model/main/models.json
```
