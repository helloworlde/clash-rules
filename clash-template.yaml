mixed-port: {{ default(global.clash.socks_port, "7890") }}
allow-lan: {{ default(global.clash.allow_lan, "true") }}
log-level: {{ default(global.clash.log_level, "error") }}
external-controller: :9090
mode: rule

{% if default(request.profile.tracing, "") == "1" %}
profile:
  tracing: true
{% endif %}

{% if default(request.clash.dns, "") == "1" %}
dns:
  enable: true
  listen: 127.0.0.1:8853
  default-nameserver:
    - 223.5.5.5
    - 1.0.0.1
  ipv6: true
  fallback:
    - https://dns.rubyfish.cn/dns-query
    - https://public.dns.iij.jp/dns-query
    - tls://8.8.4.4
  fallback-filter:
    geoip: true
    ipcidr:
      - 240.0.0.0/4
      - 0.0.0.0/32
      - 127.0.0.1/32
{% else if default(request.clash.dns, "") == "2" %}
dns:
  enable: true
  listen: 127.0.0.1:5533
  ipv6: true
  default-nameserver:
    - 119.29.29.29
    - 223.5.5.5
  nameserver:
    - https://doh.pub/dns-query
    - https://dns.alidns.com/dns-query
  fallback:
    - https://1.1.1.1/dns-query
    - https://dns.google/dns-query
  fallback-filter:
    geoip: true
    geoip-code: CN
    ipcidr:
      - 240.0.0.0/4
      - 0.0.0.0/32
      - 127.0.0.1/32
{% else if default(request.clash.dns, "") == "3" %}
dns:
  enable: true
  listen: 127.0.0.1:5533
  ipv6: true
  default-nameserver:
    - 127.0.0.1:5533
  nameserver:
    - 127.0.0.1:5533
  fallback:
    - 127.0.0.1:5533
  fallback-filter:
    geoip: true
    geoip-code: CN
    ipcidr:
      - 240.0.0.0/4
      - 0.0.0.0/32
      - 127.0.0.1/32
{% endif %}

proxies: ~
proxy-groups: ~
rules: ~
