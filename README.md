<div align="center">
   <h1>自用clash规则,cn域名和特定网站直连(黑名单模式)</h1>
</div>

**目前 Clash 支持的规则类型如下：**

- DOMAIN-SUFFIX：域名后缀匹配
- DOMAIN：域名匹配
- DOMAIN-KEYWORD：域名关键字匹配
- IP-CIDR：IP 段匹配
- SRC-IP-CIDR：源 IP 段匹配
- GEOIP：GEOIP 数据库（国家代码）匹配
- DST-PORT：目标端口匹配
- SRC-PORT：源端口匹配
- PROCESS-NAME：源进程名匹配
- RULE-SET：Rule Provider 规则匹配
- MATCH：全匹配

```yaml
- DOMAIN-KEYWORD,dwai,🎯 全球直连
- DOMAIN-KEYWORD,cn,🎯 全球直连


regexp:.*.cn.*,
regexp:.*hunau.*,
regexp:.*baidu.*,
regexp:.*delivery.mp.microsoft.*,
regexp:.*163.*,
regexp:.*chaoxing.*,
regexp:.*bing.*,
regexp:.*steamserver.*,
regexp:.*steamstatic.*,
regexp:.*dwai.life.*,
regexp:.*tearemix.*,


keyword:baidu,
keyword:cn,
keyword:hunau,
keyword:baidu,
keyword:delivery.mp.microsoft,
keyword:163,
keyword:chaoxing,
keyword:bing,
keyword:steamserver,
keyword:steamstatic,
keyword:dwai.life,
keyword:tearemix,



```


**正则表达式原理：**

1. **普通字符匹配**：正则表达式中的普通字符，比如字母和数字，会直接匹配字符串中的相应字符。

2. **元字符使用**：特殊字符或元字符，如 `.`、`*`、`?`、`+`、`^`、`$`、`[]`、`()`、`|` 等，在正则表达式中具有特殊意义，它们可以指定更复杂的匹配模式，如匹配任意字符、重复字符、可选字符等。

3. **模式组合**：通过组合上述普通字符和元字符，可以创建非常复杂的匹配模式，以识别特定的字符串模式，例如URL。

**匹配URL的正则表达式原理：**

- **起始和结束**：通常正则表达式以 `^` 开始表示行的起始，以 `$` 结束表示行的结束，确保整个字符串匹配URL格式。
- **协议**：使用 `(https?|ftp)` 等来匹配URL的协议部分，其中 `?` 表示前面的字符是可选的，匹配http或https。
- **域名**：使用 `[a-zA-Z0-9.-]` 来匹配域名中的合法字符，包括字母、数字、点和连字符。
- **端口**：使用 `(:\d{1,5})?` 来匹配端口号，`?` 表示端口是可选的。
- **路径、查询和片段**：使用 `(/[\w/:%#\$&\?\(\)~\.=\+\-]*)?` 等来匹配URL的路径、查询参数和片段。

**关键词匹配原理：**

关键词匹配通常是指在文本中搜索指定的单词或短语。这种匹配通常不使用正则表达式那样复杂的模式，而是简单的字符串查找。

- **完全匹配**：关键词通常要求完全匹配，即文本中的单词必须与搜索词完全一致。
- **大小写敏感**：关键词匹配可能区分大小写，也可能不区分，这取决于具体的搜索工具或函数设置。

**区别：**

1. **复杂度**：正则表达式可以提供非常复杂的匹配模式，而关键词匹配通常比较简单，只针对具体的字符串。
2. **灵活性**：正则表达式可以根据需求灵活调整，匹配各种不同的模式，而关键词匹配通常只能匹配固定的字符串。
3. **性能**：由于正则表达式的复杂性，其匹配过程可能需要更多的时间和计算资源，而关键词匹配通常更快。
4. **使用场景**：正则表达式适用于需要识别复杂模式的场景，如验证输入、数据提取等；关键词匹配适用于简单的文本查找或搜索场景。
