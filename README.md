# In Case of Crisis — Gemini Plugin

Surfaces an organization's own approved crisis, emergency, and incident-response protocols the moment a workplace safety situation comes up in conversation.

Built by [RockDove Solutions](https://www.rockdovesolutions.com). Ported from the [incaseofcrisis/claude](https://github.com/incaseofcrisis/claude) integration to the Google Gemini / Antigravity plugin platform.

---

## Bundled Components

| Component | Path / Details | Description |
|---|---|---|
| **Skill** | `skills/in-case-of-crisis/SKILL.md` | Guides Gemini on when to invoke the crisis connector (fires, severe weather, medical emergencies, lockdowns, evacuations) and how to search for and retrieve the appropriate protocol. |
| **MCP Connector** | `mcp_config.json` | Connects directly to In Case of Crisis's hosted gateway (`https://mcpgateway.incaseofcrisis.com/mcp`) over Streamable HTTP. |
| **Rules** | `rules/AGENTS.md` | Enforces verbatim fidelity and prioritization of official crisis protocols over AI model memory during physical emergencies. |

---

## Setup & Prerequisites

1. **In Case of Crisis Account**: An organization must have an active In Case of Crisis account with their emergency preparedness protocols published. No protocol content is stored locally inside this plugin; it retrieves your organization's live data on demand.
2. **Account Authorization**: The first time the connector is called, you may be prompted to complete a one-time OAuth consent workflow to link your organization's In Case of Crisis account.

---

## Connector Tools

The hosted MCP server exposes two core tools used in sequence:

| Tool | Purpose | Key Inputs |
|---|---|---|
| `list_crisis_protocols` | Searches and browses approved crisis, emergency, and incident-response protocols. | `query` (situation in user's words; omit to browse all), `protocol_type` (`All`, `Custom`, or `Sponsored`) |
| `get_crisis_protocol` | Retrieves verbatim procedure text, escalation contacts, and citations for a specific protocol. | `event_id` (unique protocol ID from `list_crisis_protocols`), `asked` (user's original question), `name` (protocol name) |

---

## Example Prompts

- *"There's a fire reported on the 3rd floor, what are our immediate evacuation steps?"*
- *"What is our organization's severe weather and tornado protocol?"*
- *"Walk me through our facility lockdown and security threat procedure."*
- *"Show all emergency and crisis protocols available in our plan."*

---

## Safety & Compliance

- **No Paraphrasing of Critical Steps**: Guidance is returned verbatim with escalation contacts and citations to avoid omissions or distortion of life-safety instructions.
- **Strict Scope**: Triggers solely on physical workplace safety and emergency events, not routine IT incidents or general business operations.
- **Tenant Isolation**: Only authorized users with valid In Case of Crisis credentials can access their respective organization's proprietary plans.
