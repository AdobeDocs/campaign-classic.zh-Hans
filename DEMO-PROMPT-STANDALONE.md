---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---
# 🚀演示提示 — v7到v8文档分析

**将此整个提示复制并粘贴到Cursor/ChatGPT中以分析任何v7文件夹**

&#x200B;---

## 📋提示（从此处复制）⬇️

```markdown
# Campaign v7 Documentation Analysis

Analyze the v7 documentation folder and generate a detailed Markdown report with recommendations.

---

## CONTEXT

**v7 Repository**: `/Users/florentvignes/Documents/GitHub/campaign-classic.en/`  
**v8 Repositories**:
- `/Users/florentvignes/Documents/GitHub/campaign.en/` (Campaign v8)
- `/Users/florentvignes/Documents/GitHub/campaign-web.en/` (Campaign Web UI v8)

---

## TARGET FOLDER

**Analyze this folder**: `/Users/florentvignes/Documents/GitHub/campaign-classic.en/help/delivery/using/`

*(Replace with any folder: workflow, web, platform, reporting, etc.)*

---

## FEATURE PARITY CONTEXT

### v7-Specific Features (NOT in v8 FFDA)
- **Coupons** (personalized-coupons.md)
- **MRM** (Marketing Resource Management)
- **Surveys** (online surveys)
- **Distributed Marketing**
- **Mid-sourcing** (on-premise setup)
- **SpamAssassin** (on-premise spam filtering)
- **On-premise/Hybrid** configurations

### v8 Documentation Structure
- **Campaign Web UI**: `/campaign-web.en/help/v8/` - https://experienceleague.adobe.com/en/docs/campaign-web/v8/
- **Campaign v8**: `/campaign.en/help/v8/` - https://experienceleague.adobe.com/en/docs/campaign/campaign-v8/

---

## OUTPUT FORMAT

Generate a complete Markdown report with this structure:

### 1. HEADER & SUMMARY
\`\`\`markdown
# 📊 v7 [Folder Name] Analysis

**Folder**: `/help/[folder]/using/`  
**Generated**: [Date]  
**Total Files**: [X]

## 📈 Summary

| Metric | Count | Percentage |
|--------|-------|------------|
| 📄 Total Files | X | 100% |
| ✅ KEEP | X | X% |
| 🗑️ DELETE | X | X% |
| ➡️ MOVE | X | X% |
| 🔍 REVIEW | X | X% |
\`\`\`

### 2. FILE-BY-FILE ANALYSIS TABLE
\`\`\`markdown
## 📋 Complete File Analysis

### [Category Name] (X files)

| # | v7 File | v8 Match | Match % | Notes | Action |
|---|---------|----------|---------|-------|--------|
| 1 | filename.md | [v8 link](https://...) | 95% | Fully in v8 | 🗑️ DELETE |
| 2 | **filename.md** | NONE | 0% | **v7-specific** | ✅ **KEEP** |
| 3 | filename.md | [v8 link](https://...) | 70% | Migrate tips | ➡️ MOVE |

[Repeat for each category: Get Started, Email, SMS, etc.]
\`\`\`

### 3. MUST KEEP SECTION
\`\`\`markdown
## ✅ Must Keep - v7-Specific Features

| File | Reason | Badge Text |
|------|--------|------------|
| filename.md | Feature not in v8 FFDA | "This feature is not available..." |
\`\`\`

### 4. QUICK WINS SECTION
\`\`\`markdown
## 🗑️ Quick Wins - Safe to Delete Now

**[Category]** (X files):
- ✅ filename.md → 95% in v8/path
- ✅ filename.md → 90% in v8/path
\`\`\`

### 5. MIGRATION SECTION
\`\`\`markdown
## ➡️ Content to Migrate First

| v7 File | v8 Destination | Content to Migrate | Effort |
|---------|----------------|-------------------|--------|
| filename.md | /v8/path.md | Sections X, Y, Z | 2 hours |
\`\`\`

### 6. EXECUTION PLAN
\`\`\`markdown
## 🎯 Execution Plan

### Week 1: Quick Deletions
- [ ] Delete [category] files (X)
- [ ] Delete [category] files (X)
**Total**: X files deleted

### Week 2: Badging
- [ ] Badge v7-specific files (X)

### Week 3: Review
- [ ] Review partial matches (X)
\`\`\`

---

## ANALYSIS RULES

### For Each File, Determine:

1. **Match Percentage**:
   - 95-100% = Fully covered in v8 → DELETE
   - 70-90% = Mostly covered, check gaps → DELETE or MOVE
   - 40-70% = Partial coverage → REVIEW
   - 0-40% = Not in v8 → KEEP or REVIEW

2. **v7-Specific Indicators** (→ KEEP):
   - Mentions "on-premise", "hybrid", "mid-sourcing"
   - Coupons, MRM, Surveys, Distributed Marketing
   - SpamAssassin, nlserver configuration
   - Client Console specific features
   - Database schema/structure docs

3. **DELETE Criteria**:
   - Basic features (email, SMS, push creation)
   - Standard workflow activities (query, split, enrichment)
   - Common reports
   - Channel basics fully documented in v8

4. **MOVE Criteria**:
   - Troubleshooting tips not in v8
   - Best practices missing in v8
   - Advanced patterns useful for v8
   - Good examples/use cases

5. **REVIEW Criteria**:
   - Partial v8 coverage (50-70%)
   - Unclear if feature exists in v8
   - Complex mixed content

---

## IMPORTANT

- **Organize by category** (Get Started, Email, SMS, Push, etc.)
- **Include Experience League URLs** for v8 matches
- **Bold v7-specific files** that must be kept
- **Estimate match percentage** for each file
- **Provide clear reasoning** for each decision
- **Include effort estimates** for migrations

---

Generate the complete Markdown report now.
```

&#x200B;---

## 🎯演示说明

### 第1步：显示提示1. 打开此文件(`DEMO-PROMPT-STANDALONE.md`)2. 滚动到“提示”部分3. 说： *“这是我们的自动分析提示”*

### 第2步：复制提示1. 选择从“# Campaign v7文档分析”到结尾的所有内容2. 复制到剪贴板3. 说： *“我刚刚复制了整个提示……”*

### 步骤3：粘贴并执行1. 打开光标2. 粘贴提示3. 说：*“……并将其粘贴到Cursor“*”4. 点击Enter

### 步骤4：显示结果1. 等待生成（~30-60秒）2. 滚动浏览生成的报表3. 突出显示关键部分：   - 📊摘要统计信息   - 📋文件逐文件表   - ✅必须保留节   - 🗑️个快速入选   - 🎯执行计划

### 步骤5：Wow时刻1. 显示Markdown预览2. 指出：   - *“111个文件已自动分析”*   - *“67个文件可安全删除（减少60%）”*   - *“已识别18个v7特定文件”*   - *“完成具有时间线的执行计划”*

&#x200B;---

## 💡演示提示

### 使其具有交互性&#x200B;**询问受众**： *“我们应该分析哪个文件夹？”*- 投放✅（111个文件 — 令人印象深刻）- 工作流✅（121个文件 — 更大）- web ✅ （26个文件 — 快速演示）- 报告✅ （32个文件 — 快速）

### 动态自定义&#x200B;**显示灵活性**：在提示中更改文件夹路径：

```
/help/workflow/using/  → Analyze workflows
/help/web/using/       → Analyze web apps
/help/platform/using/  → Analyze platform
```

### 突出显示主要功能1. **自动化**： *“无需手动操作”*2. **准确性**： *“使用v8文档进行比较”*3. **可操作**： *“已准备好执行带有复选框的计划”*4. **Smart**： *“自动识别v7特定功能”*

### 时间比较&#x200B;**Before**： *&quot;手动分析=每个文件夹2-3天&quot;*\**After**： *&quot;自动分析=每个文件夹30秒&quot;*

**ROI**： *&quot;21个文件夹× 2天= 42天→ 15分钟&quot;*

&#x200B;---

## 📊预期的输出预览

```markdown
# 📊 v7 Delivery Analysis

**Total Files**: 111

## 📈 Summary
| Metric | Count | Percentage |
|--------|-------|------------|
| ✅ KEEP | 18 | 16% |
| 🗑️ DELETE | 67 | 60% |
| ➡️ MOVE | 8 | 7% |
| 🔍 REVIEW | 18 | 17% |

## 📋 File Analysis

### 📧 Email (18 files)
| # | v7 File | v8 Match | % | Action |
|---|---------|----------|---|--------|
| 1 | about-email-channel.md | campaign-web/v8/email | 95% | 🗑️ DELETE |
| 2 | creating-an-email-delivery.md | campaign-web/v8/email/create | 95% | 🗑️ DELETE |

### 📱 SMS (7 files)
| # | v7 File | v8 Match | % | Action |
|---|---------|----------|---|--------|
| 1 | sms-channel.md | campaign-web/v8/msg/send-sms | 90% | 🗑️ DELETE |
| 2 | **sms-set-up-mid.md** | NONE | 0% | ✅ **KEEP** |

[... continues for all categories ...]

## ✅ Must Keep (18 files)
- **personalized-coupons.md** - Coupons not in v8 FFDA
- **sms-set-up-mid.md** - Mid-sourcing (on-prem)
- **spamassassin.md** - On-prem spam filtering

## 🗑️ Quick Wins (67 files)
Email basics, SMS, Push, Direct mail → All in v8

## 🎯 Execution Plan
Week 1: Delete 67 files (60%)
Week 2: Badge 18 files
Week 3: Review 18 files
```

&#x200B;---

## 🎬演示脚本

**正在打开**：
> “今天，我将向您展示我们如何使用AI对v7文档进行自动重组。 这过去需要几周时间，现在只需要几分钟的时间。”

**问题**：
> “我们有1,500多个v7文档文件。 许多在v8中重复。 我们需要确定保留、删除或迁移的内容。”

**解决方案**：
> “我们创建了一个智能提示，用于分析任何文件夹并生成可操作建议。”

**演示**：
> “我来给你看看。 我将分析包含111个文件的“投放”文件夹……”
> 
> [复制提示，粘贴，执行]
> 
> “……30秒内，我们得到一个完整的分析。”

**个结果**：
> “看看这个：
> - 要删除67个文件（减少60%）
> - 已识别18个特定于v7的文件
> - 8个要迁移的文件
> - 完成3周的执行计划
> 
> 全部自动化。 一切都是准确的。”

**关闭**：
> “同样的流程适用于所有21个文件夹。 过去需要6周的时间，现在需要15分钟。”

&#x200B;---

## 🚀准备演示！

**Just**：
1. 打开此文件
2. 复制提示
3. 粘贴到光标中
4. 显示魔法✨

**总演示时间**： 3-5分钟\
**Wow因子**： 🔥🔥🔥

