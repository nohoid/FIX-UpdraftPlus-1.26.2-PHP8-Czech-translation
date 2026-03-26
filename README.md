# 🚨 Fix: UpdraftPlus Czech Translation (PHP 8+)

Oprava kritických chyb v české lokalizaci, které na PHP 8.0+ způsobují pád pluginu (**Fatal Error: ArgumentCountError / ValueError**).

### 🔍 Problém
Chybné formátování `sprintf()` řetězců v souborech `.po`, `.mo` a `.l10n.php`. PHP 8 vyžaduje striktní escapování procent (`%%`) a kompletní zástupné symboly (`%1$s`).

### ✅ Provedené změny
| Lokace (Soubor) | Chybný text | Opravený (bezpečný) text |
| :--- | :--- | :--- |
| `dropbox.php:622` | `%1$službu Premium%2$` | `%1$službu Premium%2$s` |
| `lock-admin.php:23` | `%1$zabezpečit` | `%1$szabezpečit` |
| `notices.php:219` | `20 % s kódem %s` | `20 %% s kódem %s` |
| `dropbox.php:1022` | `%2$s % využito` | `%2$s %% využito` |
| `updraftvault.php:522` | `99.9999%` | `99.9999%%` |

### 📦 Obsah
- `updraftplus-cs_CZ.po` – Zdroj překladu.
- `updraftplus-cs_CZ.mo` – Kompilovaný soubor.
- `updraftplus-cs_CZ.l10n.php` – PHP formát pro WP 6.5+.

### ⚙️ Instalace
Nahraďte soubory v adresáři:
`wp-content/languages/plugins/`

*Poznámka: Neukládejte přímo do složky pluginu, aby nedošlo k přepsání při aktualizaci.*

---
**Changelog:** Fix fatal errors in CZ translation (improper % escaping and placeholder syntax) for PHP 8+ compatibility.
