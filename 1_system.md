@startuml "ゼンコネクト - Phase1"
!include https://raw.githubusercontent.com/plantuml-stdlib/C4-PlantUML/master/C4_Context.puml

' 境界づけられたコンテキストの定義
System_Boundary(zen-connect-api, "ゼンコネクト API") {
    System(register, "新規登録", "新規登録する")
    System(auth, "ログイン・ログアウト", "ログインする/ログアウトする")
    System(profile, "プロフィール情報", "プロフィール情報を更新する")
    System(experience, "体験記録","瞑想の体験を記録として残す")
}

System_Boundary(zen-connect-worker, "ゼンコネクト ワーカー") {
    System(readModelUpdater, "Read Model Updater", "イベント駆動で読み取りモデルを更新")
}

System_Ext(authServer, "外部認証サービス", "外部の認証基盤を利用する場合")
System_Ext(zennConnectReadDatabase, "ZenConnect Read DB", "読み取り専用のデータベース")
System_Ext(zennConnectWriteDatabase, "ZenConnect Write DB", "書き込み専用のデータベース")


' 外部アクター
Person(user, "ユーザー", "坐禅や瞑想を楽しみたいユーザー")

' 関係性の定義
Rel(user, register, "アカウントを作成する")
Rel(user, auth, "ログイン・ログアウトする")
Rel(user, profile, "プロフィールを変更する")
Rel(user, experience, "体験を記録する")

' 内部コンテキスト間の関係性
Rel(register, authServer, "認証情報を登録", "できれば認証基盤は外部サービスを利用")
Rel(auth, authServer, "認証情報を確認", "ログイン・ログアウト")

Rel(profile, authServer, "プロフィール情報を更新", "認証情報の更新")
Rel(register, zennConnectWriteDatabase, "新規登録情報を保存", "書き込み")

Rel(profile, zennConnectReadDatabase, "プロフィール情報を取得", "読み取り")
Rel(profile, zennConnectWriteDatabase, "プロフィール情報を更新", "書き込み")

Rel(experience, zennConnectReadDatabase, "体験記録を取得", "読み取り")
Rel(experience, zennConnectWriteDatabase, "体験記録を保存", "書き込み")

Rel(zennConnectWriteDatabase, readModelUpdater, "イベントを発行", "書き込み")
Rel(readModelUpdater, zennConnectReadDatabase, "読み取りモデルを更新", "イベント駆動で更新")

@enduml