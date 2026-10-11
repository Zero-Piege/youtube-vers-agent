<h1 align="center">
  <img src="https://cdn.simpleicons.org/youtube/FF0000" width="72" alt="YouTube" /> youtube-vers-agent
</h1>

<p align="center"><strong>YouTube eğitimlerini açık ve doğrulanmış Claude Code becerilerine dönüştürün.</strong></p>

<p align="center">
  <a href="../../LICENSE"><img src="https://img.shields.io/badge/License-MIT-2ea44f?style=flat" alt="MIT License" /></a>
  <a href="https://github.com/Zero-Piege/youtube-vers-agent/stargazers"><img src="https://img.shields.io/github/stars/Zero-Piege/youtube-vers-agent?style=flat&logo=github" alt="GitHub stars" /></a>
  <a href="../../.claude/skills/youtube-vers-agent/SKILL.md"><img src="https://img.shields.io/badge/Claude%20Code-skill-cb785c?style=flat&logo=anthropic&logoColor=white" alt="Claude Code skill" /></a>
</p>

<p align="center">
  <a href="README.en.md">🇬🇧 English</a> · <a href="README.zh.md">🇨🇳 中文</a> · <a href="README.zh-TW.md">🇹🇼 繁體中文</a> · <a href="README.ja.md">🇯🇵 日本語</a> · <a href="README.pt.md">🇵🇹 Português</a> · <a href="README.pt-BR.md">🇧🇷 Português (Brasil)</a> · <a href="README.ko.md">🇰🇷 한국어</a><br />
  <a href="README.es.md">🇪🇸 Español</a> · <a href="README.de.md">🇩🇪 Deutsch</a> · <a href="README.fr.md">🇫🇷 Français</a> · <a href="README.he.md">🇮🇱 עברית</a> · <a href="README.ar.md">🇸🇦 العربية</a> · <a href="README.ru.md">🇷🇺 Русский</a> · <a href="README.pl.md">🇵🇱 Polski</a><br />
  <a href="README.cs.md">🇨🇿 Čeština</a> · <a href="README.nl.md">🇳🇱 Nederlands</a> · <a href="README.tr.md">🇹🇷 Türkçe</a> · <a href="README.uk.md">🇺🇦 Українська</a> · <a href="README.vi.md">🇻🇳 Tiếng Việt</a> · <a href="README.tl.md">🇵🇭 Tagalog</a> · <a href="README.id.md">🇮🇩 Bahasa Indonesia</a><br />
  <a href="README.th.md">🇹🇭 ไทย</a> · <a href="README.hi.md">🇮🇳 हिन्दी</a> · <a href="README.bn.md">🇧🇩 বাংলা</a> · <a href="README.ur.md">🇵🇰 اردو</a> · <a href="README.ro.md">🇷🇴 Română</a> · <a href="README.sv.md">🇸🇪 Svenska</a> · <a href="README.it.md">🇮🇹 Italiano</a><br />
  <a href="README.el.md">🇬🇷 Ελληνικά</a> · <a href="README.hu.md">🇭🇺 Magyar</a> · <a href="README.fi.md">🇫🇮 Suomi</a> · <a href="README.da.md">🇩🇰 Dansk</a> · <a href="README.no.md">🇳🇴 Norsk</a>
</p>

---

Bir YouTube bağlantısı ve hedef verin. Beceri videoyu Claude ve Gemini ile birbirinden bağımsız analiz eder, bulguları notes/SPEC.md dosyasında birleştirir, ardından yeniden kullanılabilir bir Claude Code becerisi oluşturup doğrular. Gemini isteğe bağlıdır; kullanılamazsa sonuç tek kaynağa dayalı olarak işaretlenir.

## Nasıl çalışır

1. **İsteği netleştirin** — videodan ne çıkarılacağını ve ne oluşturulacağını belirleyin. 20 dakikadan uzun videolarda belirli bir bölümü seçebilirsiniz.
2. **Claude ile analiz** — watch:watch aracının yerel motorunu kullanın ve altı bölümlü yapım şartnamesini notes/lecture-claude.md dosyasına kaydedin.
3. **Gemini ile bağımsız analiz** — Claude'un notlarını göstermeden aynı analizi iki kez yapın ve iki yanıtı notes/lecture-gemini.md dosyasına kaydedin. Gemini kullanılamıyorsa yalnızca Claude ile devam edin ve tek kaynak olarak işaretleyin.
4. **Bulguları karşılaştırın** — notes/SPEC.md içindeki her öğeyi CONFIRMED, UNE SOURCE veya DÉSACCORD olarak etiketleyin. Görüntü karelerini yeniden inceleyerek uyuşmazlıkları çözün; komutları, paket adlarını, ayarları ve hata mesajlarını aynen koruyun.
5. **Oluşturun ve doğrulayın** — şartnameyi skill-creator'a verin, beceriyi oluşturun ve gerçek bir kullanım senaryosunda çalıştırın.

## Gereksinimler

- Claude Code
- YouTube video analizi için watch:watch becerisi
- Sonucu oluşturmak için skill-creator becerisi
- Gemini erişimi (isteğe bağlı; yalnızca Claude ile devam edilebilir)

## Kurulum

```bash
git clone https://github.com/Zero-Piege/youtube-vers-agent.git
cd youtube-vers-agent
cp -r .claude/skills/youtube-vers-agent ~/.claude/skills/
```

Ardından eklentileri yeniden yüklemek için Claude Code içinde /reload-plugins komutunu çalıştırın.

## Kullanım

```text
/youtube-vers-agent https://youtu.be/VIDEO_ID "projenin tamamı" "bir Claude Code becerisi"
```

## Oluşturulan dosyalar

- `notes/lecture-claude.md` — Claude'un altı bölümlü video analizi
- `notes/lecture-gemini.md` — Varsa Gemini'nin iki bağımsız analizi
- `notes/SPEC.md` — Karşılaştırılmış şartname ve açık sorular
- Seçilen çıktı dizininde oluşturulan beceri

## Depo yapısı

```text
README.md
docs/
└── readmes/
    ├── README.en.md
    └── README.<locale>.md
.claude/
└── skills/
    └── youtube-vers-agent/
        └── SKILL.md
```

## Lisans

Bu proje MIT Lisansı kapsamında yayımlanır. LICENSE dosyasına bakın.
