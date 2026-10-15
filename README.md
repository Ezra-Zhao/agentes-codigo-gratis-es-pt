# 🆓 Guía rápida: agentes de código gratis — programa con IA sin pagar suscripción (ES · PT)

Una sola página para desarrolladores sin presupuesto: dos rutas reales para usar agentes de código (Claude Code, Codex, Cursor, OpenCode…) con **modelos gratuitos**, qué ganas con cada una y cómo conectar cada agente.

**Autor:** Ezra-Zhao · Octubre 2026

Proyectos originales:
- **free-claude-code (FCC)** — https://github.com/Alishahryar1/free-claude-code (más de 56.000 estrellas en octubre de 2026)
- **OmniRoute** — https://github.com/diegosouzapw/OmniRoute (más de 71.000 estrellas en octubre de 2026; hecho por un desarrollador brasileño)

> **Nota de autoría:** guía original de síntesis del autor; no reproduce la documentación de ninguno de los dos proyectos. Las cifras de tokens/proveedores son las que declara cada proyecto y pueden cambiar: los niveles gratuitos los controla cada proveedor.

---

## 🇪🇸 Español

### Primero: las dos rutas, frente a frente

| | **free-claude-code (FCC)** | **OmniRoute** |
|---|---|---|
| Qué es | Una capa que conecta tus agentes con proveedores que regalan tokens, cuidando no violar los términos de cada proveedor | Una pasarela (gateway) autoalojada con un solo endpoint compatible con OpenAI/Anthropic |
| Cifras que declara | 61 proveedores «ToS-friendly»; más de 1.300 millones de tokens gratis al mes entre todos | 359 proveedores, 150+ gratuitos, 1.200+ modelos |
| Agentes que cubre | 11: Claude Code, Codex, Pi, OpenCode, Cline, Hermes, DeepSeek Harness, Grok Build, Muse Code, Aider y VS Code Chat | Los que acepten endpoint compatible: Claude Code, Codex, Cursor, OpenCode, Cline, Copilot… |
| Instalación (macOS/Linux) | `curl -fsSL "https://raw.githubusercontent.com/Alishahryar1/free-claude-code/main/scripts/install.sh" \| sh` | `npm install -g omniroute` (o Docker: `docker run … diegosouzapw/omniroute`) |
| Cómo lo usa el agente | FCC deja cada agente configurado contra su catálogo de modelos | Apuntas el agente a `http://localhost:20128/v1` con tu clave de OmniRoute y modelo `auto` |
| Extras | Si un proveedor cae, salta al siguiente modelo configurado sin cortar tu sesión | Fallback consciente de cuotas + compresión de contexto que ahorra tokens |
| Licencia | AGPL-3.0 | MIT |
| Elige esta ruta si… | Quieres que **todo quede configurado** y solo programar | Quieres **control total** de la pasarela (equipo, varios agentes, tus reglas) |

### Después: conectar cada agente (una línea por agente)

| Agente | Cómo se conecta a la ruta gratis | ⚠️ Error típico |
|---|---|---|
| Claude Code | Con FCC: usa su lanzador y elige modelo del catálogo. Con OmniRoute: variables `ANTHROPIC_BASE_URL=http://localhost:20128` y tu clave de OmniRoute | Mezclar la suscripción de pago y la ruta gratis en el mismo entorno sin saber cuál está activa |
| Codex | Define un proveedor personalizado en `~/.codex/config.toml` con la `base_url` del gateway (o el cliente de FCC) | Apuntar Codex al endpoint equivocado (formato OpenAI vs. Anthropic no son intercambiables sin pasarela) |
| Cursor | Ajustes → Models → API de OpenAI: pega la clave del gateway y su URL base compatible | Cursor verifica la clave contra SU servidor en algunos planes: si falla, usa el agente dentro de VS Code (Cline) en su lugar |
| OpenCode | Añade un proveedor compatible en `opencode.json` con la URL base del gateway y el modelo elegido | Dejar el modelo en un nombre que el gateway no conoce: usa `auto` si la pasarela lo ofrece |
| Cline (VS Code) | En sus ajustes elige proveedor «OpenAI Compatible», URL base del gateway + clave | Cline gasta tokens rápido en modo autónomo: con modelos gratis, revisa el plan antes de aprobar pasos en cadena |
| Copilot / VS Code Chat | FCC lo lista entre sus 11 clientes; en VS Code Chat eliges el modelo del catálogo conectado | En empresas, las políticas de la organización pueden bloquear endpoints externos |
| Aider | Variables de entorno tipo `OPENAI_API_BASE` + `OPENAI_API_KEY` apuntando al gateway, o vía FCC | Aider aplica cambios directos al repo: trabaja en una rama y revisa el diff |
| Pi / Hermes / otros del catálogo FCC | Sigue el lanzador de FCC para ese cliente; comparten el mismo catálogo de modelos | Instalar cinco agentes «por probar» y no dominar ninguno: elige UNO y apréndelo |

### Reglas de supervivencia con modelos gratis

1. **Lo gratis cambia.** Un proveedor puede recortar su nivel gratuito mañana: ten siempre dos modelos configurados (la ruta de fallback lo hace por ti).
2. **Tus claves, en tu máquina.** Prefiere pasarelas autoalojadas (OmniRoute) o locales (FCC) antes que pegar claves en webs de terceros.
3. **Respeta los términos.** Si un proveedor marca su nivel gratis como «no para terceros» (en OmniRoute aparecen como `tos: avoid`), quedan fuera del enrutado automático: no fuerces la vuelta.
4. **Calidad desigual.** Reserva los modelos gratis para tareas mecánicas (renombrar, generar tests, andamiaje, explicar código) y revisa el diff como si lo hubiera escrito un becario rápido.
5. **El límite real es la cuota, no el precio.** Cuando el trabajo importa, combina: gratis para el volumen y, si un día pagas, una sola suscripción para lo crítico.

---

## 🇵🇹 Português

### Primeiro: as duas rotas, frente a frente

| | **free-claude-code (FCC)** | **OmniRoute** |
|---|---|---|
| O que é | Uma camada que liga seus agentes a provedores que dão tokens de graça, cuidando para não violar os termos de cada provedor | Um gateway auto-hospedado com um único endpoint compatível com OpenAI/Anthropic |
| Números que declara | 61 provedores «ToS-friendly»; mais de 1,3 bilhão de tokens grátis por mês somando todos | 359 provedores, 150+ gratuitos, 1.200+ modelos |
| Agentes que cobre | 11: Claude Code, Codex, Pi, OpenCode, Cline, Hermes, DeepSeek Harness, Grok Build, Muse Code, Aider e VS Code Chat | Os que aceitam endpoint compatível: Claude Code, Codex, Cursor, OpenCode, Cline, Copilot… |
| Instalação (macOS/Linux) | `curl -fsSL "https://raw.githubusercontent.com/Alishahryar1/free-claude-code/main/scripts/install.sh" \| sh` | `npm install -g omniroute` (ou Docker: `docker run … diegosouzapw/omniroute`) |
| Como o agente usa | O FCC deixa cada agente configurado contra o catálogo de modelos dele | Você aponta o agente para `http://localhost:20128/v1` com sua chave do OmniRoute e o modelo `auto` |
| Extras | Se um provedor cair, ele pula para o próximo modelo configurado sem cortar sua sessão | Fallback consciente de cotas + compressão de contexto que economiza tokens |
| Licença | AGPL-3.0 | MIT |
| Escolha esta rota se… | Você quer **tudo configurado** e só programar | Você quer **controle total** do gateway (equipe, vários agentes, suas regras) |

### Depois: ligar cada agente (uma linha por agente)

| Agente | Como se liga à rota grátis | ⚠️ Erro típico |
|---|---|---|
| Claude Code | Com o FCC: use o launcher dele e escolha o modelo do catálogo. Com o OmniRoute: variáveis `ANTHROPIC_BASE_URL=http://localhost:20128` e sua chave do OmniRoute | Misturar a assinatura paga e a rota grátis no mesmo ambiente sem saber qual está ativa |
| Codex | Defina um provedor personalizado em `~/.codex/config.toml` com a `base_url` do gateway (ou o cliente do FCC) | Apontar o Codex para o endpoint errado (formato OpenAI e Anthropic não são intercambiáveis sem gateway) |
| Cursor | Configurações → Models → API da OpenAI: cole a chave do gateway e a URL base compatível | O Cursor valida a chave contra o servidor DELE em alguns planos: se falhar, use um agente dentro do VS Code (Cline) no lugar |
| OpenCode | Adicione um provedor compatível no `opencode.json` com a URL base do gateway e o modelo escolhido | Deixar o modelo com um nome que o gateway não conhece: use `auto` se o gateway oferecer |
| Cline (VS Code) | Nas configurações, escolha o provedor «OpenAI Compatible», URL base do gateway + chave | O Cline gasta tokens rápido no modo autônomo: com modelos grátis, revise o plano antes de aprovar passos em cadeia |
| Copilot / VS Code Chat | O FCC o lista entre seus 11 clientes; no VS Code Chat você escolhe o modelo do catálogo conectado | Em empresas, as políticas da organização podem bloquear endpoints externos |
| Aider | Variáveis de ambiente tipo `OPENAI_API_BASE` + `OPENAI_API_KEY` apontando para o gateway, ou via FCC | O Aider aplica mudanças direto no repo: trabalhe numa branch e revise o diff |
| Pi / Hermes / outros do catálogo FCC | Siga o launcher do FCC para aquele cliente; todos dividem o mesmo catálogo de modelos | Instalar cinco agentes «para testar» e não dominar nenhum: escolha UM e aprenda ele |

### Regras de sobrevivência com modelos grátis

1. **O grátis muda.** Um provedor pode cortar o nível gratuito amanhã: tenha sempre dois modelos configurados (a rota de fallback faz isso por você).
2. **Suas chaves, na sua máquina.** Prefira gateways auto-hospedados (OmniRoute) ou locais (FCC) antes de colar chaves em sites de terceiros.
3. **Respeite os termos.** Se um provedor marca o nível grátis como «não para terceiros» (no OmniRoute aparecem como `tos: avoid`), eles ficam fora do roteamento automático: não force a barra.
4. **Qualidade desigual.** Reserve os modelos grátis para tarefas mecânicas (renomear, gerar testes, andaime, explicar código) e revise o diff como se fosse de um estagiário rápido.
5. **O limite de verdade é a cota, não o preço.** Quando o trabalho importa, combine: grátis para o volume e, se um dia você pagar, uma única assinatura para o que é crítico.

---

## 🇬🇧 English summary

One-page cheat sheet (Spanish + Portuguese) for coding for free with AI agents, comparing the two real routes: **free-claude-code** (a layer wiring 11 agent harnesses to ToS-friendly free-token providers, 1.3B+ free tokens/month as declared by the project) and **OmniRoute** (self-hosted MIT gateway, 359 providers / 150+ free / 1,200+ models, one endpoint at `localhost:20128/v1`). Includes a one-line hookup per agent (Claude Code, Codex, Cursor, OpenCode, Cline, Copilot/VS Code Chat, Aider…) with the typical mistake for each, plus survival rules for free tiers. Original synthesis by the author; figures are as declared by each project.

**Author:** Ezra-Zhao · October 2026 · MIT License
