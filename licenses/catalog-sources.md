# 数据来源与许可清单

> **本文件是 Penmanship（中小学书法练习）第三方数据来源的事实清单**，
> 同时是应用内「数据来源与许可」页面与页脚署名的**唯一数据来源**（R2-C10 / T2-47）。
>
> - 改这张表 = 改应用内显示。改完请跑：`npx vitest run src/services/sources.test.ts`（强校验表结构与必填字段）。
> - 许可证全文见同目录：`ARPHICPL.TXT`（文鼎公众授权书）、`cnchar-MIT.txt`。
> - 仓内同名软链：`licenses/catalog-sources.md → ../web/public/licenses/catalog-sources.md`（两处同一文件，不复制）。

**关于教材内容**（R2-C10 的边界）：本应用**只内置公开字表与元数据，不内置任何教材课文原文**。
教研性文字（如对临提示、笔顺规则卡片）为本应用自撰。

<!-- sources-table:start -->
| 名称 | 版本 / 快照 | 许可 | 获取日期 | 用途 | 核对记录 |
|---|---|---|---|---|---|
| [zispace/hanzi-chars-ext](https://github.com/zispace/hanzi-chars-ext) | 2016–2019 审定版写字表快照（上游未打版本 tag、未锁 commit，本地副本保留文件 sha256） | **上游未声明开源许可证**（README 与仓库均无 LICENSE 文件）——按「仅自用与内部教研」使用，不做再分发、不商用 | 2026-10-25 | 教材写字表：统编版 12 册 2500 字，实际收录 2490 字（覆盖率 99.60%） | 自动核对逐行通过（[docs/二期/教材字表来源与核对记录.md](https://github.com/zispace/hanzi-chars-ext)，人工抽检 100 字待完成） |
| [chanind/hanzi-writer-data](https://github.com/chanind/hanzi-writer-data) | master 分支快照（无版本锚点），经 `tools/import-glyphs` 本地化处理入 `glyphs.db` | **Arphic Public License**（字体派生；需随附 `ARPHICPL.TXT`，本项目已内置并可商用） | 2026-10-22 | 字形轮廓 `strokes` 与笔顺中线 `medians`：3500 字的描红、动画与评分唯一来源 | 需求选型见 `docs/需求说明.md` 数据源章节；字形自洽由 `scripts/verify-glyph-shards.mjs` 校验 |
| [theajack/cnchar](https://github.com/theajack/cnchar) + `cnchar-radical` | 3.2.6 | **MIT** | 2026-10-27 | 拼音、部首、多音字、汉字结构：**构建期**静态提取为 `tools/import-glyphs/data/meta/radical.json`，运行时不依赖 | 强校验脚本 `scripts/verify-meta.mjs`（10 项，全绿） |
| 界面字体 PingFang SC / Microsoft YaHei | 随操作系统提供 | **操作系统自带**，不作为本项目资产分发，故无需额外署名（列此仅为披露完整） | — | UI 文本渲染（字形/练字区域不使用该字体） | — |
<!-- sources-table:end -->

> 表格约定：单元格内不使用竖线；修改时保持 6 列结构（名称 / 版本 / 许可 / 获取日期 / 用途 / 核对记录）。

---

## 已知不足（如实披露，不粉饰）

1. **教材字表上游未提供许可证**（该项最重要）：`zispace/hanzi-chars-ext` 仓库未见 LICENSE 文件。
   因此本项目的对外分发形态需保持为**自用 / 教研用途**；若要商用，须替换为有明确授权的字表或取得作者书面授权。
2. **两处上游快照均无版本锚点**：字形数据取 jsdelivr `@master`（按下游瞬时状态），教材字表仅保留文件 sha256
   （`fc4355bd21010c74241c5c01c51be9a86520ef463ea4a4d441f82fe424383ad2`），无法据此还原确切 commit。
   后果：字形/字表重导出不保证与本次逐字节一致。改善需在上游取 tag/commit 并写入产物（属治理改进，不在本期范围）。
3. **教材字表人工抽检未完成**：`docs/二期/教材字表来源与核对记录.md` 第四节 100 字抽检表仍空，
   抽检完成前教材册次保持 `lessonStructure: 'unverified'` 标注。
