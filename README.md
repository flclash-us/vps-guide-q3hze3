# Clash 规则配置完全指南

深入了解 Clash 规则系统，实现精准分流。

## 规则类型详解

### GEOIP 规则（最重要）

```yaml
rules:
  # 中国IP直连
  - GEOIP,CN,DIRECT
  # 非中国IP走代理
  - GEOIP,!CN,Proxy
```

### 域名规则

```yaml
rules:
  # 精确域名
  - DOMAIN,www.google.com,Proxy
  # 域名后缀（最常用）
  - DOMAIN-SUFFIX,google.com,Proxy
  # 域名关键字
  - DOMAIN-KEYWORD,google,Proxy
```

## 规则集（Rule Providers）

现代 Clash 推荐使用规则集：

```yaml
rule-providers:
  ads:
    type: http
    behavior: domain
    url: "https://cdn.jsdelivr.net/gh/Loyalsoldier/clash-rules@release/rules/denylist.txt"
    interval: 86400
```

## 常用规则集推荐

| 规则集 | 地址 | 说明 |
|--------|------|------|
| Loyalsoldier | GitHub | 全面的分流规则 |
| blackmatrix7 | GitHub | 每日更新 |

## 常见问题

**规则不生效？** 检查规则顺序，Clash 按顺序匹配首个命中的规则。

---

推荐工具：

- [Clash for Windows](https://clashforwindows.site/)
- [ClashMI](https://clashmi.site/)
- [FlClash](https://flclash.us/)
