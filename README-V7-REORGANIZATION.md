---
source-git-commit: 65d223acd23f26bd9c6979d11815d23f02ae2382
workflow-type: tm+mt
source-wordcount: '316'
ht-degree: 0%

---
# 📚 v7文档重组工具包

**2提示pour analyzer et réorganizer la doc v7 → v8**

---

## 📁个文件夹

### 🔍提示（说明）

| Fichier | 说明 | 输出 |
|---------|-------------|--------|
| `PROMPT-1-OVERVIEW-ALL-FOLDERS.md` | Vue d&#39;ensemble de TOUS les folders v7 | `v7-reorganization-overview.md` |
| `PROMPT-2-DETAILED-FOLDER.md` | 分析联合国文件夹标题平均匹配百分比 | `[folder]-detailed-analysis.md` |

---

## 🚀利用率

### ⃣1️组合值(tous les folders)

```bash
# 1. Ouvrir le prompt
open PROMPT-1-OVERVIEW-ALL-FOLDERS.md

# 2. Copier tout le contenu du bloc "COPIER CE PROMPT"
# 3. Coller dans Cursor/ChatGPT
# 4. Obtenir : v7-reorganization-overview.md
```

**热内尔** ：
- 📊执行摘要（全局统计信息）
- 📁分析des 21个文件夹
- 🎯 Matrice de优先顺序
- ✅操作项
- ⚠️风险
- 📈梅特里克

**尾** ：~50-60页Markdown

---

### ⃣2️分析动态文件夹

```bash
# 1. Ouvrir le prompt
open PROMPT-2-DETAILED-FOLDER.md

# 2. Modifier la ligne :
📁 **Analyze**: /Users/.../help/delivery/using/

# 3. Remplacer par le folder souhaité :
# - /help/delivery/using/
# - /help/workflow/using/
# - /help/web/using/
# - etc.

# 4. Copier tout le contenu du bloc "COPIER CE PROMPT"
# 5. Coller dans Cursor/ChatGPT
# 6. Obtenir : [folder]-detailed-analysis.md
```

**热内尔** ：
- 📊统计信息文件夹
- 📋 Tableau détaillé organisé comme Experience League
- 🔗个连线可修剪项(v7 + Experience League)
- 📈 Jusqu&#39;à 3匹配v8 par fichier avec %
- 📄重述文件par文件
- 🎯重组计划
- ✅复选框用于进行跟踪

**尾** ：~30-40页Markdown

---

## 📊示例输出

### 提示1（概述）

```markdown
# 📊 v7 Documentation Reorganization Overview

**Total Files**: 1,500
**KEEP**: 400 (27%)
**DELETE**: 800 (53%)
**MOVE**: 200 (13%)
**REVIEW**: 100 (7%)

## 📁 Folder Analysis

### 🟢 100% KEEP - v7-Only Content
| Folder | Files | Reason |
|--------|-------|--------|
| /installation/ | 75 | On-premise setup |
| /mrm/ | 5 | Not in v8 FFDA |
...
```

### 提示2 （详细文件夹）

```markdown
# 📊 v7 Folder Analysis: Delivery

**Total Files**: 111

| # | v7 File | v8 Match 1 | % | v8 Match 2 | % | Notes | Action |
|---|---------|------------|---|------------|---|-------|--------|
| 1 | about-email-channel.md | campaign-web/v8/email | 95% | - | - | Fully in v8 | 🗑️ DELETE |
| 9 | sms-set-up-mid.md | NONE | 0% | - | - | Mid-sourcing (on-prem) | ✅ KEEP |
...
```

---

## 🎯工作流推荐

### 塞梅因1：伦桑布尔值
1. Exécuter **提示符1** → Obtenir `v7-reorganization-overview.md`
2. 标识符作为文件夹优先级
3. 合作伙伴平均利益相关者

### 瑟曼2-4 ：分析戴尔
1. 优先置入沙克文件夹：
   - Exécuter **提示2**
   - obtenir `[folder]-detailed-analysis.md`
   - 瓦利德莱迪西代
   - 评论者行为

### Semaine 5+ ：执行
1. Supprimer les fichiers identifiers(DELETE)
2. Badger les fichiers v7-only (KEEP)
3. Migrer le contentu manquant (MOVE)
4. 审阅者不确定(REVIEW)

---

## 💡个提示

### 倾倒提示
- ✅复印机/综合提示字典
- ✅ Ne pas修饰符格式
- ✅ Adapter seulement le chemin du文件夹（提示2）

### 倒出少量输出
- 📝 Output en Markdown (pas HTML)
- 🔗联属可自定义项自动完成
- ✅复选框用于进行跟踪
- 📊统计和百分比
- 🎨表情符号图标

### Pour l&#39;analyze
- 🎯 Commencer par组文件夹（投放、工作流）
- ⚡优先赛快速获胜（95-100%匹配）
- 🔍审核者手动处理不明确（&lt;70%匹配）
- ✅验证器avec SME前卫隐藏大量

---

## ⚠️重要

### 前锋超本
1. ✅ Vérifier l&#39;équivalent v8
2. ✅ Vérifier qu&#39;il n&#39;y a pas de contenu v7特定
3. ✅ Mettre à jour `redirects.csv`
4. ✅ Valider avec un expert (pour les premier)

### Pour les fichiers v7-only
1. ✅ Ajouter un badge au début du fichier
2. ✅ Expliquer pourquoi测试仅限v7
3. ✅留存时间限制v8

---

## 🆘支持

**问题**？
- Vérifier les chemins des repos→提示新字形符号
- →Demander un résumé输出长
- 贝索因·德→德·平·莱奎普医生

---

**Derniere mise à jour** ： 2026-01-13

