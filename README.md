# glanzgarage-rentus — RENT US Glanzgarage (Live-Site, Haupt-Domain)

> ⚠️ **HIER NICHT BAUEN.** Dieses Repo ist nur der Deploy-Spiegel. Änderungen gehören nach
> `~/XcodeProjects/Glanzgarage/site/` und werden von dort hierher gespiegelt — sonst sind sie
> beim nächsten Spiegeln weg. Pflichtlektüre vorher: `~/XcodeProjects/Glanzgarage/CLAUDE.md`.
> (Am 04.08.2026 ist genau das passiert und musste nachgezogen werden.)

Statische Website für **RENT US Glanzgarage** (Kunde Mike Knörzer), gehostet über
GitHub Pages unter der Domain **glanzgarage-rentus.de** (angelegt 20.08.2026).

- **Quelle/Wahrheit:** `~/XcodeProjects/Glanzgarage` (`site/`). Dieses Repo ist ein
  Deploy-Spiegel für die eigene Domain — bei Änderungen dort bauen und hierher spiegeln.
- Reine Statik (HTML/CSS/JS), kein Build. `CNAME` = Custom Domain.
- ⚠️ `3d-check/` **muss** hier liegen — der Buchungs-Wizard lädt absolut `/3d-check/`.

## Es gibt DREI Deploy-Spiegel — jeder Patch muss in alle drei

| Repo | Domain | Wohin gespiegelt wird |
|---|---|---|
| `glanzgarage-rentus` | **glanzgarage-rentus.de** (Haupt, Flyer) | `site/` → Wurzel · `tools/3d-check/` → `3d-check/` |
| `info-rentus` | info-rentus.de | `site/` → Wurzel · `tools/3d-check/` → `3d-check/` |
| `deadrabbit-landing` | pelczer.de | `site/` → `rentus/` · `tools/3d-check/` → `3d-check/` |

**Warum drei Repos:** GitHub Pages erlaubt pro Repo nur **eine** Custom-Domain
(die `CNAME`-Datei). Jede eigene Domain braucht daher ihr eigenes Repo.

## Domain-Eigenheit dieses Spiegels
`canonical`, `og:url`, JSON-LD `@id`/`url`, `sitemap.xml` und `robots.txt` zeigen hier auf
**glanzgarage-rentus.de** (Entscheidung 20.08.2026: das ist die Haupt-Adresse für Google).
Beim Spiegeln aus `Glanzgarage/site/` muss diese Ersetzung **jedes Mal** neu gemacht werden:

```sh
find . -type f \( -name '*.html' -o -name '*.xml' -o -name '*.txt' -o -name '*.js' \) \
  ! -name '*.backup_*' -exec sed -i '' 's/info-rentus\.de/glanzgarage-rentus.de/g' {} +
```
