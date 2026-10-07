# skills-equipo — Skills auditadas del equipo WD-Soluciones

Tap de skills para todos los agentes del equipo (Hermes, OpenClaw/Ruper, OpenCode, Qwen, Antigravity).
**Repo privado.** Skills seleccionadas del **Skills Hub oficial de Hermes** para:

- creación de **páginas web** y landings
- **mini apps / PWA** y herramientas web
- **publicación/despliegue** (GitHub/Netlify/Cloudflare, incluso sin cuenta)

## Cómo suscribirse (Hermes / OpenClaw-lineage)

```bash
hermes skills tap add suasesorimac-jpg/skills-equipo
hermes skills tap list
hermes skills search landing --source github     # ya aparecen las del tap
```

Para OpenCode/Qwen/Antigravity (no leen taps): copiar la carpeta `skills/<nombre>/` a su carpeta de skills
(o apuntar su config a esta carpeta). Las skills son markdown plano (estándar **agentskills.io**).

## Qué contiene

| Skill | Para qué | Origen | Trust |
|---|---|---|---|
| `frontend-design` | criterio de diseño de interfaz (anti "AI slop") | anthropics/skills | trusted |
| `webapp-testing` | probar webs/mini apps de verdad con Playwright | anthropics/skills | trusted |
| `publish-site` | deploy versionado + rollback (GitHub/Cloudflare/Netlify Pages) | Nous (official) | official |
| `cloudflare-temporary-deploy` | publicar en vivo **sin cuenta ni credenciales** | Nous (official) | official |
| `impeccable` | guía de diseño frontend + detector de defectos UI | Nous (official; upstream pbakaus/impeccable) | official |
| `auteur` | páginas tipo cinematográfico (scroll/motion) | Nous (official) | official |
| `live-dashboard` | dashboards que se auto-actualizan | Nous (official) | official |

## Auditoría (no instalar sin leer)

- Se descargó **`SKILL.md` + todos los anexos** de cada skill y se escaneó: tuberías a shell (`curl|sh`),
  `rm -rf` sobre raíz, base64, `eval/exec`, claves SSH, volcado de entorno, llamadas salientes,
  exfiltración (ngrok/webhook.site), subprocesos y persistencia.
- **Resultado: sin hallazgos peligrosos.** El escáner propio de Hermes (`skills-guard-v7`) dio
  **ALLOWED** en las 7. Evidencia cruda en `auditoria/`.
- ⚠️ **`impeccable`**: su `SKILL.md` oficial es un envoltorio del upstream `pbakaus/impeccable`;
  trae JS minificado y **puede instalar hooks** en Claude Code / Codex / Cursor / Gemini / Copilot.
  **NO activar sus hooks** sin autorización explícita del PO. En la instalación no creó ninguno (opt-in).

## Regla del equipo

Skills de fuente **comunitaria** (ClawHub, skills.sh masivo) **no** entran aquí sin auditoría previa.
Todo lo que se añada a este repo debe pasar el mismo escrutinio y quedar registrado en `auditoria/`.
