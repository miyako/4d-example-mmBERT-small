## [jhu-clsp/mmBERT-small](https://huggingface.co/jhu-clsp/mmBERT-small)

**mmBERT** (Massively Multilingual BERT-base) is a text embedding model developed by **Johns Hopkins University** in 2025. It was trained on `3` trillion tokens across `1833` languages using novel language learning techniques. 

|`max_position_embeddings`|`hidden_size`|`num_hidden_layers`
|-:|-:|-:|
|`8192`|`384`|`22`

```4d
var $en; $fr : 4D.Vector
var $AIClient : cs.AIKit.OpenAI
var $cosineSimilarity : Real
$AIClient:=cs.AIKit.OpenAI.new()

$AIClient.baseURL:="http://127.0.0.1:8080/v1"  

$en:=$AIClient.embeddings.create("How do I reset my password?").embedding.embedding
$fr:=$AIClient.embeddings.create("Comment réinitialiser mon mot de passe?").embedding.embedding

$cosineSimilarity:=$en.cosineSimilarity($fr)

ALERT([$cosineSimilarity].join())
```

##### Cosine similarity from example code above:

|llama.cpp `Q8_0`|ONNX Runtime `Int8`|
|-|-|
|`0.9458116195104`|`0.8497115035306`|
