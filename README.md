# viper_beginner

必要な開発環境

- Python 3.6.2 以上
- geth
- populus
- web3(python)
- solidity
- viper

# 開発環境の構築

## Ethereumクライアントをインストールする

- Geth

Ethereumの`P2P`ネットワークに参加するには、クライアントソフトウェアが必要。
各言語によっていくつかのクライアントソフトウェアある。

- cpp-ethereum (c++)
- pyethereum (python)
- Geth (Go)

Gethが現在推奨されている。

```Bash
$ brew tap ethereum/ethereum
$ brew install ethereum

$ geth version
Geth
Version: 1.10.15-stable
Architecture: amd64
Go Version: go1.17.5
Operating System: darwin
GOPATH=
GOROOT=go
```

## Solidityをインストールする

`Ethereum`では、スマートコントラクトのコードは`EVM Code(Ethereum Virtual Machine Code )`と呼ばれるバイトコード形式で記述・実行される。

EVM Codeに変換するためのスマートコントラクト記述に特化したプログラミング言語はいくつかあり、その一つである`Solidity`はJavascriptライクな構文を持つ静的片付け言語です。

```Bash
$ brew install solidity

$ solc --version
solc, the solidity compiler commandline interface
Version: 0.8.11+commit.d7f03943.Darwin.appleclang
```

`HelloWorld.sol`

以下は Solidity でのサンプルコードです。
contract 句で宣言されるコントラクトが基本の構成要素です。コントラクトは Java などのオブジェクト指向言語におけるクラスに似ています。そして、function に続くのが関数定義です。
このコードでは get 関数が呼ばれると "Hello World" という文字列を返します。

`function`が関数定義になる。
このコードでは`get`関数が呼ばれると`Hello World`という文字列を返す。

```
pragma solidity ^0.8.11;

contract HelloWorld {
    function get() internal pure returns (string retVal) {
        return "Hello World";
   }
}
```

関数定義にて Visibility (可視性)の設定が以下の4つからできる。

- external
- public
- internal
- private

もし指定がなければ `Warning: No visibility specified. Defaulting to "public". `という警告が出る。

`pure`は純粋関数の意味で、**状態の読み込みと変更がない**ことを示す。

純粋関数にもかかわらず pure の記述がないと`Warning: Function state mutability can be restricted to pure`という警告が出る。

詳細については以下の公式ドキュメントを参照。

- http://solidity.readthedocs.io/en/latest/solidity-in-depth.html

```Bash
# サンプルコードを HelloWorld.sol として保存し、下記のコマンドを実行するとコンパイルできます。
# Binary: に続く文字列が、コンパイルされたバイトコードである EVM Code です。

$ solc --bin hello_world.sol

======= hello_world.sol:HelloWorld =======
Binary:

```

# 参考資料

- https://qiita.com/naoki_maeda/items/25fd28777d04e144aea4
- https://qiita.com/kyrieleison/items/d6684d55fc73f482d2ce
- https://gihyo.jp/dev/serial/01/bbc1
- https://www.oreilly.co.jp/books/9784873118963/
- https://lastrust.io/2020/06/05/whatis-did-web3/
