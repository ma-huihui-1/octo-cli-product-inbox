# octo-cli-product-inbox

这是 AINOL Agent 实操考核中用于管理 `octo-cli` 反馈、需求和 PRD 流程的 GitHub 需求池。

目标产品：[`Mininglamp-OSS/octo-cli`](https://github.com/Mininglamp-OSS/octo-cli)

本仓库只用于：

- 记录 bug 反馈
- 记录 feature 新需求
- 记录产品问题
- 沉淀 PRD
- 跟踪 review 和状态变化

注意：目标仓库 `Mininglamp-OSS/octo-cli` 只读，不在本仓库中修改目标产品源码。

---

## Issue 类型

本仓库提供 4 类 issue 模板：

| 模板 | 用途 |
|---|---|
| Bug 反馈 | 记录异常、报错、与预期不一致的问题 |
| Feature 新需求 | 记录新功能、新能力、新场景 |
| Question 产品问题 | 记录产品问题、使用咨询、需要解释的内容 |
| PRD 模板 | 将已确认需求整理成产品需求文档 |

---

## Label 体系

每个 issue 至少包含 4 类标签：

1. `type/*`：这是什么类型的事
2. `priority/*`：这件事有多急
3. `status/*`：当前处理到哪一步
4. `source/*`：这个 issue 从哪里来

如果进入 PRD review，再增加：

5. `review/*`：PRD 审核状态

示例：

```text
type/feature
priority/P1
status/in-review
source/exam
review/requested
```

---

## PM 流程

本仓库的需求流转流程为：

```text
收到反馈
↓
创建 issue，并打 type / priority / status / source 标签
↓
确认是否值得处理
↓
进入 PRD 编写
↓
提交 review
↓
根据 review 结果修改或完成
```

对应状态标签：

```text
status/new
status/needs-info
status/accepted
status/in-prd
status/in-review
status/rejected
status/done
status/wontfix
```

---

## PRD 规则

PRD 只写 What，不写 How。

不要写：

- 技术实现方案
- 数据库、Redis、接口、代码
- 内部字段名
- “接口返回 200”这类技术验收标准

应该写：

- 用户遇到了什么问题
- 用户希望完成什么
- 用户可以看到什么结果
- 用户失败时能否知道原因
- 用户需要多久完成操作

---

## Review 规则

PRD 完成后，issue 会进入：

```text
status/in-review
review/requested
```

如果 reviewer 要求修改，则进入：

```text
status/rejected
review/changes-requested
```

如果 review 通过，则进入：

```text
status/done
review/approved
```

---


## 安全红线

本仓库不记录任何 token、API key、密码或其他凭证。
如果需要验证权限，只记录验证结果，不展示凭证内容。

---

## 定时扫描规则

Agent 会定时扫描本仓库 issue 的变化，包括：

- 新 issue
- label 变化
- close / reopen
- reviewer 评论
- wontfix / rejected / done 状态变化

如果没有变化，不发送过程消息。

如果发现变化，需要在考试群中汇报，并 @ 主考。
