

# What's this?

WebApps(on Windows)のデプロイ様テンプレート

* サービスプランはStandardサービスプラン
* インスタンスタイプは S1(1GB CPU, 1.75GB MEM, 50GB Storage)
* アラート設定は以下の通り
    * HTTP 401 エラー
    * HTTP 404 エラー
    * 内部 エラー(5xx, 6xx)
    * 平均メモリ使用量　（閾値80%）
    * 平均応答時間

# How to Deploy

* Parameters.jsonを適宜更新
* 事前にサブスクリプションを設定すること

```
# Azure ログイン
az login

To sign in, use a web browser to open the page https://aka.ms/devicelogin and enter the code xxxxx to authenticate.

https://aka.ms/devicelogin へアクセスし、xxxxxを入力し、認証する。

# Azure サブスクリプション　確認
az account list --output table

#  Azure サブスクリプション アクティベート（切替）
az account set --subscription "<SubscrioptionName>"

# Azure リソース　確認
az resource list --output table
```


* コマンド叩く
Azure CLI

```
az group deployment create --resource-group <resourceGroupName> --template-file template.json --parameters parameters.json

```

* FYI  
[初めての Azure Resource Manager テンプレートを作成およびデプロイする](https://docs.microsoft.com/ja-jp/azure/azure-resource-manager/resource-manager-create-first-template)  
[Azure Resource Manager テンプレートの構造と構文の詳細](https://docs.microsoft.com/ja-jp/azure/azure-resource-manager/resource-group-authoring-templates)  
[az group deployment](https://docs.microsoft.com/en-us/cli/azure/group/deployment?view=azure-cli-latest#az_group_deployment_create)