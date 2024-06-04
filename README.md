# gqlgen-sample

## サーバーの構築

### プロジェクトの骨組みを作成する
```zsh
go run github.com/99designs/gqlgen init
```

### スキーマを定義する
- ` schema.graphqls`に定義する

### リゾルバを実装する
- `graph/schema.resolvers.go`がリゾルバ関数本体
- `graph/resolver.go`にてデータベースなどのアプリの依存関係を宣言する

### ブラウザ操作
- `http://localhost:8080`を開く
- クエリ実行
    ```
    mutation createTodo {
      createTodo(input: { text: "todo", userId: "1" }) {
        user {
          id
        }
        text
        done
      }
    }
    ```
    ```
    query findTodos {
      todos {
        text
        done
        user {
          name
        }
      }
    }
    ```

### 触りそうなところ
- `model/`でスキーマ定義
- `schema.resolvers.go`のコード実装あたり？
