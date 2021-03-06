# 構成管理
## 要件

## 設定変更の履歴
Config でリソース間の関係と設定の履歴を記録する。  
設定変更に起因するトラブルの原因調査に活用する。  

## 設定コンプライアンス
Config ルールを使用して AWS リソースが設計通りの状態になっていることを確認する。  
ルールには、AWS が用意しているマネージドルールと独自で作成するカスタムルールがある。  
まずはマネージドルールを使用してコンプライアンス確認をし、不足する場合はカスタムルールを作成する。  

マネージドルールの詳細は AWS ドキュメントに記載がある。  
[AWS Config マネージドルール](https://docs.aws.amazon.com/ja_jp/config/latest/developerguide/evaluate-config_use-managed-rules.html)

## サーバーインベントリの収集
Systems Manager を活用してインベントリを収集する。  

インベントリを収集するには EC2 インスタンスに対して以下の設定が必要。  

* SSM Agentをインストール
* 必要な権限が付与されたIAM Roleをアタッチ

収集する情報は以下の通り。  

|タイプ|説明|
|---|---|
|アプリケーション|アプリケーション名、発行元、バージョンなど。|
|AWS コンポーネント|EC2 ドライバ、エージェント、バージョンなど。|
|ネットワーク設定の詳細|IP アドレス、MAC アドレス、DNS、ゲートウェイ、サブネットマスクなど。|
|Windows 更新|Hotfix ID、インストール者、インストール日など。|
|インスタンスの詳細|システム名、オペレーティングシステム (OS) 名、OS バージョン、最終起動、DNS、ドメイン、ワークグループ、OS アーキテクチャなど。|
|サービス|名前、表示名、ステータス、依存サービス、サービスのタイプ、起動タイプなど。|
|Windows ロール|名前、表示名、パス、機能タイプ、インストール日など。|


## 構成ドキュメントの自動化
AWS リソースのパラメーターはプログラムにより取得しマークダウン形式で出力・保管する。  
このプログラムは手動/自動実行とし、結果は S3/ローカルディスクに保管する。



