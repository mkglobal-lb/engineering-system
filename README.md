# Engineering Playbook
## Professional Software Engineering Reference — مرجع هندسي مهني

**Purpose | الهدف**

This repository is a **central personal/professional reference** for how to work as a professional software engineer and how to work with Code Agents across any project.

هذا الـ repository هو **مرجع مركزي شخصي/مهني** لطريقة العمل كمهندس برمجيات محترف، وكيفية التعامل مع Code Agents في أي مشروع.

It is **not** installed into projects. Projects do not depend on it. You open this playbook when you need guidance, copy the relevant prompt/workflow, and work inside the actual project normally.

**لا يتم إدخاله داخل المشاريع.** المشاريع لا تعتمد عليه. أنت تفتح هذا المرجع عند الحاجة، تأخذ الـ workflow أو prompt المناسب، ثم تعمل داخل المشروع نفسه بشكل طبيعي.

---

## Start Here | ابدأ من هنا

Open:

**[`START_HERE.md`](START_HERE.md)**

Do not read the whole repository before using it. Use the index to go directly to the workflow you need.

لا تقرأ كل الملفات من البداية. افتح `START_HERE.md` واختر نوع العمل المطلوب فقط.

---

## Core Operating Loop | دورة العمل الأساسية

`CAPTURE → CLASSIFY → INVESTIGATE → DECIDE → IMPLEMENT → VERIFY → REVIEW → CLOSE → LEARN`

- **Capture | التقط:** What happened? What is expected?
- **Classify | صنّف:** Bug, feature, refactor, migration, incident, etc.
- **Investigate | حقّق:** Understand actual code/data before changing it.
- **Decide | قرّر:** Choose the smallest correct approach and understand risks.
- **Implement | نفّذ:** Fix the root cause; preserve unrelated behavior.
- **Verify | تحقّق:** Run real checks and tests.
- **Review | راجع:** Inspect correctness, business rules, architecture, security, and regressions.
- **Close | أغلق:** Finish only with evidence.
- **Learn | تعلّم:** Capture reusable knowledge in the playbook.

---

## Repository Map | خريطة الملفات

- `01-WORKFLOWS/` — What to do step-by-step.
- `02-CODE-AGENT/` — How to speak to Code Agents and reusable prompts.
- `03-VERIFICATION/` — Testing, review, and Definition of Done.
- `04-ENGINEERING/` — Long-lived engineering principles and design guidance.
- `05-LEXICON/` — Engineering terms and how to use them.
- `06-DECISIONS/` — How to make and record engineering decisions.
- `07-LEARNING/` — Inbox for new knowledge before promoting it into the playbook.
- `CHANGELOG.md` / `VERSION` — Track meaningful changes to the playbook itself.

---

## Language Rule | قاعدة اللغة

Arabic explains the intent and workflow clearly. English prompt blocks are written to be copied directly to Code Agents.

العربي للشرح والفهم. الـ English داخل الـ prompt blocks جاهز للنسخ مباشرة للـ Code Agent.

---

## Non-Goals | ما ليس هدف هذا النظام

This playbook does **not**:
- impose one framework, database, architecture, or testing library;
- replace project-specific requirements;
- replace source code, tests, schemas, or production evidence;
- require approval before every small change;
- force every task through a heavyweight process.

هذا النظام لا يفرض technology معينة، ولا يستبدل business rules الخاصة بالمشروع، ولا يحول كل تعديل صغير إلى عملية بيروقراطية.

---

## Golden Rule | القاعدة الذهبية

> **Do not accept a completion claim without evidence.**
>
> لا تقبل كلمة "تم" بدون دليل فعلي: code diff, test result, trace, build result, migration verification, or equivalent evidence.
