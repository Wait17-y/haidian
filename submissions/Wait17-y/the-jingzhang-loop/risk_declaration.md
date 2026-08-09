# F5: Risk Management Declaration
## 京张AI创新带城市设计 — 提交风险声明

> 本文件声明提交包中识别的风险及其缓解措施。所有风险均在当前项目约束（AI辅助、控规缺失、概念阶段）下评估。

---

## 1. Narrative Risk (叙事风险)

**Risk ID:** RISK-NAR-001
**Severity:** Medium
**Status:** Mitigated

### 风险描述
提案的叙事逻辑可能被误读为"设计方案"而非"概念建议"。The Loop 三层模型、一轴三区等框架性表述可能给人以确定性的错觉，超出实际规划层级。

### 缓解措施
- `proposal.md` 前置 Disclaimer（8项声明）明确"概念边界 ≠ 规划边界"
- 全文中 `概念建议` 出现 >100 次，`概念基准` >20 次，`参考方案` 广泛使用
- 所有 GeoJSON metadata 标记 `boundary_type: "provisional_bbox"`，`legal_status: "not_statutory_planning_boundary"`
- 所有指标表述为 `Innovation Capacity`，附 `legal_note`
- `agent.json` 声明 AI 辅助生成

### 残余风险
- 读者可能忽略前 Disclaimer 直接阅读正文
- 图表中空间表达可能被脱离文字引用

---

## 2. Planning Authority Risk (规划权限风险)

**Risk ID:** RISK-PLA-001
**Severity:** High
**Status:** Mitigated

### 风险描述
5项控规条件全部缺失（FAR/建筑高度/建筑密度/绿地率/建筑退线）。在此条件下提出的空间概念建议不能直接用于规划审批。任何将概念面积、容积率建议、高度概念解读为法定规划指标的行为均构成越权。

### 缓解措施
- `compliance_matrix.json` 记录25项约束检查，5项控规明确标记"缺失"
- `assumptions.json` 记录6项关键假设含 `confidence` 和 `impact` 评估
- `design_depth_matrix.json` 定义10项空间策略为"概念基准深度"
- `proposal.md` Ch0 Pre-Disclaimer §2: 声明控规缺失
- Phase 1 优先低成本可逆措施（弹性空间、界面激活），避免不可逆投资

### 残余风险
- 评审者可能将"概念建议"的量化数值（如 ~10 ha、~8 ha）误认为法定指标
- 后续正式规划阶段可能与概念方案存在重大偏差

---

## 3. Evidence Risk (证据风险)

**Risk ID:** RISK-EVI-001
**Severity:** Medium
**Status:** Mitigated

### 风险描述
提案的核心证据来源为 OSM 开放数据 + 公开对标研究 + Agent 分析推导。OSM 数据存在标签不完整、时效滞后问题。全球对标（Kendall/Station F/Shibuya）基于公开可获取的二手信息，未进行实地验证。空间边界为矩形 bbox，不反映实际地块权属。

### 缓解措施
- `sources.json` 记录6项数据来源及其局限性
- `traceability.json` 9条推导链完整记录 Source → Finding → Strategy → Design Decision → Drawing → Metric
- `assumptions.json` 的 `confidence` 字段为每条假设标注可信度（high/medium/low）
- 全球对标的技术指标（空间质量评分等）明确标注为"公开综合评估/概念参考"
- 所有面积数值标注为"概念参考基准"

### 残余风险
- OSM 数据精度可能影响建筑高度分类的准确性（64%低层占比基于有标签样本）
- 全球对标评分体系的主观性无法完全消除

---

## 4. Technical Risk (技术风险)

**Risk ID:** RISK-TEC-001
**Severity:** Low
**Status:** Accepted

### 风险描述
- CI/CD 类渲染工具（Poppler/WeasyPrint）在 Windows 环境下未安装，PDF 通过 matplotlib PdfPages 生成
- 06_design_logic_diagram.png 的 CJK 字体回退可能产生 tofu（方块字符），取决于运行环境的字体可用性
- proposal.en.md 通过 Kimi-k3 API 分段翻译，术语一致性未经人工校对

### 缓解措施
- `submission_manifest.md` 记录文件版本与生成方式
- F4 预检脚本验证所有文件的完整性和格式正确性

---

## 5. Participation Risk (参与风险)

**Risk ID:** RISK-PAR-001
**Severity:** Low
**Status:** Accepted (Inherent)

### 风险描述
作为 AI 辅助的单人提交（`agent.json` 声明），成果未经过多专业团队协作审查、公众参与或 stakeholder 验证。城市设计通常需要规划师、建筑师、交通工程师、景观设计师等多专业协作。

### 缓解措施
- `agent.json` 透明声明 AI 辅助生成
- 共创章程（Taskbook）明确 agent 成果的开放共创性质
- 方案内置 Citizen AI Participation Model 作为后续真实参与的框架

---



---

## AI Usage Statement

AI tools (Codex GPT-5 by OpenAI, Kimi-k3 by Moonshot AI) were used in this project for:

- **Data organization**: Structuring spatial data, matrix generation, and file inventory management
- **Drafting assistance**: Initial proposal text generation, English translation (Kimi-k3)
- **Consistency checking**: Validation scripts, cross-reference verification, compliance matrix generation

**Human control and review**: All final design decisions — including The Loop framework, three-district positioning, spatial strategies, and scenario narratives — were reviewed and controlled by the project participant (Wait17-y). The AI served as an analytical and drafting assistant, not an autonomous designer. All outputs were calibrated against:

- Planning constraints documented in Stage A6 (5 planning control items all missing)
- The Co-Creation Charter (Taskbook), specifically Charter.3 (agent outputs are open co-creation suggestions, not substitutes for professional planning)
- Professional urban design standards referenced in standard_matrix.json

This transparency statement is also recorded in machine-readable form at `matrices/agent.json`.

## Risk Summary Matrix

| Risk ID | Category | Severity | Status | Key Mitigation |
|---------|----------|----------|--------|----------------|
| RISK-NAR-001 | Narrative Risk | Medium | Mitigated | Disclaimer + 概念建议 wording |
| RISK-PLA-001 | Planning Authority | High | Mitigated | 5项控规标记缺失 + Innovation Capacity metrics |
| RISK-EVI-001 | Evidence Risk | Medium | Mitigated | Traceability chains + assumption confidence |
| RISK-TEC-001 | Technical Risk | Low | Accepted | Manifest + Preflight |
| RISK-PAR-001 | Participation Risk | Low | Accepted | agent.json transparency |

---

## Sign-off

本风险声明基于2026-08-08提交版本的完整审查。
所有 HIGH/MEDIUM 风险已实施缓解措施。
LOW 风险已记录并被接受为项目约束的内在特征。

**提交者:** Wait17-y (Codex GPT-5 Assisted)
**审查状态:** Self-reviewed, F4 validated
**下一步:** 正式规划阶段需补充控规数据并进行多专业团队验证
