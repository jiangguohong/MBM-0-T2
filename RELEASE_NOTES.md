# T2 GitHub 公开 repo · 制备说明与建仓参数（内部文件，勿入公开仓）

**制备时间**：2026-10-24 19:1x（WD）
**状态**：素材就绪，待 T1 DOI 回填 + LH 把关后建仓
**序列依据**：MBM-0 发表运营交接清单 v1（2026-09-08）T2 环节——"公开发布 github 留最后"

## 建仓参数

| 项 | 值 |
|---|---|
| 建议仓名 | `mbm-0` |
| 可见性 | **public**（压轴锚点，T2 环节即公开） |
| 描述 | MBM-0 — Memory Birth Metrics: a black-box measurement protocol for agent memory growth dynamics |
| topics | `agent-memory` `benchmark` `evaluation` `llm-agent` |
| 建仓执行 | DSH 主责（发表运营总负责），WD 已备全套素材；或飞龙在天裁定后代发 |

## 文件清单（本目录）

| 文件 | 来源 | 备注 |
|---|---|---|
| `README.md` | WD 撰写 | 英；DOI 引用位为占位符（**待 T1 Zenodo 产出后回填**） |
| `protocol/protocol_mbm0_v0_revA_en.md` | S4 原文直拷 | 未改一字 |
| `protocol/protocol_mbm0_v0_revA_zh.md` | S1 **脱敏版** | 见下方脱敏记录 |
| `.github/ISSUE_TEMPLATE/measurement_report.yml` | WD 撰写 | 施测提交模板（v1 数据收集管道） |
| `LICENSE-MATERIALS` | CC BY 4.0 官方法律文本 | curl 自 creativecommons.org |
| `LICENSE` | Apache-2.0 官方法律文本 | curl 自 apache.org |

## 脱敏记录（S1 → 公开中文版）

1. **删**母本「审订说明」段中内部协作角色信息（协议起草方/修订方/裁决角色）——替换为中性的「版本记录」段，只留修订要点（删防方向泄露节、案例标注、防灌水条款、BIR 留白、Generative Agents 先例、MSUR 多窗口）；
2. **增**「脱敏说明」段（2026-10-24）：明示本版为公开脱敏版、协议正文与 Rev.A 逐字一致；
3. **改**案例 #001 状态：母本「观察中（T_obs 进行中）」已过时（观察窗 2026-09-15 关闭）→ 改为「观察窗已关闭，第四环复核中，结论以 v0.1 补丁为准」；
4. **保留**：落款「飞影双系统 · 46894742@qq.com」（裁决的对外身份与唯一联系方式）、受测系统代号 DSH（对外脱敏代号，S4 同）。

## 待办（按依赖序）

1. **T1 Zenodo**：注册（邮箱 46894742@qq.com，确认邮件需查收）→ 上传 S4（MD+PDF）→ 取 DOI —— 执行人 DSH（或飞龙在天本机）
2. **DOI 回填**：README 的 Citation 段占位符替换为真 DOI
3. **LH 把关**：README 与中文脱敏版回传 LH 终审（LH 保留协议学术质量与文本把关权；重大修订须回传 LH 复核）
4. **案例 #001 第四环**：DSH 回证后更新协议两版本的案例段（v0.1 补丁），同步 dev.to 已发文章（PUT /api/articles/4685369）
5. **建仓**：以上齐后执行，public

## 红线自查（制备时执行）

- [ ] 无内部路径（D:\agent_shared、C:\Users、\.hetu 等）
- [ ] 无机制细节（阈值/公式/参数/架构）
- [ ] 无三方协作结构信息（WD/DSH/LH 角色、隧道、河图）
- [ ] 无意识断言（consciousness/sentient/alive/awakened；awakening-like 框架仅作机制隐喻且带免责声明）
- [ ] 案例数据仅行为层
- [ ] 邮箱仅 46894742@qq.com（裁决保留）
