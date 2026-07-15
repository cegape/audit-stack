# Contribuer à stack-audit

## Règle de confidentialité (impérative)
Ce dépôt ne contient **que la méthode générique** (repères, dimensions, gabarit). Il ne doit **jamais** contenir de données internes : noms de produits, URLs de dépôts privés, secrets, extraits `fichier:ligne` de code réel, ni résultats d'audit. Les **fiches produites** sont des livrables (hors dépôt).

Quand la méthode repère un secret committé, elle en signale seulement l'existence et le fichier — jamais la valeur.

## Portée
- `skills/stack-audit/` : skill + `references/` (dimensions, hints par techno) + `templates/`.
- `commands/audit-stack.md` : slash-command d'audit d'un projet.

## Style
- Tout en **français**. Markdown soigné.
- Scripts éventuels : **Python 3 stdlib uniquement** (conventions `anssi-pg078-audit-kit` / `rgaa-audit-plugin`).

## Faire évoluer la méthode
Ajouter un repère de localisation ou une techno : compléter `references/hints-par-stack.md` et, si besoin, `references/dimensions.md`. Garder les exemples génériques.
