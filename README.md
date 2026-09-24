# Mihomo rule providers

This public repository stores the provider snapshots used by [clash-o.yaml](https://raw.githubusercontent.com/anytalks/clash-rule-providers/main/clash-o.yaml) consumers, plus personal routing rules. The local config file is intentionally **not** mirrored here because it contains proxy credentials.

## Layout

- `rules/self.list` is the editable source for custom rules inferred from the original config. It lists each match rule with its route.
- `rules/self-*.yaml` are the provider payloads consumed by the config. Keep them aligned with `self.list` when changing a custom rule.
- `rules/geosite/`, `rules/geoip/`, `rules/classical/`, and `rules/ipcidr/` contain refreshed upstream snapshots.
- `rules/sources.tsv` maps each refreshed file to its upstream source.
- `.github/workflows/sync-rule-providers.yml` has a manual **Sync rule providers** action. Run it from the GitHub Actions page to download the newest upstream snapshots. It does not change personal rules.

## Sources

- [MetaCubeX/meta-rules-dat](https://github.com/MetaCubeX/meta-rules-dat) for compiled MRS geosite and geoip data.
- [blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script) for proxy, global media, China media, Google FCM, and NetEase Music rules.
- [ACL4SSR/ACL4SSR](https://github.com/ACL4SSR/ACL4SSR) for app-clean rules.
- [Loyalsoldier/clash-rules](https://github.com/Loyalsoldier/clash-rules) for application and LAN CIDR lists.

The rules are mirrored from those upstream projects. Please also follow their attribution and licensing terms.

## Privacy

The public files contain the custom service/domain names listed in `rules/self.list`. Proxy nodes, UUIDs, passwords, and other credentials from the source config are excluded.
