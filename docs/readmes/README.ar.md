<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>حوّلوا دروس YouTube إلى مهارات وسير عمل واضحة ومتحقَّق منها لعدة وكلاء ذكاء اصطناعي.</strong></p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/badge/License-MIT-2ea44f?style=flat" alt="MIT License" /></a>
  <a href="https://github.com/Zero-Piege/youtube-vers-agent/stargazers"><img src="https://img.shields.io/github/stars/Zero-Piege/youtube-vers-agent?style=flat&logo=github" alt="GitHub stars" /></a>
  <a href="../../docs/platforms/README.md"><img src="https://img.shields.io/badge/Agent%20Skills-multi--platform-6f42c1?style=flat&logo=github" alt="Multi-platform support" /></a>
</p>

<p align="center">
  <a href="../../README.md">🇬🇧 English</a> · <a href="README.zh.md">🇨🇳 中文</a> · <a href="README.zh-TW.md">🇹🇼 繁體中文</a> · <a href="README.ja.md">🇯🇵 日本語</a> · <a href="README.pt.md">🇵🇹 Português</a> · <a href="README.pt-BR.md">🇧🇷 Português (Brasil)</a> · <a href="README.ko.md">🇰🇷 한국어</a><br />
  <a href="README.es.md">🇪🇸 Español</a> · <a href="README.de.md">🇩🇪 Deutsch</a> · <a href="README.fr.md">🇫🇷 Français</a> · <a href="README.he.md">🇮🇱 עברית</a> · <a href="README.ar.md">🇸🇦 العربية</a> · <a href="README.ru.md">🇷🇺 Русский</a> · <a href="README.pl.md">🇵🇱 Polski</a><br />
  <a href="README.cs.md">🇨🇿 Čeština</a> · <a href="README.nl.md">🇳🇱 Nederlands</a> · <a href="README.tr.md">🇹🇷 Türkçe</a> · <a href="README.uk.md">🇺🇦 Українська</a> · <a href="README.vi.md">🇻🇳 Tiếng Việt</a> · <a href="README.tl.md">🇵🇭 Tagalog</a> · <a href="README.id.md">🇮🇩 Bahasa Indonesia</a><br />
  <a href="README.th.md">🇹🇭 ไทย</a> · <a href="README.hi.md">🇮🇳 हिन्दी</a> · <a href="README.bn.md">🇧🇩 বাংলা</a> · <a href="README.ur.md">🇵🇰 اردو</a> · <a href="README.ro.md">🇷🇴 Română</a> · <a href="README.sv.md">🇸🇪 Svenska</a> · <a href="README.it.md">🇮🇹 Italiano</a><br />
  <a href="README.el.md">🇬🇷 Ελληνικά</a> · <a href="README.hu.md">🇭🇺 Magyar</a> · <a href="README.fi.md">🇫🇮 Suomi</a> · <a href="README.da.md">🇩🇰 Dansk</a> · <a href="README.no.md">🇳🇴 Norsk</a>
</p>

---

يدعم هذا المستودع عدة منصات للوكلاء. تشرح هذه الصفحة سير العمل الخاص بـ Claude Code؛ أما التنسيقات المحمولة وإعدادات Codex وGemini CLI وGitHub Copilot وChatGPT وواجهة OpenAI API فتجدها في [دليل المنصات](../../docs/platforms/README.md).

قدّموا رابط YouTube والهدف المطلوب. تحلّل المهارة الفيديو بشكل مستقل باستخدام Claude وGemini، وتجمع النتائج في notes/SPEC.md، ثم تنشئ مهارة Claude Code قابلة لإعادة الاستخدام وتتحقق منها. استخدام Gemini اختياري؛ وعند عدم توفره تُوسم النتيجة بأنها مستندة إلى مصدر واحد.

## آلية العمل

1. **تحديد المطلوب** — تحديد ما ينبغي استخراجه من الفيديو وما ينبغي بناؤه. يمكن اختيار مقطع محدد إذا تجاوز الفيديو 20 دقيقة.
2. **تحليل Claude** — استخدام المحرك المحلي في watch:watch وحفظ مواصفات من ستة أجزاء في notes/lecture-claude.md.
3. **تحليل Gemini المستقل** — تكرار التحليل مرتين دون إطلاع Gemini على ملاحظات Claude، ثم حفظ الإجابتين في notes/lecture-gemini.md. إذا لم يتوفر Gemini، يُستكمل العمل باستخدام Claude فقط مع الإشارة إلى المصدر الواحد.
4. **مقارنة النتائج** — وسم كل بند في notes/SPEC.md بأحد التصنيفات CONFIRMED أو UNE SOURCE أو DÉSACCORD. تُراجع لقطات الفيديو لحل الخلافات مع الحفاظ على الأوامر وأسماء الحزم والإعدادات ورسائل الخطأ كما ظهرت.
5. **البناء والتحقق** — تمرير المواصفات إلى skill-creator، وإنشاء المهارة وتشغيلها على حالة استخدام حقيقية.

## المتطلبات

- Claude Code
- مهارة watch:watch لتحليل فيديوهات YouTube
- مهارة skill-creator لإنشاء النتيجة
- إمكانية الوصول إلى Gemini (اختيارية؛ يمكن متابعة العمل باستخدام Claude وحده)

## التثبيت

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

بعد ذلك، شغّلوا /reload-plugins في Claude Code لإعادة تحميل الإضافات.

## الاستخدام

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "المشروع بأكمله" "مهارة Claude Code"
```

## الملفات الناتجة

- `notes/lecture-claude.md` — تحليل Claude للفيديو في ستة أجزاء
- `notes/lecture-gemini.md` — تحليلا Gemini المستقلان عند توفره
- `notes/SPEC.md` — المواصفات المتقاطعة والأسئلة المفتوحة
- المهارة المنشأة في مجلد الإخراج المحدد

## بنية المستودع

```text
README.md                                      Full English guide and GitHub landing page
docs/readmes/README.<locale>.md                Translated guides
.claude/skills/youtube-vers-agent/SKILL.md     Installable Claude Code skill
```

## الترخيص

هذا المشروع متاح بموجب ترخيص MIT. راجعوا LICENSE.
