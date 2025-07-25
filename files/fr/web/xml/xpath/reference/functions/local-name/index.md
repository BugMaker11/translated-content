---
title: local-name
slug: Web/XML/XPath/Reference/Functions/local-name
original_slug: Web/XPath/Functions/local-name
---

{{XsltSidebar}}{{ XsltRef() }}

La fonction `local-name` retourne une chaîne représentant le nom local du premier nœud d'un ensemble de nœuds donné.

### Syntaxe

```
local-name( [ensemble-de-nœuds] )
```

### Arguments

- `ensemble-de-nœuds` (optionnel)
  - : Le nom local du premier nœud de cet ensemble de nœuds sera retourné. Si cet argument est omis, le nœud de contexte courant sera utilisé.

### Retour

Une chaîne.

### Notes

- Le nom local est la partie locale d'un [nom étendu](https://www.w3.org/TR/xpath#dt-expanded-name).

### Définition

[XPath 1.0, section 4.1](https://www.w3.org/TR/xpath#function-local-name).

### Support Gecko

Supportée.
