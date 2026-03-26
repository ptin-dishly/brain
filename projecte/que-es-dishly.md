# Què és Dishly?

## El client: Cal Blay

Grup de restaurants de cuina tradicional catalana. 4-6 establiments grans amb múltiples sales, especialitzats en esdeveniments (casaments, comunions, dinars d empresa). 380 treballadors entre comercials, cuiners, cambrers i personal de sala.

## El problema

Cal Blay gestiona els al·lèrgens alimentaris de manera **100% manual**: notes en paper, trucades, comunicació verbal entre comercials, cuina i sala.

Amb centenars de comensals diaris i 14 al·lèrgens regulats per la UE, això provoca:

- **Errors per comunicació verbal** — un cambrer oblida un al·lèrgen, un cuiner no rep el canvi
- **Estrès del personal** — gestionar restriccions de memòria amb la pressió del servei
- **Risc sanitari real** — una reacció al·lèrgica pot ser greu o mortal
- **Pèrdua d ingredients** — sense control de quantitats, es compra de més o de menys

## La solució: Dishly

Plataforma web (PWA) que digitalitza tota la cadena de gestió d al·lèrgens:

### Els 4 actors

| Actor | Què fa amb Dishly |
|-------|-------------------|
| **Comercial** | Registra events, comensals i els seus al·lèrgens individuals |
| **Cuina** | Rep comandes amb restriccions, alertes automàtiques si hi ha conflicte, suggeriments d alternatives |
| **Cambrer** | Veu per taula/seient quin plat servir a qui i amb quines restriccions. Gestiona imprevistos sense moure s |
| **Comensal** | Escaneja QR → veu la carta amb al·lèrgens. Sense registre |

### Funcionalitats clau

1. **Catàleg de plats** amb ingredients i al·lèrgens (14 UE, Reglament 1169/2011)
2. **Alertes automàtiques** quan un plat conté un al·lèrgen d un comensal
3. **Suggeriment d alternatives** segures (plats sense l al·lèrgen conflictiu)
4. **Recompte d ingredients** per event (quantitats totals basades en gramatges)
5. **Propagació en temps real** (WebSockets) — qualsevol canvi arriba a cuina i sala al moment
6. **Traçabilitat** — cada acció queda registrada (qui, què, quan)

### Els 14 al·lèrgens regulats (UE)

Gluten, crustacis, ous, peix, cacauets, soja, llet, fruits de closca, api, mostassa, sèsam, diòxid de sofre/sulfits, tramussos, mol·luscs.

## Arquitectura

```
Frontend (PWA) ←— HTTP/WS —→ Backend (API + WebSockets) ←— SQL —→ PostgreSQL + Redis
```

Tot corre en contenidors Docker sobre una VM Debian 13.

## Equip

22 persones, 3 equips:

| Equip | Gent | Responsabilitat |
|-------|------|-----------------|
| Frontend (7) | PWA responsive, vistes per rol, QR públic |
| Backend (7) | API REST, WebSockets, auth, motor d alertes |
| BD (8) | Esquema, migracions, seeds, optimització |

## Repo

- [frontend](https://github.com/ptin-dishly/frontend)
- [backend](https://github.com/ptin-dishly/backend)
- [database](https://github.com/ptin-dishly/database)
- [docs](https://github.com/ptin-dishly/docs) — convencions
- [brain](https://github.com/ptin-dishly/brain) — aquest vault
