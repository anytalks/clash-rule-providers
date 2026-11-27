# Mihomo rule providers

This public repository stores Mihomo rule-provider snapshots and personal routing rules. A companion config is kept separate because it contains the private proxy-node section.

## Layout

- `rules/self.list` is the editable source for custom rules inferred from the original config. It lists each match rule with its route.
- `rules/self-*.yaml` are the provider payloads consumed by the config. Keep them aligned with `self.list` when changing a custom rule.
- `rules/surge/self.list` is the editable source for Surge custom rules (`TYPE,VALUE,POLICY[,OPTIONS]`), including Meta/Muse, Google/Antigravity, Emby, and personal routing rules.
- `rules/surge/self-*.list` are pure-match Surge `RULE-SET` payloads generated from `rules/surge/self.list` (regenerated automatically by the sync workflow), and `rules/surge/url-reject.list` stores migrated `URL-REGEX` ad-blocking rules.
- `rules/geosite/`, `rules/geoip/`, `rules/classical/`, and `rules/ipcidr/` contain refreshed upstream snapshots.
- `rules/sources.tsv` maps each refreshed file to its upstream source.
- `.github/workflows/sync-rule-providers.yml` has a manual **Sync rule providers** action. Run it from the GitHub Actions page to download the newest upstream snapshots. It does not change personal rules.

## Routing groups

- `Google` isolates all Google-ecosystem services (including Gemini, Antigravity, Vertex AI, Firebase Studio, YouTube, Google FCM, Google Scholar, and Google IPs) by combining `rules/self-google.yaml`, `rules/geosite/google.mrs`, `rules/geosite/google-gemini.mrs`, `rules/geosite/youtube.mrs`, `rules/classical/googlefcm.yaml`, and `rules/geoip/google.mrs`. Google entries (including YouTube IP CIDRs) are stripped from `rules/self-ai.yaml`, `rules/self-domestic.yaml`, `rules/classical/global-media.yaml`, `rules/classical/scholar.yaml`, and `rules/classical/proxy.yaml` (preserved automatically by the sync workflow). Google ad domains remain in `ads` / `app-clean` for ad blocking.
- `AI` combines the upstream `category-ai-!cn` and `category-ai-cn` snapshots with the custom non-Google AI endpoints in `rules/self-ai.yaml` (including SpaceXSI/Grok/Cursor auth, OpenAI/Anthropic/MCP helpers, and major AI coding, inference, and media platforms). Claude/Anthropic keywords are stripped from `rules/classical/global-media.yaml` on sync so they stay routed to the AI group. In the companion config, `ChatGpt` routes non-Google AI providers (`self-ai`, OpenAI, Anthropic) after `Google`.

## Sources

- [MetaCubeX/meta-rules-dat](https://github.com/MetaCubeX/meta-rules-dat) for compiled MRS geosite and geoip data.
- [Centralmatrix3/Matrix-io](https://github.com/Centralmatrix3/Matrix-io) for GitHub, Microsoft, WeChat, Speedtest, proxy, and media rules.
- [Repcz/Tool](https://github.com/Repcz/Tool) for Surge native rule-sets.
- [dler-io/Rules](https://github.com/dler-io/Rules) for Google FCM and Scholar rules.
- [ACL4SSR/ACL4SSR](https://github.com/ACL4SSR/ACL4SSR) for app-clean rules.
- [Loyalsoldier/clash-rules](https://github.com/Loyalsoldier/clash-rules) for application and LAN CIDR lists.

The rules are mirrored from those upstream projects. Please also follow their attribution and licensing terms.

## Privacy
