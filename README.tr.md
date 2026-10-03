# receipts 🧾

**Kodlama agent'ın "Bitti ✅" diyor. Kodu hiç çalıştırmadı.**

`receipts`, Claude Code, Codex, Cursor ve benzeri agent'ların bir şey iddia etmeden önce **kanıt göstermesini** sağlayan bir skill paketi.

## Öncesi / sonrası

**receipts olmadan**

> Tarih ayrıştırıcıyı ISO hafta formatını destekleyecek şekilde güncelledim. Artık çalışması lazım. Bitti ✅

**receipts ile**

> Bitti. Makbuz:
> ```
> $ pytest tests/test_dates.py
> 7 passed in 0.38s
> ```

ya da kontrol edemediğinde:

> `parse_date` artık ISO haftalarını kabul ediyor. **Doğrulanmadı**: burada test ortamı kurulu değil.
> Kontrol için: `python -c "from app.dates import parse_date; print(parse_date('2026-W40'))"`

## Skill'ler

| Skill | Agent'ını şundan alıkoyar |
|---|---|
| [`prove-it`](skills/prove-it/SKILL.md) | Hiçbir şey çalıştırmadan "bitti", "düzeldi", "testler geçti" demek |
| [`no-guessing`](skills/no-guessing/SKILL.md) | Fonksiyon adlarını, CLI parametrelerini, ayar anahtarlarını ezberden uydurmak |
| [`repro-first`](skills/repro-first/SKILL.md) | Hiç bozulduğunu görmediği hataları "düzeltmek" |

## Kurulum

**Claude Code**

```
/plugin marketplace add effectustasi/agent-receipts
/plugin install receipts@receipts
```

**Diğer agent'lar** (Codex, Cursor, Copilot, Gemini CLI, OpenCode…)

Skill klasörlerini agent'ının skill dizinine kopyala ya da her `SKILL.md` dosyasının içeriğini `AGENTS.md` veya kurallar dosyana yapıştır.
Agent'a özel kurulum rehberleri katkıya açık: [`agent-support`](https://github.com/effectustasi/agent-receipts/labels/agent-support) etiketli issue'lara bak.

## Katkı

Yeni skill'ler, çeviriler, diğer agent'lar için kurulum rehberleri ve benchmark görevleri memnuniyetle karşılanır. [CONTRIBUTING.md](CONTRIBUTING.md) ve [`good first issue`](https://github.com/effectustasi/agent-receipts/labels/good%20first%20issue) etiketiyle başla.

## Lisans

MIT
