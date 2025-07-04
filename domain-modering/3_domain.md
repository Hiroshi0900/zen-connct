@startuml "zenconnect- ドメインモデル図"

skinparam packageStyle rectangle

' ----- ユーザー集約 -----
package "ユーザー集約(User Aggregate)" {
  abstract class "ユーザー(User)" as User <<Entity>> <<AggregateRoot>> {
    + ユーザーID(userId)
  }
  
  class "仮登録ユーザー(ProvisionalUser)" as ProvisionalUser <<Entity>> {
    + メールアドレス(email)
    + 登録トークン(registrationToken)
  }
  
  class "本登録ユーザー(ActiveUser)" as ActiveUser <<Entity>> {
    + 認証サーバーユーザーID(authServerUserId)
    + プロフィール(profile)
  }
  
  class "プロフィール(Profile)" as Profile <<Value Object>> {
    + 表示名(displayName)
    + 自己紹介(bio)
    + プロフィール画像URL(profileImageUrl)
  }
}

' ----- 体験記録集約 -----
package "体験記録集約(Experience Aggregate)" {
  abstract class "体験記録(Experience)" as Experience <<Entity>> <<AggregateRoot>> {
    + 体験記録ID(experienceId)
    + ユーザーID(userId)
    + 体験記録内容(content)
  }
  
  class "公開体験記録(PublicExperience)" as PublicExperience <<Entity>> {
  }
  
  class "非公開体験記録(PrivateExperience)" as PrivateExperience <<Entity>> {
  }
  
  class "体験記録内容(ExperienceContent)" as ExperienceContent <<Value Object>> {
    + 瞑想セッション(session)
    + 感情状態(emotionalState)
    + 作成日時(createdAt)
    + 更新日時(updatedAt)
  }
  
  class "瞑想セッション(MeditationSession)" as MeditationSession <<Value Object>> {
    + 開始時刻(startTime)
    + 終了時刻(endTime)
    + 瞑想タイプ(meditationType)
    + メモ(note)
  }
  
  class "感情状態(EmotionalState)" as EmotionalState <<Value Object>> {
    + 瞑想前(before)
    + 瞑想後(after)
  }
}

' ----- 集約内の関係と多重度 -----
ProvisionalUser --|> User
ActiveUser --|> User
ActiveUser "1" *-- "1" Profile : プロフィールを持つ >

PublicExperience --|> Experience
PrivateExperience --|> Experience
Experience "1" *-- "1" ExperienceContent : 内容を持つ >
ExperienceContent "1" *-- "1" MeditationSession : セッションを持つ >
ExperienceContent "1" *-- "1" EmotionalState : 感情状態を持つ >

' ----- 集約間の関係（ID参照）-----
Experience "0..*" ..> "1" User : ユーザーIDで参照（ユーザーは体験記録を0個以上持てる） >

' ----- ルール/制約の注釈 -----
note right of User
**ユーザールール**
- ユーザーIDは一意である
- ユーザーの状態は型で表現される
- ProvisionalUser: 仮登録状態
- ActiveUser: 本登録完了
- 状態遷移時は新しいインスタンスを作成
end note

note left of Experience
**体験記録ルール**
- 体験記録IDは一意である
- 公開/非公開は型で表現される
- PublicExperience: 公開記録
- PrivateExperience: 非公開記録
- 公開設定変更時は新しいインスタンスを作成
end note

' ----- 集約の境界の説明 -----
note top of User : 集約ルート：ユーザー情報の一貫性を保証

note top of Experience : 集約ルート：体験記録の一貫性を保証

@enduml