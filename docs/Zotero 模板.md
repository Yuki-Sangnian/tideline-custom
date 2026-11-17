---
title: "{{title | replace('"', "'")}}"
citekey: "{{citekey}}"
itemType: "{{itemType}}"
{%- if date %}
year: {{date | format("YYYY")}}
{%- endif %}
authors: "{% for c in creators %}{% if not loop.first %}、{% endif %}{% if c.name %}{{c.name}}{% else %}{{ (c.lastName + " " + c.firstName) | trim | replace(r/([㐀-鿿]) ([㐀-鿿])/g, "$1$2") }}{% endif %}{% endfor %}"
zotero: "{{desktopURI}}"
{%- if importDate %}
added: {{importDate | format("YYYY-MM-DD")}}
{%- endif %}
keywords:
{%- for t in tags %}
  - "{{t.tag | replace('"', "'")}}"
{%- endfor %}
---
## 摘要
{{abstractNote}}

## 摘录
{%- for a in annotations %}
{%- if a.annotatedText %}
- {{a.annotatedText | replace("\n", " ")}}{% if a.comment %}（{{a.comment | replace("\n", " ")}}）{% endif %}
{%- endif %}
{%- endfor %}

## 笔记
