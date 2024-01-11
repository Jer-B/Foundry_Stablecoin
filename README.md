<!-- @format -->
# English README　[Jump to Japanese Version](#japanese)

# Preview
For an easy interaction with the contract use abi.ninja website.
Here is a link to the contract loaded on it: [Foundry Stablecoin contract]()

Click on function on the left to add them in the center of the page and interact with them.
- Functions under the 'READ' category are for getting actual values.
- Functions under the 'Write' category are for inserting new data.

- NOTE: The above contract is deployed on the Sepolia Testnet, so testnet funds are required for interacting with it.


# Foundry DeFi Stablecoin


Contract is deployed at 0xxxx
[View on Sepolia]()


1. This project is meant to be a stablecoin where users can deposit WETH and WBTC in exchange for a token that will be pegged to the USD.

I used the 32 hours long video from Cyfrin Foundry Blockchain course to learn about Foundry.  
[Cyfrin Foundry](https://github.com/Cyfrin/foundry-full-course-f23)



## Requirements

- [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
  - You'll know you did it right if you can run `git --version` and you see a response like `git version x.x.x`
- [foundry](https://getfoundry.sh/)
  - You'll know you did it right if you can run `forge --version` and you see a response like `forge 0.2.0 (816e00b 2023-03-16T00:05:26.396218Z)`

## Quickstart

```
git clone https://github.com/Jer-B/Foundry_Stablecoin
cd Foundry_Stablecoin
forge build
```

# Updates
- The latest version of openzeppelin-contracts has changes in the ERC20Mock file. To follow along with the course, you need to install version 4.8.3 which can be done by ```forge install openzeppelin/openzeppelin-contracts@v4.8.3 --no-commit``` instead of ```forge install openzeppelin/openzeppelin-contracts --no-commit```

# Usage

## Start a local node

```
make anvil
```

## Deploy

This will default to your local node. You need to have it running in another terminal in order for it to deploy.

```
make deploy
```


## Testing

1. Unit
2. Integration
3. Forked
4. Staging

In this repo we cover #1 and Fuzzing. 

```
forge test
```

### Test Coverage

```
forge coverage
```

and for coverage based testing: 

```
forge coverage --report debug
```

# Deployment to a testnet or mainnet

1. Setup environment variables

You'll want to set your `alchemy_RPC_sepolia` and `PRIVATE_KEY_TESTNET` as environment variables. You can add them to a `.env` file, similar to what you see in `.env.example`.

- `PRIVATE_KEY_TESTNET`: The private key of your account (like from [metamask](https://metamask.io/)). **NOTE:** FOR DEVELOPMENT, PLEASE USE A KEY THAT DOESN'T HAVE ANY REAL FUNDS ASSOCIATED WITH IT.
  - You can [learn how to export it here](https://metamask.zendesk.com/hc/en-us/articles/360015289632-How-to-Export-an-Account-Private-Key).
- `alchemy_RPC_sepolia`: This is url of the sepolia testnet node you're working with. You can get setup with one for free from [Alchemy](https://alchemy.com/?a=673c802981)

Optionally, add your `ETHERSCAN_API_KEY` if you want to verify your contract on [Etherscan](https://etherscan.io/).

1. Get testnet ETH

Head over to [faucets.chain.link](https://faucets.chain.link/) and get some testnet ETH. You should see the ETH show up in your metamask.


2. Deploy

```
make deploy ARGS="--network sepolia"
```

## Scripts

Instead of scripts, we can directly use the `cast` command to interact with the contract. 

For example, on Sepolia:

1. Get some WETH 

```
cast send 0xdd13E55209Fd76AfE204dBda4007C227904f0a81 "deposit()" --value 0.1ether --rpc-url $alchemy_RPC_sepolia --private-key $PRIVATE_KEY_TESTNET
```

2. Approve the WETH

```
cast send 0xdd13E55209Fd76AfE204dBda4007C227904f0a81 "approve(address,uint256)" 0x091EA0838eBD5b7ddA2F2A641B068d6D59639b98 1000000000000000000 --rpc-url $alchemy_RPC_sepolia --private-key $PRIVATE_KEY_TESTNET
```

3. Deposit and Mint DSC

```
cast send 0x091EA0838eBD5b7ddA2F2A641B068d6D59639b98 "depositCollateralAndMintDsc(address,uint256,uint256)" 0xdd13E55209Fd76AfE204dBda4007C227904f0a81 100000000000000000 10000000000000000 --rpc-url $alchemy_RPC_sepolia --private-key $PRIVATE_KEY_TESTNET
```


## Estimate gas

You can estimate how much gas things cost by running:

```
forge snapshot
```

And you'll see an output file called `.gas-snapshot`


# Formatting


To run code formatting:
```
forge fmt
```





<a name="japanese"></a>
# 日本語版のREADME

# プレビュー
コントラクトとの簡単な対話には abi.ninja ウェブサイトを使用してください。
以下は、それにロードされたコントラクトへのリンクです:  [Foundry Stablecoin contract]()

左側の関数をクリックして、それらをページの中央に追加し、それらと対話します。
- `READ`カテゴリーの下にある関数は実際の値を取得するためのものです。
- `Write`カテゴリーの下にある関数は新しいデータを挿入するためのものです。

- 注意: 上記のコントラクトは Sepolia テストネット上にデプロイされており、それと対話するにはテストネット用の資金が必要です。


# Foundry DeFi Stablecoin


このコントラクトは、0xxxx にデプロイされています。
[View on Sepolia]()


1. このプロジェクトは、ユーザーがWETHとWBTCを預け入れ、USDにペッグされたトークンと交換することができるステーブルコインを目指しています。

Foundryを学ぶために、Cyfrin Foundry Blockchainコースの32時間の長いビデオを使用しました。
[Cyfrin Foundry](https://github.com/Cyfrin/foundry-full-course-f23)


## 必要条件

- [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)
  - git --version を実行して git version x.x.x のような応答が表示されれば成功です。
- [foundry](https://getfoundry.sh/)
  - forge --version を実行して forge 0.2.0 (816e00b 2023-03-16T00:05:26.396218Z) のような応答が表示されれば成功です

## Quickstart

```
git clone https://github.com/Jer-B/Foundry_Stablecoin
cd Foundry_Stablecoin
forge build
```

# パッケージのインストール
- openzeppelin-contractsの最新バージョンではERC20Mockファイルに変更がありました。バージョン4.8.3をインストールするには、次の手順を実行してください：  ```forge install openzeppelin/openzeppelin-contracts --no-commit```　の代わりにこのコマンドを使って⇨```forge install openzeppelin/openzeppelin-contracts@v4.8.3 --no-commit``` 


## ローカルノード(ブロックチェーン)を起動する

```
make anvil
```

## 使用方法

デプロイメント:

```
make deploy
```

## テスト方法

1. ユニットテスト
2. 統合テスト
3. フォークテスト
4. ステージングテスト

このリポジトリではテスト番号1とファズテストをカバーしています。

```
forge test
```

### Test Coverage

```
forge coverage
```

カバレッジベースのテストのコマンド：

```
forge coverage --report debug
```

# テストネットまたはメインネットへのデプロイ

1. 環境変数の設定

`alchemy_RPC_sepolia` と `PRIVATE_KEY_TESTNET` を環境変数として設定する必要があります。これらを .env ファイルに追加することができます。.env.example に示されているようなものです。


- `PRIVATE_KEY_TESTNET`: アカウントのプライベートキー[metamask](https://metamask.io/)). **注意**: 開発のために、実際の資金が関連付けられていないキーを使用してください。

  - [ここでキーのエクスポート方法を学ぶことができます](https://metamask.zendesk.com/hc/en-us/articles/360015289632-How-to-Export-an-Account-Private-Key).
- `alchemy_RPC_sepolia`: これはあなたが作業している Sepolia テストネットノードのURLです。 [Alchemy](https://alchemy.com/?a=673c802981)　から無料でセットアップできます。

オプションで、 [Etherscan](https://etherscan.io/)　で契約を検証したい場合は ETHERSCAN_API_KEY を追加してください。

1. テストネットETHを取得

 [faucets.chain.link](https://faucets.chain.link/) にアクセスし、テストネットETHを取得してください。MetamaskでETHが表示されるはずです。


2. デプロイ

```
make deploy ARGS="--network sepolia"
```

## Scripts

テストネットまたはローカルネットワークにデプロイした後、スクリプトを実行できます。

ローカルにデプロイされたcastを使用する例：

1. WETHを取得する

```
cast send 0xdd13E55209Fd76AfE204dBda4007C227904f0a81 "deposit()" --value 0.1ether --rpc-url $alchemy_RPC_sepolia --private-key $PRIVATE_KEY_TESTNET
```

2. WETHを承認する

```
cast send 0xdd13E55209Fd76AfE204dBda4007C227904f0a81 "approve(address,uint256)" 0x091EA0838eBD5b7ddA2F2A641B068d6D59639b98 1000000000000000000 --rpc-url $alchemy_RPC_sepolia --private-key $PRIVATE_KEY_TESTNET
```

3. WETHを預け入れてDSCをミントする

```
cast send 0x091EA0838eBD5b7ddA2F2A641B068d6D59639b98 "depositCollateralAndMintDsc(address,uint256,uint256)" 0xdd13E55209Fd76AfE204dBda4007C227904f0a81 100000000000000000 10000000000000000 --rpc-url $alchemy_RPC_sepolia --private-key $PRIVATE_KEY_TESTNET
```


## ガス代確認


```
forge snapshot
```

`.gas-snapshot` という名前の出力ファイルが表示されます


# フォーマット


コードのフォーマットを実行するには：
```
forge fmt
```
