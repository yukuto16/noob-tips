```mermaid

sequenceDiagram
    actor リクエスト元
    participant API as API
    participant DB as DB

    リクエスト元 ->>+ API: DELETE HTTPリクエスト
    
    API ->>+ DB: 認証情報確認
        rect rgb(255, 100, 100)
            alt 認証失敗
                API ->> API: エラー・ログ出力
                API -->> リクエスト元: HTTP 401 Unauthorized
            end
        end
    DB ->>- API: 認証情報

    API ->> API: パラメーターチェック
        rect rgb(255, 100, 100)
            alt パラメーターエラー
                API ->> API: エラー・ログ出力
                API -->> リクエスト元: HTTP 400 Bad Request
            end
        end

    API ->>+ DB: 削除
        rect rgb(255, 100, 100)
            alt 応答なし
                API ->> API: エラー・ログ出力
                API -->> リクエスト元: HTTP 500 Internal Server Error
            end
       end
    DB ->>- API: 削除結果
        rect rgb(255, 100, 100)
            alt 削除中
                API ->> API: エラー・ログ出力
                API -->> リクエスト元: HTTP 409 Conflict
            end
            alt 削除件数0件
                API ->> API: エラー・ログ出力
                API -->> リクエスト元: HTTP 404 Not Found
            end
        end

    API ->> API: ログ出力
    API ->>- リクエスト元: HTTP 200 OK

```