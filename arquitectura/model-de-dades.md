# Model de Dades

## Cadena principal

```
Allergens (14 UE, fixos)
  ↑
Ingredients → ingredient_allergens
  ↑
Dishes → dish_ingredients (amb quantity i unit)
  ↑
Menus → menu_dishes
```

Tot compartit entre tots els restaurants de Cal Blay.

## Taules

### allergens
- Taula fixa, 14 registres (Reglament UE 1169/2011)
- Gluten, crustacis, ous, peix, cacauets, soja, llet, fruits de closca, api, mostassa, sèsam, sulfits, tramussos, mol·luscs

### ingredients
- Ingredients reals de cuina
- Relació N:M amb `allergens` via `ingredient_allergens`

### dishes
- Plats del catàleg de Cal Blay
- Relació N:M amb `ingredients` via `dish_ingredients`
- `dish_ingredients` inclou `quantity` (ex: 200) i `unit` (ex: g, ml, unitats)

### menus
- Agrupació de plats (primer, segon, postres, etc.)
- Relació N:M amb `dishes` via `menu_dishes`

## Funcionalitats que permet

### Alertes automàtiques
Comensal té al·lèrgia a X → sistema creua amb ingredients dels plats → **alerta**

### Suggeriment d'alternatives
Mateixa lògica invertida: retorna plats del menú que **no** contenen l'al·lèrgen

### Recompte d'ingredients per event
Gràcies a `quantity` i `unit` a `dish_ingredients`:
```
200 comensals × 200g farina per plat = 40kg farina necessaris
```
**Requisit**: Cal Blay ha de proporcionar receptes amb gramatges
