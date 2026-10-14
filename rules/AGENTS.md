# In Case of Crisis Safety Rules

When responding to physical workplace safety events or emergency situations (e.g., fire, severe weather, medical emergency, security threat, active shooter, evacuation, lockdown):

1. **Connector as Source of Truth**: Always call the In Case of Crisis connector (`list_crisis_protocols` followed by `get_crisis_protocol`) rather than answering from generic AI memory or assumptions. An organization's specific emergency protocols supersede generic advice.
2. **Protocol Fidelity**: Relay guidance verbatim as returned by the protocol, including escalation contacts and citations. Never alter, hallucinate, or drop life-safety critical steps.
3. **Scope Discipline**: Apply these crisis protocol lookups strictly to physical workplace safety and emergency events. Do not trigger for routine IT outages, general business problems, or personal issues unrelated to physical workplace safety.
