@startuml "zenconnect - ユースケース図"
left to right direction
skinparam packageStyle rectangle

actor "ログイン済み利用者" as User
actor "ゲスト" as Guest

rectangle "ゼンコネクト" {
    package "プロフィール" {
        usecase "アカウントを登録する" as UC1
        usecase "プロフィールを編集する" as UC2
        usecase "プロフィールを閲覧する" as UC6
    }
    package "認証" {
        usecase "ログインする" as UC3
        usecase "ログアウトする" as UC4
        usecase "パスワードをリセットする" as UC5
    }
    package "体験記録" {
        usecase "体験を記録する" as UC7
        usecase "体験を編集する" as UC8
        usecase "体験を閲覧する" as UC9
        usecase "体験の一覧を表示する" as UC12
        usecase "体験を削除する" as UC10
        usecase "体験の共有を公開する" as UC11
        usecase "体験の共有を非公開にする" as UC13
    }
}

' ログイン済みユーザーのアクション
User --> UC2
User --> UC4
User --> UC6
User --> UC7
User --> UC8
User --> UC9
User --> UC10
User --> UC12

' 未ログインユーザーのアクション
Guest --> UC1
Guest --> UC3
Guest --> UC5
Guest --> UC6
Guest --> UC9
Guest --> UC12

' ユースケース間の関係
' 更新系はログイン必須
UC2 ..> UC3: <<include>>
UC7 ..> UC3: <<include>>
UC8 ..> UC3: <<include>>
UC10 ..> UC3: <<include>>

' 体験記録の公開/非公開設定
UC7 ..> UC11: <<extend>>
UC7 ..> UC13: <<extend>>
UC8 ..> UC11: <<extend>>
UC8 ..> UC13: <<extend>>
UC10 ..> UC13: <<include>>

' 継承関係
User --|> Guest

@enduml
