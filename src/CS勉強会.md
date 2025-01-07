---
marp: true
theme: default
paginate: true
lang: "ja"
header: "データサイエンティストのためのソフトウェア工学入門"
footer: "©2025 Satoshi Yoshimura"
style: |
  @import url('../style/custom.css');
  .mermaid { 
    font-size: 16px;
    font-family: "Hiragino Kaku Gothic ProN", "メイリオ", sans-serif;
  }
math: mathjax
mermaid: true
---

<!-- Mermaidを読み込み -->
<script type="module">
import mermaid from 'https://cdn.jsdelivr.net/npm/mermaid@11.4.1/dist/mermaid.esm.min.mjs';
mermaid.initialize({ startOnLoad: true });
</script>

# データサイエンティストのための

# ソフトウェア工学入門

<div style="display: flex; justify-content: center;">
    <img src="../images/study-cs-top.jpeg" alt="ソフトウェア工学" style="border-radius: 10px; width: 50%;">
</div>

---

# 目次

1. ソフトウェア工学の重要性
   - なぜソフトウェア工学が必要か？
   - 車輪の再発明を防ぐ
   - 巨人の肩に乗る
2. 用法用量を守って
   - 高度化するソフトウェア開発
   - 適切なコーディング手法の選択
   - 帰納と演算
   - 個人とチームと消費期限
3. 効果的なコーディング手法
   - コメントの重要性
   - 可読性の高いコード作成

---

4. 開発環境の構築と活用
   - VSCode と Jupyter Notebook
   - devcontainer による環境統一
5. AI ツールの活用
   - GitHub Copilot の活用
   - Cursor の活用

---

# 1. ソフトウェア工学の重要性

<pre class="mermaid">
mindmap
  root((ソフトウェア工学))
    車輪の再発明を防ぐ
      既存ライブラリの活用
      ベストプラクティス
      設計パターン
    巨人の肩に乗る
      オープンソース
      コミュニティ
      ドキュメント
    効率的な開発
      チーム開発
      品質管理
      保守性
</pre>

---

## 1.1 なぜソフトウェア工学が必要か？

データサイエンティストにとって、ソフトウェア工学の知識が重要な理由：

- **再現性の確保**

  - 分析結果の再現
  - 他者との共同作業

- **保守性の向上**
  - 6 ヶ月後の自分が理解できるコード
  - チームでの開発効率向上

---

## 1.2 車輪の再発明を防ぐ

<div style="display: flex; justify-content: center; gap: 2rem;">
  <div>
    <p style="font-weight: bold;">既存ライブラリの活用</p>
    <p>欲しい機能は既にある可能性が高い</p>
    <p>機能の再開発に時間をかける必要がない</p>
    <p>バグが発生する可能性が低い</p>
  </div>

  <div style="flex-shrink: 0;">
    <img src="../images/wheel.jpeg" alt="ソフトウェア工学" style="border-radius: 10px;">
  </div>
</div>

---

## 1.3 巨人の肩に乗る

<div style="display: flex; justify-content: center; gap: 2rem;">
  <div>
    <p style="font-weight: bold;">オープンソース</p>
    <p >先人たちの知見を活用</p>
    <p >保守性が高い</p>
    <p style="font-weight: bold;">機能拡張</p>
    <p >自分では思いつかないような機能を利用できる</p>
    <p >人生は有限</p>

  </div>

  <div style="flex-shrink: 0;">
    <img src="https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEg6pU3mr8LH5-kB5YXc8E2S87r4w7vzFbcpP7R1VawTuSNpMuRLtBy7m26ENkIFPTWNPsdA5ZqCDWZIQOSZgOfGMBPdfljl7z9THJqrivOY5thSJmbL2Dqw5L08cm81bRJWTb2nTvjCowWc/s800/monogatari_kyojinno_katani_noru.png" alt="ソフトウェア工学" width="400">
  </div>
</div>

---

# 2. 用法用量を守って

高度化するソフトウェア開発の手法を利用することは重要ですが、その利用にはユースケースに応じた手法を選択することが重要です。

---

## 2.1 高度化するソフトウェア開発

<pre class="mermaid">
graph TD
    A[個人開発] --> B[チーム開発]
    B --> C[大規模開発]
    C --> D[保守・運用]
    
    E[帰納的アプローチ] --> F[演繹的アプローチ]
    F --> G[ハイブリッドアプローチ]
</pre>

---

## 2.2 適切なコーディング手法の選択

```c
// メモリー割当
#include <stdlib.h>

void memory_leak_example() {
    int *ptr = (int *)malloc(10 * sizeof(int));
    // メモリーリーク: mallocで確保したメモリが解放(free)されていない
}
```

<div style="display: flex; justify-content: center; gap: 2rem;">

  <div style="flex-shrink: 1;">
    <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ6f9Q4ISQd5SbWoFTdrtGE5xZkelLUbPxKDA&s" alt="ミサイル" style="border-radius: 10px;">
  </div>
    <div style="flex-shrink: 1;">
    <img src="../images/space-rocket.jpg" alt="スペースシャトル" style="border-radius: 10px;">
  </div>
</div>

---

## 2.3 帰納と演算

### 帰納的アプローチ

帰納的アプローチは、**具体的な事例や観察から一般的な法則や原理を導き出す手法**です。これは、個々のケースを分析し、それらの共通点やパターンを見つけ出すことで、より広範な結論を得ることを目指します。

例えば、データサイエンスの分野では、様々なデータセットを分析して、その中で共通するパターンや傾向を見つけ出すことが多くあります。このような分析を通じて、新しいデータセットに対しても同様の傾向があると推測することができます。

帰納的アプローチの利点は、実際のデータや経験に基づいているため、現実的で実践的な解決策を提供できる点です。しかし、観察された事例が限られている場合や、偏りがある場合には、導き出された結論が必ずしも正確でない可能性があるため、注意が必要です。

---

### 帰納的アプローチの例

```python

import pandas as pd
from typing import Dict

# データセットの基本的な統計量を計算する
def calculate_metrics(data: pd.DataFrame) -> Dict[str, float]:
    # 統計量を計算する
    return {
        'mean': data.mean().to_dict(),
        'median': data.median().to_dict(),
        'std_dev': data.std().to_dict()
    }

# サンプルデータの作成
data = pd.DataFrame({
    'A': [1, 2, 3, 4, 5],
    'B': [5, 4, 3, 2, 1]
})

# 統計量の計算
metrics = calculate_metrics(data)
print(metrics)

```

---

## 2.3 帰納と演算

### 演繹的アプローチ

演繹的アプローチは、**一般的な原理や法則から具体的な結論や予測を導き出す手法**です。これは、既存の理論や原理を前提として、それらを論理的に推論することで、新しい結論を得ることを目指します。

例えば、特定の設計パターンが成功を収めていることを観察した場合、その設計パターンが他のプロジェクトでも有効であると推測することができます。このようにして得られた知見は、新しいプロジェクトにおける意思決定や戦略の策定に役立ちます。

ソフトウェア開発においては、演繹的アプローチは一般的な手法であり、原理原則を絶対のものとして最適な設計や実装を行っていきます。

---

## 2.4 個人とチームと消費期限

ソフトウェア開発においては通常、複数人での開発が行われます。
そのため、**「自分だけが分かれば良いコード」ではなく、「チームでも分かるコード」** を作成することが重要です。

この点でもデータサイエンスにおけるコーディングとは異なる点があると思います。
多くのケースではデータサイエンティストは一人でコーディングを行うことが多いため、再利用性やコメントの重要性は低いものになっているかと思います。
また、成果物であるコードについても、保守性やメンテンナンス性を高く保つ必要があるケースは稀であるため、コードの可読性、保守性、再利用性は低いものであっても構いません。

ただ、**「1 ヶ月後の自分は他人」** という認識を持つことで、未来の自分が困らないコーディングを行うことはとても重要なものであると考えています。

---

# 3. 効果的なコーディング手法

## 3.1 コメントの重要性

```python
# 悪いコメントの例
def calculate_metrics(data: pd.DataFrame) -> Dict[str, float]:
    # データをクリッピングする
    cleaned_data = clip_outliers(data, percentile=99)
    # 統計量を計算する
    return compute_statistics(cleaned_data)
```

---

```python
# 良いコメントの例
def calculate_metrics(data: pd.DataFrame) -> Dict[str, float]:
    """データセットの基本的な統計量を計算する

    Args:
        data: 分析対象のデータフレーム
    Returns:
        統計量の辞書（平均、中央値、標準偏差など）
    """
    # 異常値の影響を軽減するため、99パーセンタイルでクリッピング
    cleaned_data = clip_outliers(data, percentile=99)
    return compute_statistics(cleaned_data)
```

---

# 4. 開発環境の構築と活用

<pre class="mermaid">
graph LR
    A[VSCode] --> B[Jupyter拡張]
    B --> C[対話的開発]
    
    D[devcontainer] --> E[環境統一]
    E --> F[再現性確保]
</pre>

---

# 5. AI ツールの活用

## 5.1 GitHub Copilot の活用

<pre class="mermaid">
flowchart LR
    A[コメント記述] --> B[Copilot提案]
    B --> C[コード生成]
    C --> D[レビュー・修正]
    D --> E[最終化]
</pre>

## 5.2 Cursor の活用

- コード補完
- リファクタリング支援
- エラー検出

---

# 6. ベストプラクティス

## 6.1 コードレビュー

<pre class="mermaid">
graph TD
    A[コード作成] --> B[自動テスト]
    B --> C[コードレビュー]
    C --> D{承認}
    D -->|Yes| E[マージ]
    D -->|No| F[修正]
    F --> A
</pre>

## 6.2 テスト駆動開発

```python
def test_data_preprocessing():
    """データ前処理のテストケース"""
    # テストデータの準備
    test_data = pd.DataFrame({
        'value': [1, 2, None, 4, 5]
    })

    # 前処理の実行
    processed_data = preprocess_data(test_data)

    # 結果の検証
    assert processed_data['value'].isna().sum() == 0
```

---

# まとめ

- ソフトウェア工学の基礎を理解する
- 適切なツールと手法を選択する
- チーム開発のベストプラクティスを実践する
- AI ツールを効果的に活用する

---

# 参考資料・Q&A

## 参考資料

- [Clean Code](https://www.amazon.co.jp/Clean-Code-%E3%82%A2%E3%82%B8%E3%83%A3%E3%82%A4%E3%83%AB%E3%82%BD%E3%83%95%E3%83%88%E3%82%A6%E3%82%A7%E3%82%A2%E9%81%93-%E3%83%AD%E3%83%90%E3%83%BC%E3%83%88%E3%83%BBC%E3%83%BB%E3%83%9E%E3%83%BC%E3%83%81%E3%83%B3/dp/4048676881)
- [VSCode Documentation](https://code.visualstudio.com/docs)
- [GitHub Copilot](https://github.com/features/copilot)

## Q&A

ご質問やご意見をお待ちしています。
