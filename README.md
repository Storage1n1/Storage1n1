# Saksham Swami

Architect of AI-driven trading systems and generative-media engines — the
kind of work where an LLM is a component inside a larger deterministic
system, not the whole system. I design the guardrails, contracts, and state
machines that make it safe to let a model make real decisions (place a
trade, edit a document, direct a 3D scene) inside a larger, more predictable
architecture.

## Projects

### AI agents & generative media
- **[Asset Studio](https://github.com/Storage1n1/asset-studio)** — LLM-authored, directly-editable motion design templates. An LLM never draws pixels or writes animation code — it writes a document (brief → storyboard → manifest), rendered by one deterministic runtime shared with the human editor. Patch-based edits only; regeneration is treated as the failure mode.
- **[Parallax Scene Maker](https://github.com/Storage1n1/parallax-scene-maker)** — a vision-language model closes a self-correcting loop over a real-time 3D (Three.js) parallax scene: it stages assets, critiques its own composition snapshot against a strict validated contract, fixes itself, and renders an animated camera dolly.
- **[Local Computer-Use Agent](https://github.com/Storage1n1/local-computer-use-agent)** — a free, fully offline alternative to Claude Computer Use / OpenAI Operator (ChatGPT Atlas) / Project Mariner: small local vision-language models drive a real desktop via Set-of-Marks grounding and crop-zoom super-resolution instead of raw pixel-coordinate prediction, so a small model never has to be good at something it's bad at.

### Algorithmic trading
- **[MT5 Grid Precision Engine](https://github.com/Storage1n1/mt5-grid-precision-engine)** — a bidirectional breakout-grid trading bot for MetaTrader 5, with a chop-range guard that suspends only the levels stuck in a losing range and a live Tkinter dashboard.
- **[Tele Trade Signal Bot](https://github.com/Storage1n1/tele-trade-signal-bot)** — reads a Telegram signal channel, parses text/image calls into structured trades with an LLM, sizes and gates every entry through a small-account risk manager (daily loss cap, drawdown halt, over-risk approval), and executes on MT5 in paper or live mode behind one shared interface.

## How I build

- **The model writes data, not code.** Whether it's a trading signal, a
  design manifest, or a 3D scene edit, the LLM's output is always a
  constrained, schema-validated document — never markup or logic that
  executes directly.
- **Fail closed.** Every system here has an explicit behavior for "the model
  said something incoherent" — clamp it, reject it, or halt, rather than
  trust it.
- **Replay and audit before trusting a system with real money or real
  output.** Both trading bots include offline replay/simulation tooling that
  drives the exact production decision logic over historical data before
  anything goes live.
