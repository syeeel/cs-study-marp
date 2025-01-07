# データサイエンティストのためのソフトウェア工学入門

# Mermaid を記述する方法

<!-- Marpと認識させるおまじない -->

## Basic Pie Chart

<!-- class名をmermaidとした要素タグ内に出力するMermaidコードを記載 -->
<pre class="mermaid">
pie title What Voldemort doesn't have?
  "FRIENDS" : 5
  "FAMILY" : 3
  "NOSE" : 45
</pre>

<!-- Mermaidを読み込み -->
<script type="module">
import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@11.4.1/dist/mermaid.esm.min.mjs';
mermaid.initialize({ startOnLoad: true });
</script>

# HTML 生成コマンド

```
npx marp src/CS勉強会.md --html --allow-local-files -o docs/index.html
```

# PDF 生成コマンド

```
npx marp src/CS勉強会.md --pdf --allow-local-files -o docs/index.pdf
```
