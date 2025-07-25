---
title: "HTML: コンテンツの作成"
slug: Learn_web_development/Getting_started/Your_first_website/Creating_the_content
l10n:
  sourceCommit: 5b20f5f4265f988f80f513db0e4b35c7e0cd70dc
---

{{LearnSidebar}}

{{PreviousMenuNext("Learn_web_development/Getting_started/Your_first_website/What_will_your_website_look_like", "Learn_web_development/Getting_started/Your_first_website/Styling_the_content", "Learn_web_development/Getting_started/Your_first_website")}}

HTML （**H**yper**T**ext **M**arkup **L**anguage、ハイパーテキスト・マークアップ・ランゲージ）は、ウェブサイトのコンテンツの構造を作るために使うコードです。例えば、コンテンツは段落、箇条書きのリスト、画像の使用、データテーブルなどの組み合わせで構成されています。タイトルが示すように、この記事では HTML とその機能の基本的な理解ができるように説明します。

<table>
  <tbody>
    <tr>
      <th scope="row">前提条件:</th>
      <td>
        コンピューターのオペレーティングシステム、ウェブサイトを構築する際に使用する基本ソフトウェア、およびファイルシステムに概ね慣れておくこと。
      </td>
    </tr>
    <tr>
      <th scope="row">学習成果:</th>
      <td>
        <ul>
          <li>HTML の目的と機能。</li>
          <li>HTML 構文の基本的な部分 — 開始タグと閉じられたタグ、要素、属性、見出し、本体。</li>
          <li>段落、見出し、画像、リスト、リンクなど、一般的な HTML 要素が含まれます。</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

## HTML とは

HTML は、コンテンツの構造を定義する*マークアップ言語*です。 HTML は一連の **{{Glossary("element", "要素")}}** で構成されており、これらの要素がコンテンツのさまざまな部分を囲み、一定の表示や動作をさせることができます。{{Glossary("tag", "タグ")}}で囲むと、単語や画像をどこかにハイパーリンクさせたり、単語を斜体にしたり、フォントを大きくしたり小さくしたりすることができます。 例えば、次のようなコンテンツがあるとします。

```plain
My cat is very grumpy
```

行を独立させたい場合は、段落タグで囲んで段落であることを指定することができます。

```html
<p>My cat is very grumpy</p>
```

### HTML 要素の中身

この段落要素についてもう少し詳しく見ていきましょう。

![開始タグ、 'my cat is very grumpy' と読めるコンテンツ、終了タグがある段落要素](grumpy-cat-small.png)

要素は主に以下のようなもので構成されています。

1. **開始タグ** (opening tag): これは、要素の名前（この場合は p）を**山括弧**で囲んだものです。どこから要素が始まっているのか、どこから効果が始まるのかを表します。 — 今回の場合どこから段落が始まるかを表しています。
2. **終了タグ** (closing tag): これは、要素名の前に**スラッシュ**が入っていることを除いて開始タグと同じです。どこで要素が終わるのかを表しています。 — この場合は、段落が終わる場所を表します。終了タグの書き忘れは、初心者のよくある間違いで、おかしな結果になることがあります。
3. **コンテンツ** (content): 要素の内容です。今回の場合はただのテキストです。
4. **要素** (element): 開始タグ、終了タグ、コンテンツで要素を構成します。

要素には属性 (attribute) を設定することができます。このような感じです。

![class 属性 class=editor-note が強調された段落の開始タグ](grumpy-cat-attribute-small.png)

属性には、実際のコンテンツには表示させたくない、要素に関する追加情報が含まれています。ここでは、 `class` が属性の**名前**で、 `editor-note` が属性の**値**です。 `class` 属性では、要素に一意ではない識別子を与えることができ、それを使って要素（および同じ `class` 値を持つ他の要素）にスタイル情報などのターゲットを設定することができます。
一部の属性、たとえば [`required`](/ja/docs/Web/HTML/Reference/Attributes/required) には値がありません。

値を設定する属性は常に次のような形式になります。

1. 要素名（すでにいくつか属性がある場合はひとつ前の属性）との間の空白
2. 属性名とそれに続く等号
3. 引用符で囲まれた属性の値

> [!NOTE]
> {{Glossary("ASCII")}} のホワイトスペース（または `"` `'` `` ` `` `=` `<` `>` のいずれかの文字）を含まない単純な属性値は引用符を省略することができますが、コードを一貫性のあるものにし、理解を容易にするため、すべての属性値を引用符で囲むことをお勧めします。

### 要素の入れ子

要素の中に他の要素を入れることもできます。これを**ネスト**（または入れ子）と言います。もしあなたの猫が**とっても**機嫌が悪いことを表したいとしたら、 "very" という単語を {{htmlelement("strong")}} 要素に入れて、単語の強調を表すことができます。

```html
<p>My cat is <strong>very</strong> grumpy.</p>
```

しかしながら要素は正しく入れ子にしなければなりません。上記の例では、まず始めに {{htmlelement("p")}} 要素が開始され、その次に {{htmlelement("strong")}} 要素が開始されています。その場合は、必ず {{htmlelement("strong")}} 要素、 {{htmlelement("p")}} 要素の順で終了しなければなりません。次の例は間違いです。

```html-nolint example-bad
<p>My cat is <strong>very grumpy.</p></strong>
```

要素は確実に他の要素の中もしくは外で開始し、終了する必要があります。上記の例のように要素が重複してしまうと、ウェブブラウザーは言おうとしていることを推測してもっとも良いと思われる解釈をするため、予期せぬ結果になることがあります。そうならないよう気を付けましょう！

### 空要素

コンテンツを持たない要素もあります。そのような要素を **{{glossary("void element", "空要素")}}** (void element) と呼びます。すでに HTML ページにある {{htmlelement("img")}} 要素を例に見ていきましょう。

```html
<img src="images/firefox-icon.png" alt="My test image" />
```

この要素は 2 つの属性を持っていますが、終了タグ `</img>` がありませんし、内部にコンテンツもありません。これは画像要素は、その機能を果たすためにコンテンツを囲むものではないからです。画像要素の目的は、画像を HTML ページの表示させたいところに埋め込むことです。

## 初めての HTML 文書の作成

以上で個々の HTML 要素の基本は終了ですが、要素単体ではあまり役に立ちません。 これで個々の要素を結合して HTML ページ全体を形成する方法を見てみましょう。 基本的な HTML ファイルを作成し、それがどのような要素で構成されているか見てみましょう。

1. 自分の `web-projects` フォルダー内に、 `first-website` という新しいフォルダーを作成します。
2. `first-website` の中で、 `index.html` という新しいファイルを作成し、次のコードを正確に表示させるように挿入します。

```html
<!doctype html>
<html lang="ja">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title>テストページ</title>
  </head>
  <body>
    <img src="" alt="テスト画像" />
  </body>
</html>
```

この中にあるものは以下の通りです。

- `<!doctype html>` — [文書型宣言](/ja/docs/Glossary/Doctype)です。これは必須の前置きです。昔々、 HTML がまだ出来たばかりの頃（1991 ～ 2 年）、文書型宣言は HTML ページが正しい HTML と見なされるために従わなければならない、一連のルールへのリンクとして機能することを意味していました。つまり、自動エラーチェックなどの有益なものを表すことができました。しかし、最近ではあまり機能しておらず、文書が正しく動作するために必要なだけです。今はこれだけ知っていれば大丈夫です。
- `<html></html>` — {{htmlelement("html")}} 要素です。この要素は、このページのすべてのコンテンツを囲み、ルート要素と呼ばれることもあります。ここでは文書の主要な言語を設定する `lang` 属性も指定します。
- `<head></head>` — {{htmlelement("head")}} 要素です。この要素は、ページの閲覧者に向けて表示するためのコンテンツではない、 HTML ページに含めたいものをすべて収めるための入れ物です。検索エンジン向けの {{Glossary("keyword", "キーワード")}} やページのディスクリプション（説明書き）、ページの見た目を変更するための CSS、文字コードの宣言などを含みます。
- `<meta charset="utf-8">` — この要素は、大部分の書き言葉の文字のほとんどを含む UTF-8 を文書で使用するように設定しています。基本的には、文書はどんなテキストコンテンツでも扱えるようになります。これを設定しない理由はありませんし、後でいくつかの問題を回避するのに役立ちます。
- `<meta name="viewport" content="width=device-width">` — この[ビューポート属性](/ja/docs/Web/CSS/CSSOM_view/Viewport_concepts#モバイルのビューポート)は、このページがある幅のビューポートで描画されることを保証し、モバイルブラウザーがビューポートより広い幅でページを描画した上で縮小して表示するのを防止します。
- `<title></title>` — {{htmlelement("title")}} 要素です。ページのタイトルを指定しています。このタイトルはページが読み込まれた時にブラウザーのタブに表示されます。また、ブックマークやお気に入りに登録した時の説明にも使われます。
- `<body></body>` — {{htmlelement("body")}} 要素です。これには、テキスト、画像、ビデオ、ゲーム、再生可能な音声トラックなど、ページを訪れたウェブの利用者に表示したいすべてのコンテンツが含まれます。

## 画像

もう一度 {{htmlelement("img")}} 要素について見ていくことにしましょう。

```html
<img src="" alt="テスト画像" />
```

前に説明したように、ページのこれが現れたところに画像を埋め込みます。画像ファイルのパスを値に持つ `src` (source) 属性を指定することによってその画像を表示できます。

また、 `alt` (alternative、代替) 属性も指定しています。 [`alt` 属性](/ja/docs/Web/HTML/Reference/Elements/img#意味のある代替説明を書く)は、以下のような理由で画像を見られない人に向けて説明するテキストを指定するものです。

1. 目が不自由な人。著しく目の不自由な人はよくスクリーンリーダーと呼ばれるツールを使っていて、それが画像の `alt` 属性の内容を読み上げます。
2. 何らかの理由で画像の表示に失敗した場合。例えば、 `src` 属性の中のパスをわざと正しくないものに変更してみてください。ページを保存したり再読み込みしたりすると、画像の場所に下記のようなものが表示されるでしょう。

![テスト画像という言葉](alt-text-example.png)

alt テキストのキーワードは「説明文」です。 alt テキストは、その画像が何を伝えているのかを読者が十分に理解できるような情報を提供する必要があります。この例では、現在のテキストである「テスト画像」は全く意味がありません。 Firefox のロゴであれば、「Firefox のロゴ: 地球の周りを燃えるような狐が囲んでいる。」の方がずっと良いでしょう。

> [!NOTE]
> アクセシビリティについての詳細は、[アクセシビリティ学習モジュール](/ja/docs/Learn_web_development/Core/Accessibility)をご覧ください。

画像を表示させてみましょう。

1. `first-website` フォルダー内に、 `images` という新しいフォルダーを作成し、前回選択した画像をこのフォルダー内に置きます。
2. `<img>` タグの `src` 属性値内に、画像へのパスを入力します。 `images` というフォルダー内にあり、 `index.html` ファイルと同じディレクトリー内にあります。したがって、パスは `images/` に画像の名前を付けたものになります。例えば、画像が `firefox-icon.png` という名前で呼ばれている場合、 `src` 属性は `src="images/firefox-icon.png"` のようになります。
3. `alt` 属性値の `テスト画像` を、画像をより適切に説明するテキストに置き換えてください。
4. ウェブブラウザー内で `index.html` ファイルを開いてください。画像が表示されるはずです。表示されない場合は、上記のコードと照らし合わせて `<img>` 要素を調べてください。引用符などの構文に抜けがないか確認してください。画像ファイル名が正しいことを確認してください。

> [!NOTE]
> 画像が実に大きく、画面に収まらない場合でも、心配しないでください。次の記事でこの課題は修正されます。
> アクセシビリティについての詳細は、[アクセシビリティ学習モジュール](/ja/docs/Learn_web_development/Core/Accessibility)と、さまざまな状況で画像に alt 属性を使用する方法を学ぶための [alt 決定ツリー](https://www.w3.org/WAI/tutorials/images/decision-tree/)をご覧ください。

## テキストのマークアップ

この節では、文字列をマークアップするために使用する基本的な HTML 要素をいくつか見ていきます。

### 見出し

見出し要素により、コンテンツの特定の部分を見出し、または小見出しとして指定することができます。本にメインタイトル、章立て、サブタイトルがあるように、 HTML 文書にも見出しがあります。 HTML には {{htmlelement("Heading_Elements", "&lt;h1&gt; - &lt;h6&gt;")}} の 6 段階の見出しがありますが、よく使うのはせいぜい 3 から 4 まででしょう。

```html
<!-- 4 段階の見出し -->
<h1>メインタイトル</h1>
<h2>最上位の見出し</h2>
<h3>小見出し</h3>
<h4>孫見出し</h4>
```

> [!NOTE]
> HTML の中で `<!--` と `-->` の間にあるものは、すべて **HTML コメント**です。ブラウザーは、コードを表示する際にコメントを無視します。つまり、コメントはページ上では表示されず、コードの中に表示されるだけです。 HTMLコメントは、コードやロジックに関する有用なメモを書き込むためのものです。

それでは、あなたの HTML の {{htmlelement("img")}} 要素の上に適切なタイトルを付けてみましょう。

> [!NOTE]
> 見出しレベル 1 には、暗黙のスタイルがあることがわかりますね。テキストを大きくしたり、太くしたりするために見出し要素を使用しないでください。見出し要素は[アクセシビリティ](/ja/docs/Learn_web_development/Core/Accessibility/HTML#%e3%83%86%e3%82%ad%e3%82%b9%e3%83%88%e3%82%b3%e3%83%b3%e3%83%86%e3%83%b3%e3%83%84)や [SEO などの理由](/ja/docs/Learn_web_development/Core/Structuring_content/Headings_and_paragraphs#%e3%81%aa%e3%81%9c%e6%a7%8b%e9%80%a0%e3%81%8c%e5%bf%85%e8%a6%81%e3%81%aa%e3%81%ae%e3%81%8b)で使用されているからです。段階を飛ばすことなく、意味のある見出しの並びをページ上に作るようにしてください。

### 段落

先に説明したように、 {{htmlelement("p")}} 要素は段落を示しています。通常の文章を書くときにはこの要素を頻繁に使うことになるでしょう。

```html
<p>これは単一の段落です</p>
```

前の記事のサンプルテキストを 1 つまたは複数の段落に入れ、 {{htmlelement("img")}} 要素のすぐ下に配置してください。保存したら、ページをブラウザーで見てみてください。

### リスト

ウェブのコンテンツの多くはリストであり、 HTML にはリストのための特別な要素があります。リストのマークアップは、常に 2 つ以上の要素で構成されています。最も一般的なリストの種類は、順序付きリストと順序なしリストです。

1. **順序なしリスト**は、お買い物リストのようにアイテムの順番が特に関係ない時に使います。順序なしリストは {{htmlelement("ul")}} 要素で囲みます。
2. **順序付きリスト**は料理のレシピのようにアイテムの順番が関係ある時に使います。順序付きリストは {{htmlelement("ol")}} 要素で囲みます。

リストの中に入るそれぞれのアイテムは {{htmlelement("li")}} (list item) 要素の中に書きます。

例えば、次の段落の一部をリストにしたい場合、

```html
<p>
  At Mozilla, we're a global community of technologists, thinkers, and builders
  working together…
</p>
```

以下のようにマークアップします。

```html
<p>At Mozilla, we're a global community of</p>

<ul>
  <li>technologists</li>
  <li>thinkers</li>
  <li>builders</li>
</ul>

<p>working together…</p>
```

ページに番号付きリストと番号なしリストを追加してみましょう。

## リンク

リンクはとても重要です。これがウェブをウェブたらしめているものです。リンクを追加するには、 {{htmlelement("a")}} 要素を使う必要があります。 "a" は "anchor" を省略したものです。段落中の文字をリンクにするには次の手順で行います。

1. リンクにしたい文字を選びます。今回は "Mozilla Manifesto" を選びました。
2. 選んだ文字を {{htmlelement("a")}} 要素で囲みます。

   ```html
   <a>Mozilla Manifesto</a>
   ```

3. このように {{htmlelement("a")}} 要素に `href` 属性を追加します。

   ```html
   <a href="">Mozilla Manifesto</a>
   ```

4. この属性の値には、リンク先のウェブアドレスを記入します。

   ```html
   <a href="https://www.mozilla.org/en-US/about/manifesto/">
     Mozilla Manifesto
   </a>
   ```

アドレスの先頭にある `https://` や `http://` の部分（*プロトコル*と言います）を書き忘れると、予期せぬ結果となってしまうかもしれません。リンクを作ったら、ちゃんとそれが遷移したいところに行ってくれるかを確かめましょう。

> [!NOTE]
> `href` は属性名として変に思うかもしれません。覚えにくかったら、 `href` は _**h**ypertext **ref**erence_ を表しているということを覚えておきましょう。

もしまだやってないのなら、ページにリンクを追加してみましょう。

## まとめ

ここまでの説明に沿ってやってきたのなら、以下のようなページができあがっているはずです（[ここ](https://mdn.github.io/beginner-html-site/)でも見られます）。

![ウェブページのスクリーンショットで、 Firefox のロゴ、「Mozilla is cool」という見出し、そして 2 段落のテキストが表示されています。](finished-test-page-small.png)

もし途中で行き詰まってしまったなら、 GitHub にある[完成版のコード例](https://github.com/mdn/beginner-html-site/blob/main/index.html)と見比べてみてください。

この記事では HTML の表面的な部分だけを勉強しました。もっと知りたい場合は [HTML を学ぶ](/ja/docs/Learn_web_development/Core/Structuring_content)を読んでみてくだい。

{{PreviousMenuNext("Learn_web_development/Getting_started/Your_first_website/What_will_your_website_look_like", "Learn_web_development/Getting_started/Your_first_website/Styling_the_content", "Learn_web_development/Getting_started/Your_first_website")}}
