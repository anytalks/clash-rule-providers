# Mihomo rule providers

This public repository stores Mihomo rule-provider snapshots and personal routing rules. A companion config is kept separate because it contains the private proxy-node section.

## Layout

- `rules/self.list` is the editable source for custom rules inferred from the original config. It lists each match rule with its route.
- `rules/self-*.yaml` are the provider payloads consumed by the config. Keep them aligned with `self.list` when changing a custom rule.
- `rules/geosite/`, `rules/geoip/`, `rules/classical/`, and `rules/ipcidr/` contain refreshed upstream snapshots.
- `rules/sources.tsv` maps each refreshed file to its upstream source.
- `.github/workflows/sync-rule-providers.yml` has a manual **Sync rule providers** action. Run it from the GitHub Actions page to download the newest upstream snapshots. It does not change personal rules.

## Routing groups

The companion Clash config uses the same 16 routing group names as the local Surge `Default.conf`. GitHub matches `其他地址` before Microsoft rules. Generic foreign proxy rules and unmatched traffic also use `其他地址`; Chinese domain and IP rules retain `国内地址`.

## Sources

- [MetaCubeX/meta-rules-dat](https://github.com/MetaCubeX/meta-rules-dat) for compiled MRS geosite and geoip data.
- [blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script) for GitHub, Microsoft, WeChat, Speedtest, Scholar, proxy, and media rules.
- [ACL4SSR/ACL4SSR](https://github.com/ACL4SSR/ACL4SSR) for app-clean rules.
- [Loyalsoldier/clash-rules](https://github.com/Loyalsoldier/clash-rules) for application and LAN CIDR lists.

The rules are mirrored from those upstream projects. Please also follow their attribution and licensing terms.

## Privacy
