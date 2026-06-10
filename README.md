# Think Skills — Claude Code 思维技能包

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

A collection of metacognition and debugging skills for [Claude Code](https://claude.ai/code). These skills help you think better, debug faster, and avoid rabbit holes — all within your Claude Code sessions.

一套面向 Claude Code 的元认知与调试技能集合。帮助你更清晰地思考、更高效地调试、避免陷入死胡同。

---

## Skills / 技能

| Skill | Invoke | Purpose |
|-------|--------|---------|
| **assess-me** | `/assess-me` | Self-cognition audit — catch blind spots, verify assumptions, externalize thinking |
| **reframe** | `/reframe` | Strip noise, get a fresh perspective on stuck problems |
| **debug-root-cause** | `/debug-root-cause` | Systematic RCA methodology — 20 structured approaches for any bug |

### assess-me

A structured self-assessment protocol. When debugging goes in circles or results confuse you, run `/assess-me` to check your goal state, progress, gaps, assumptions, blockers, and recovery path.

### reframe

When context is cluttered with tool call history and intermediate results, run `/reframe` to compose a clean problem summary and get a fresh answer from the model.

### debug-root-cause

Stop random grepping. Run `/debug-root-cause` to select a systematic investigation method (Divide & Conquer, Comparison, Hypothesis Testing, Log Injection, and 16 more) and follow it step by step.

---

## Installation / 安装

Clone into your Claude Code projects directory:

```bash
git clone https://github.com/savvych/think-skills.git
```

Skills are loaded by Claude Code from `SKILL.md` files — no package manager, no build step, no dependencies.

---

## Creating a New Skill / 创建新技能

```
think-skills/
└── <skill-name>/
    ├── SKILL.md             # Entry point — frontmatter + procedure
    └── references/          # (optional) Reference materials
```

Each `SKILL.md` needs:
- **Frontmatter**: `name` (invocation name) and `description` (trigger conditions)
- **Body**: When to Use, Steps (phased), Verification, Pitfalls

---

## License / 许可证

MIT

---

## 中文说明

Think Skills 是为 Claude Code 设计的元认知与系统化调试技能包。当前包含三个技能：

- **assess-me**：自我认知审计。当你反复尝试却毫无进展、结果令人困惑、或同时存在多个假设时，运行此技能来系统性地审视你的目标、进展、盲点、假设、障碍和恢复路径。
- **reframe**：问题重构。当上下文中充斥着工具调用记录和中间结果时，运行此技能将关键信息重组为一份简洁的问题摘要，让模型给出全新的分析视角。
- **debug-root-cause**：根因分析。提供 20 种系统化的调试方法论（分解法、对比法、假设法、日志注入法等），取代盲目的随机尝试。

**使用方式**：在 Claude Code 中运行 `/<skill-name>` 即可调用。

---

## Description en français

Think Skills est une collection de compétences de métacognition et de débogage pour Claude Code. Elle contient trois outils :

- **assess-me** : Auto-évaluation cognitive. Quand vous tournez en rond, que les résultats sont confus, ou que plusieurs hypothèses s'affrontent, cet outil structure votre réflexion autour de 6 dimensions clés.
- **reframe** : Recadrage de problème. Lorsque l'historique des appels d'outils encombre votre contexte, cet outil extrait l'essentiel et le presente comme une question neuve au modèle.
- **debug-root-cause** : Analyse de cause racine. 20 méthodes systématiques (diviser pour régner, comparaison, test d'hypothèse, injection de logs, etc.) pour remplacer les tâtonnements aléatoires.

**Utilisation** : Lancez `/<nom-du-skill>` dans Claude Code.

---

## Descrição em português

Think Skills é uma coleção de habilidades de metacognição e depuração para Claude Code. Inclui três habilidades:

- **assess-me** : Auditoria de autocognição. Quando você está andando em círculos, resultados são confusos, ou múltiplas hipóteses existem, esta habilidade examina sistematicamente seu objetivo, progresso, lacunas, suposições, bloqueadores e caminho de recuperação.
- **reframe** : Reformulação de problema. Quando o contexto está poluído com histórico de chamadas de ferramentas, esta habilidade extrai o essencial e apresenta como uma pergunta nova ao modelo.
- **debug-root-cause** : Análise de causa raiz. 20 métodos sistemáticos (dividir e conquistar, comparação, teste de hipótese, injeção de log, etc.) para substituir tentativas aleatórias.

**Uso** : Execute `/<nome-da-habilidade>` no Claude Code.

---

## Descripción en español

Think Skills es una colección de habilidades de metacognición y depuración para Claude Code. Incluye tres habilidades:

- **assess-me** : Auditoría de auto-cognición. Cuando estás dando vueltas, los resultados son confusos, o existen múltiples hipótesis, esta habilidad examina sistemáticamente tu objetivo, progreso, vacíos, suposiciones, bloqueadores y ruta de recuperación.
- **reframe** : Reformulación de problemas. Cuando el contexto está saturado con el historial de llamadas de herramientas, esta habilidad extrae lo esencial y lo presenta como una pregunta nueva al modelo.
- **debug-root-cause** : Análisis de causa raíz. 20 métodos sistemáticos (divide y vencerás, comparación, prueba de hipótesis, inyección de registros, etc.) para reemplazar intentos aleatorios.

**Uso** : Ejecuta `/<nombre-de-la-habilidad>` en Claude Code.
