# Anti Pitch Toolkit 🚀
**AI-powered pitch deck, sales, and business planning workspace**

Ez a repo a te személyes AI pitch-gyártó eszközöd. Claude Code + GitHub = minden anyagod egy helyen, memóriával, sablonokkal, és automatikus skill-kiválasztással.

---

## Gyors Start (5 perc)

### 1. Telepítsd a Claude Code-ot

**Mac / Linux / WSL:**
```bash
curl -fsSL https://claude.ai/install.sh | bash
```

**Windows PowerShell:**
```powershell
irm https://claude.ai/install.ps1 | iex
```

Ellenőrzés: `claude --version`

### 2. Klónozd a repót
```bash
git clone https://github.com/[your-username]/anti-pitch-toolkit.git
cd anti-pitch-toolkit
```

### 3. Nyisd meg VS Code-ban (opcionális, de ajánlott)
```bash
code .
```
A Claude Code extension automatikusan aktiválódik (ha fel van telepítve).

### 4. Indítsd el Claude Code-ot a repóban
```bash
claude
```
Claude beolvassa a `CLAUDE.md`-t és a skills-t → tudja ki vagy, mit csinálsz, hogyan kell dolgoznod.

---

## Hogyan Használd

### Egyszerű használat — csak mondd el, mit akarsz:

```
Csinálj egy sales one-pagert logistics cégeknek.
Pain point: manual invoicing. Küldős formátum.
```

```
Készíts egy pitch decket egy fintech befektetőnek.
Összeg: €500K. Current ARR: €120K.
```

```
Adj egy HTML prezentációt amit linken tudok küldeni.
Téma: AI workflow automation. Sötét téma.
```

Claude automatikusan kiválasztja a megfelelő skill-t és elmenti az outputot az `/outputs/` mappába.

---

## Skill-ek (automatikusan triggerelnek)

| Skill | Mikor aktivál | Output |
|---|---|---|
| `pitch-deck` | prezentáció, slides, deck | Markdown + opcionálisan HTML |
| `sales-onepager` | kiküldős, one-pager, email attachment | Markdown |
| `investor-brief` | befektetői, funding, raise | Markdown |
| `html-presentation` | web link, böngészős, HTML verzió | .html fájl |
| `collaborator-deck` | partner, együttműködés, white-label | Markdown |
| `business-planning` | GTM, árazás, pénzügyi terv | Markdown |

Manuálisan is hívhatod: `/pitch-deck`, `/sales-onepager`, stb.

---

## Output Fájlok

Minden generált anyag ide kerül: `/outputs/`

Naming convention:
```
onepager-logistics-2026-03.md
pitchdeck-fintech-investor-2026-03.md
presentation-ai-automation-2026-03.html
```

A `.html` fájlokat csak megnyitod böngészőben — küldhatod mellékletként vagy feltöltheted bárhova.

---

## Projekt Memória Frissítése

Ha változik valami (új szolgáltatás, új ár, új USP), nyisd meg a `CLAUDE.md`-t és frissítsd. Minden következő session-ben Claude az új infóval dolgozik.

---

## Repo Frissítése

```bash
git add .
git commit -m "Updated CLAUDE.md with new pricing"
git push
```

---

## Tippek

**Adj kontextust az audienciáról:**
> "Ez egy hideglevél utáni follow-up anyag, €200-500M árbevételű logisztikai cégek ops vezetőinek."

**Kérj vázlatot először, aztán finomíts:**
> "Először adj egy vázlatot, aztán megmondom mi hiányzik."

**Kérj több verziót:**
> "Adj egy rövidebb és egy hosszabb verziót is."

**HTML-t mindig tesztelj böngészőben:**
> Az `/outputs/` mappában lévő `.html` fájlt egyszerűen húzd be a böngészőbe.

---

## Support
Ha valami nem működik vagy új skill-t szeretnél: jelezd Rekának.
