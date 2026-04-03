# Setup Node.js + pnpm

## 1. Instal·lar fnm (Fast Node Manager)

[fnm](https://github.com/Schniz/fnm) és un gestor de versions de Node.js ràpid i senzill. **No instal·leu Node.js directament** — sempre via fnm.

```bash
curl -fsSL https://fnm.vercel.app/install | bash
```

Després afegiu la configuració al vostre shell:

**Bash** — afegir a `~/.bashrc`:

```bash
eval "$(fnm env --use-on-cd --shell bash)"
```

**Zsh** — afegir a `~/.zshrc`:

```bash
eval "$(fnm env --use-on-cd --shell zsh)"
```

Reinicieu el terminal o feu `source ~/.bashrc` / `source ~/.zshrc`.

## 2. Instal·lar Node.js v24.13.0

```bash
fnm install 24.13.0
fnm use 24.13.0
fnm default 24.13.0
```

Verificar:

```bash
node --version
# v24.13.0
```

## 3. Instal·lar pnpm

**Sempre utilitzem pnpm**, mai npm ni yarn.

```bash
corepack enable
corepack prepare pnpm@latest --activate
```

Verificar:

```bash
pnpm --version
```

## 4. Per què fnm i no nvm?

- fnm és **molt més ràpid** que nvm (escrit en Rust)
- Canvia de versió automàticament quan entreu a un directori amb `.node-version` (gràcies a `--use-on-cd`)
- Compatible amb `.nvmrc` si algú el tenia abans
