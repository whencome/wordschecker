# words checker

一个简单的敏感词检测工具，用于对检测内容中出现的敏感内容进行检测评估。
conf/目录下提供了一份简单的敏感词列表，可以直接使用，也可以自己提供。

## 配置敏感词列表

敏感词列表配置一行一个，支持正则表达式。具体配置格式如下：
```text
// 普通关键词（适用于文本直接匹配）
QQ
// 支持自定义权重，在敏感词之后加上“ => 权重”，权重就是评分，默认都是1
微信 => 2
// 支持配置正则规则，使用“#rule#:”前缀
#rule#:[1-9]\d{5,}
// 正则规则也支持权重配置
#rule#:[1-9]\d{5,} => 3
```

## 使用方式

```go
// 1. 初始化词典，用于指定敏感词列表
InitDict("/home/www/conf/sensitive_words.conf")

// 2. 关键词评估
str := "这个是一段测试文本，欢迎加QQ123456。"
evaluator := NewEvaluator()
eval := evaluator.Evaluate(str)
```
