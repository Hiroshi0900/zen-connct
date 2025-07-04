@startuml "zenconnect - オブジェクト図(object diagram)"

' ----- 仮登録ユーザーの例(ProvisionalUser examples) -----
object "仮登録ユーザー1(provisionalUser1)" as provisionalUser1 {
  ユーザーID(userId) = "user-001"
  メールアドレス(email) = "tanaka@example.com"
  登録トークン(registrationToken) = "abc123xyz"
}

' ----- 本登録ユーザーの例(ActiveUser examples) -----
object "本登録ユーザー1(activeUser1)" as activeUser1 {
  ユーザーID(userId) = "user-002"
  認証サーバーユーザーID(authServerUserId) = "auth0|12345"
}

object "田中さんのプロフィール(profile1)" as profile1 {
  表示名(displayName) = "田中太郎"
  自己紹介(bio) = "毎日瞑想を実践しています。マインドフルネスが好きです。"
  プロフィール画像URL(profileImageUrl) = "https://example.com/images/tanaka.jpg"
}

object "本登録ユーザー2(activeUser2)" as activeUser2 {
  ユーザーID(userId) = "user-003"
  認証サーバーユーザーID(authServerUserId) = "auth0|67890"
}

object "鈴木さんのプロフィール(profile2)" as profile2 {
  表示名(displayName) = "鈴木花子"
  自己紹介(bio) = "ヨガと瞑想で心を整えています"
  プロフィール画像URL(profileImageUrl) = null
}

' ----- 公開体験記録の例(PublicExperience examples) -----
object "公開体験記録1(publicExperience1)" as publicExperience1 {
  体験記録ID(experienceId) = "exp-001"
  ユーザーID(userId) = "user-002"
}

object "体験記録内容1(content1)" as content1 {
  作成日時(createdAt) = "2025-06-29T08:00:00Z"
  更新日時(updatedAt) = "2025-06-29T08:00:00Z"
}

object "瞑想セッション1(session1)" as session1 {
  開始時刻(startTime) = "2025-06-29T08:00:00Z"
  終了時刻(endTime) = "2025-06-29T08:20:00Z"
  瞑想タイプ(meditationType) = "マインドフルネス瞑想"
  メモ(note) = "朝の静かな時間に集中できた"
}

object "感情状態1(emotionalState1)" as emotionalState1 {
  瞑想前(before) = "少し不安"
  瞑想後(after) = "落ち着いた"
}

' ----- 非公開体験記録の例(PrivateExperience examples) -----
object "非公開体験記録1(privateExperience1)" as privateExperience1 {
  体験記録ID(experienceId) = "exp-002"
  ユーザーID(userId) = "user-002"
}

object "体験記録内容2(content2)" as content2 {
  作成日時(createdAt) = "2025-06-29T20:00:00Z"
  更新日時(updatedAt) = "2025-06-29T20:00:00Z"
}

object "瞑想セッション2(session2)" as session2 {
  開始時刻(startTime) = "2025-06-29T20:00:00Z"
  終了時刻(endTime) = "2025-06-29T20:15:00Z"
  瞑想タイプ(meditationType) = "呼吸瞑想"
  メモ(note) = null
}

object "感情状態2(emotionalState2)" as emotionalState2 {
  瞑想前(before) = "疲れている"
  瞑想後(after) = "リフレッシュした"
}

' ----- 別ユーザーの公開体験記録(Another user's PublicExperience) -----
object "公開体験記録2(publicExperience2)" as publicExperience2 {
  体験記録ID(experienceId) = "exp-003"
  ユーザーID(userId) = "user-003"
}

object "体験記録内容3(content3)" as content3 {
  作成日時(createdAt) = "2025-06-30T07:30:00Z"
  更新日時(updatedAt) = "2025-06-30T07:30:00Z"
}

object "瞑想セッション3(session3)" as session3 {
  開始時刻(startTime) = "2025-06-30T07:30:00Z"
  終了時刻(endTime) = "2025-06-30T07:45:00Z"
  瞑想タイプ(meditationType) = "慈悲の瞑想"
  メモ(note) = "感謝の気持ちを込めて"
}

object "感情状態3(emotionalState3)" as emotionalState3 {
  瞑想前(before) = "普通"
  瞑想後(after) = "幸せ"
}

' ----- オブジェクト間の関係(Object relationships) -----
activeUser1 -- profile1
activeUser2 -- profile2

publicExperience1 -- content1
content1 -- session1
content1 -- emotionalState1

privateExperience1 -- content2
content2 -- session2
content2 -- emotionalState2

publicExperience2 -- content3
content3 -- session3
content3 -- emotionalState3

' ----- 注記(Notes) -----
note right of provisionalUser1
  仮登録ユーザーは
  プロフィールを持たない
end note

note right of publicExperience1
  田中さんの公開体験記録
  他のユーザーも閲覧可能
end note

note right of privateExperience1
  田中さんの非公開体験記録
  本人のみ閲覧可能
end note

note left of activeUser2
  鈴木さんは画像を
  設定していない
end note

@enduml