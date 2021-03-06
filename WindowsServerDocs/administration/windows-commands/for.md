---
title: 対象
description: ファイルのセット内で、各ファイルに対して指定されたコマンドを実行する for コマンドのリファレンストピックです。
ms.prod: windows-server
ms.technology: manage-windows-commands
ms.topic: article
ms.assetid: e275726c-035f-4a74-8062-013c37f5ded1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 24ef5bc159e67862d419bd2728b14585f8b095d4
ms.sourcegitcommit: bf887504703337f8ad685d778124f65fe8c3dc13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/16/2020
ms.locfileid: "83437017"
---
# <a name="for"></a>対象

ファイルのセット内で、各ファイルに対して指定されたコマンドを実行します。

## <a name="syntax"></a>構文

```
for {%% | %}<variable> in (<set>) do <command> [<commandlineoptions>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `{%% | %}<variable>` | 必須です。 置き換え可能なパラメーターを表します。 `%`コマンドプロンプトで**for**コマンドを実行するには、1つのパーセント記号 () を使用します。 `%%`バッチファイル内で**for**コマンドを実行するには、2つのパーセント記号 () を使用します。 変数は大文字と小文字が区別され、 **% a**、 **% b**、 **% c**などのアルファベット順の値で表す必要があります。 |
| (`<set>`) | 必須。 1つ以上のファイル、ディレクトリ、またはテキスト文字列、またはコマンドを実行する値の範囲を指定します。 かっこが必要です。 |
| `<command>` | 必須。 各ファイル、ディレクトリ、またはテキスト文字列、または*set*に含まれる値の範囲に対して実行するコマンドを指定します。 |
| `<commandlineoptions>` | 指定したコマンドで使用するコマンドラインオプションを指定します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>解説

- このコマンドは、バッチファイル内で使用することも、コマンドプロンプトから直接使用することもできます。

- **For**コマンドには、次の属性が適用されます。

  - このコマンドは、指定された `% variable` `%% variable` コマンドがすべてのファイルを処理するまで、指定されたセット内の各テキスト文字列にまたはを置き換えます。

  - 変数名は大文字と小文字が区別され、グローバルであり、一度にアクティブにできるのは52以上です。

  - を通じてバッチパラメーターとの混同を避けるために `%0` `%9` 、 **0** ~ **9**の数字以外の*変数*には任意の文字を使用できます。 単純なバッチファイルの場合、などの1文字 `%%f` が機能します。

  - 複雑なバッチファイルで*変数*に複数の値を使用して、異なる置き換え可能な変数を区別できます。

- *Set*パラメーターは、1つのファイルグループまたは複数のファイルグループを表すことができます。 ワイルドカード文字 (**&#42;** と **?**) を使用して、ファイルセットを指定できます。 有効なファイルセットを次に示します。

  ```
  (*.doc)
  (*.doc *.txt *.me)
  (jan*.doc jan*.rpt feb*.doc feb*.rpt)
  (ar??1991.* ap??1991.*)
  ```

- このコマンドを使用すると、*セット*内の最初の値が `% variable` またはに置き換えら `%% variable` れ、指定したコマンドによってこの値が処理されます。 この処理は、*設定*値に対応するすべてのファイル (またはファイルのグループ) が処理されるまで続行されます。

- と**は****パラメーターでは**ありませんが、このコマンドで使用する必要があります。 これらのいずれかのキーワードを省略すると、エラーメッセージが表示されます。

- コマンド拡張機能が有効になっている場合 (既定)、の次の**追加の形式**のがサポートされています。

  - **ディレクトリのみ:***Set*にワイルドカード文字 (**&#42;** または **?**) が含まれている場合、指定された*コマンド*は、 *set*に一致するディレクトリ (指定されたディレクトリ内のファイルのセットではなく) ごとに実行されます。 の構文は次のとおりです。

    ```
    for /d {%%|%}<Variable> in (<Set>) do <Command> [<CommandLineOptions>]
    ```

  - **再帰:***ドライブ*:*パス*をルートとするディレクトリツリーをウォークし、ツリーの各ディレクトリで**for**ステートメントを実行します。 **/R**の後にディレクトリが指定されていない場合は、現在のディレクトリがルートディレクトリとして使用されます。 *Set*が単なるピリオド (.) の場合は、ディレクトリツリーを列挙するだけです。 の構文は次のとおりです。

    ```
    for /r [[<drive>:]<path>] {%%|%}<variable> in (<set>) do <command> [<commandlinepptions>]
    ```

  - **値の範囲の反復処理:** 反復変数を使用して開始値 (*start*#) を設定し、値が設定された終了値 (*終了*#) を超えるまで値のセット範囲をステップ実行します。 **/l**は、 *start*# と*end*# を比較することによって反復を実行します。 *Start*# が*end*より小さい場合は、コマンドが実行されます。 反復変数が*終了*# を超えると、コマンドシェルはループを終了します。 負の*手順*# を使用して、値を小さくする範囲をステップ実行することもできます。 たとえば、(1, 1, 5) はシーケンス 1 2 3 4 5 を生成し、(5,-1, 1) はシーケンス 5 4 3 2 1 を生成します。 の構文は次のとおりです。

    ```
    for /l {%%|%}<variable> in (<start#>,<step#>,<end#>) do <command> [<commandlinepptions>]
    ```

  - **反復処理とファイル解析:** ファイルの解析を使用して、コマンドの出力、文字列、およびファイルの内容を処理します。 反復変数を使用して、調査するコンテンツまたは文字列を定義し、さまざまな*parsingkeywords*オプションを使用して解析をさらに変更します。  *Parsingkeywords*トークンオプションを使用して、反復変数として渡すトークンを指定します。 トークンオプションを指定せずに使用した場合、 **/f**では最初のトークンのみが確認されることに注意してください。

    ファイルの解析では、出力、文字列、またはファイルの内容を読み取り、個々のテキスト行に分割し、各行を0個以上のトークンに解析します。 次に、トークンに設定された反復変数値を使用して、 **for**ループが呼び出されます。 既定では、 **/f**は、各ファイルの各行から空白で区切られた最初のトークンを渡します。 空白行はスキップされます。

    構文は次のとおりです。

    ```
    for /f [<parsingkeywords>] {%%|%}<variable> in (<set>) do <command> [<commandlinepptions>]
    for /f [<parsingkeywords>] {%%|%}<variable> in (<literalstring>) do <command> [<commandlinepptions>]
    for /f [<parsingkeywords>] {%%|%}<variable> in ('<command>') do <command> [<commandlinepptions>]
    ```

    *Set*引数は、1つ以上のファイル名を指定します。 各ファイルは、*セット*内の次のファイルに移動する前に、開かれ、読み取られ、処理されます。 既定の解析動作をオーバーライドするには、 *parsingkeywords*を指定します。 これは、別の解析オプションを指定するための1つ以上のキーワードを含む、引用符で囲まれた文字列です。

    **Usebackq**オプションを使用する場合は、次のいずれかの構文を使用します。

    ```
    for /f [usebackq <parsingkeywords>] {%%|%}<variable> in (<Set>) do <command> [<commandlinepptions>]
    for /f [usebackq <parsingkeywords>] {%%|%}<variable> in ('<LiteralString>') do <command> [<commandlinepptions>]
    for /f [usebackq <parsingkeywords>] {%%|%}<variable> in (`<command>`) do <command> [<commandlinepptions>]
    ```

    次の表は、 *parsingkeywords*に使用できる解析キーワードの一覧です。

    | Keyword | 説明 |
    | ------- | ----------- |
    | eol =`<c>` | 行末の文字 (1 文字のみ) を指定します。 |
    | スキップ =`<n>` | ファイルの先頭でスキップする行数を指定します。 |
    | delims =`<xxx>` | 区切り記号セットを指定します。 これにより、スペースとタブの既定の区切り記号セットが置き換えられます。 |
    | トークン =`<x,y,m–n>` | 各反復処理の**for**ループに各行のトークンを渡すかどうかを指定します。 その結果、追加の変数名が割り当てられます。 *m-n*は、 *m*番目から*n*番目のトークンまでの範囲を指定します。 **Tokens =** 文字列の最後の文字がアスタリスク (**&#42;**) の場合は、追加の変数が割り当てられ、最後に解析されたトークンの後の行に残りのテキストが渡されます。 |
    | usebackq | バッククォートされた文字列をコマンドとして実行するか、単一引用符で囲まれた文字列をリテラル文字列として使用するか、またはスペースを含む長いファイル名に対して、それぞれのファイル名を `<set>` 二重引用符で囲むように指定します。 |

  - **変数の代入:** 次の表に、省略可能な構文 (任意の変数**I**) を示します。

    | 修飾子を持つ変数 | Description |
    | ---------------------- | ----------- |
    |` %~I` | `%I`を展開して、周囲の引用符を削除します。 |
    | `%~fI `| `%I`は、完全修飾パス名に展開されます。 |
    | `%~dI `| `%I`はドライブ文字のみに拡張されます。 |
    | `%~pI` | `%I`はパスのみに展開されます。 |
    | `%~nI `| `%I`ファイル名のみに展開されます。 |
    | `%~xI` | `%I`は、ファイル名拡張子のみに展開されます。 |
    | `%~sI` | 短い名前のみを含むようにパスを展開します。 |
    | `%~aI` | `%I`ファイルのファイル属性に展開されます。 |
    | `%~tI` | `%I`は、ファイルの日付と時刻に展開されます。 |
    | `%~zI` | `%I`は、ファイルのサイズに拡張されます。 |
    | `%~$PATH:I` | PATH 環境変数に一覧表示されているディレクトリを検索し、 `%I` 見つかった最初のディレクトリの完全修飾名に展開します。 環境変数名が定義されていない場合、またはファイルが検索で見つからない場合、この修飾子は空の文字列に展開されます。 |

    次の表に、複合結果を取得するために使用できる修飾子の組み合わせを示します。

    | 結合された修飾子を持つ変数 | Description |
    | -------------------------------- | ----------- |
    | `%~dpI `| `%I`は、ドライブ文字とパスのみに展開されます。 |
    | `%~nxI` | `%I`ファイル名と拡張子のみを展開します。 |
    | `%~fsI` | `%I`は、短い名前のみで完全なパス名に展開されます。 |
    | `%~dp$PATH:I` | の PATH 環境変数に示されているディレクトリを検索 `%I` し、最初に見つかったドライブ文字とパスに展開します。 |
    | `%~ftzaI` | `%I`は、 **dir**のような出力行に展開されます。 |

    上の例では、 `%I` と PATH を他の有効な値に置き換えることができます。 **変数名が有効な場合**は、構文が終了し **%~** ます。

    などの大文字の変数名を使用 `%I` すると、コードを読みやすくし、大文字と小文字が区別されない修飾子との混同を避けることができます。

- **文字列の解析:**`for /f` `<literalstring>` 二重引用符 (usebackq*を使用*し*ない*) または単一引用符 (usebackq) (たとえば、(MyString) または (' MyString ')) でラップすることにより、即時文字列で解析ロジックを使用できます。 `<literalstring>`は、ファイルからの1行の入力として扱われます。 二重引用符で解析する場合、 `<literalstring>` コマンドシンボル (など `\ & | > < ^` ) は通常の文字として扱われます。

- **出力の解析:** コマンドを使用すると、 `for /f` かっこの間に逆引用符を付けることによって、コマンドの出力を解析でき `<command>` ます。 これはコマンドラインとして扱われ、Cmd.exe に渡されます。 出力はメモリにキャプチャされ、ファイルであるかのように解析されます。

## <a name="examples"></a>例

**を**バッチファイルで使用するには、次の構文を使用します。

```
for {%%|%}<variable> in (<set>) do <command> [<commandlineoptions>]
```

置き換え可能な変数 **% f**を使用して、拡張子が .doc または .txt の現在のディレクトリにあるすべてのファイルの内容を表示するには、次のように入力します。

```
for %f in (*.doc *.txt) do type %f
```

前の例では、現在のディレクトリにある .doc または .txt 拡張子を持つ各ファイルは、すべてのファイルの内容が表示されるまで、 **% f**変数の代わりに使用されます。 このコマンドをバッチファイルで使用するには、 **% f**のすべての出現箇所を **%% f**で置き換えます。 それ以外の場合、変数は無視され、エラーメッセージが表示されます。

ファイルを解析するために、コメント行を無視するには、次のように入力します。

```
for /f eol=; tokens=2,3* delims=, %i in (myfile.txt) do @echo %i %j %k
```

このコマンドは、 *myfile.txt*の各行を解析します。 セミコロンで始まる行を無視し、各行の2番目と3番目のトークンを**for** body に渡します (トークンはコンマまたはスペースで区切られます)。 For ステートメントの本文では、 **% i**を参照して2番目のトークンを取得し、 **% j**を**使用**して3番目のトークンを取得し、 **% k**を参照して残りのすべてのトークンを取得します。 指定したファイル名にスペースが含まれている場合は、テキストを引用符で囲みます (ファイル名など)。 引用符を使用するには、 **usebackq**を使用する必要があります。 それ以外の場合、引用符は、解析するリテラル文字列の定義として解釈されます。

**% i**は**for**ステートメントで明示的に宣言されています。 **% j**と **% k**は、**トークン =** を使用して暗黙的に宣言されています。 **トークン =** を使用すると、文字 z または z を超える変数を宣言しようとしていない場合に、最大26個のトークンを指定できます。

かっこの間に*set*を配置することで、コマンドの出力を解析するには、次のように入力します。

```
for /f usebackq delims== %i in ('set') do @echo %i
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
