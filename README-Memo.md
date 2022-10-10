
## 新しいテーブル

`api/db/schema.prisma`を編集し、次のコマンドを実行すると、migrationが実行され、スキーマの定義からDBの定義を作れる
```
yarn rw prisma migrate dev
```

##　CRUDを含んだscaffoldを生成
```
yarn rw g scaffold post
```
次のような感じでCRUDに必要なファイルを生成できる。Redwoodはこれらをscaffolds(足場)と呼んでいるらしい
```
    ✔ Successfully wrote file `./web/src/components/Post/EditPostCell/EditPostCell.tsx`
    ✔ Successfully wrote file `./web/src/components/Post/Post/Post.tsx`
    ✔ Successfully wrote file `./web/src/components/Post/PostCell/PostCell.tsx`
    ✔ Successfully wrote file `./web/src/components/Post/PostForm/PostForm.tsx`
    ✔ Successfully wrote file `./web/src/components/Post/Posts/Posts.tsx`
    ✔ Successfully wrote file `./web/src/components/Post/PostsCell/PostsCell.tsx`
    ✔ Successfully wrote file `./web/src/components/Post/NewPost/NewPost.tsx`
    ✔ Successfully wrote file `./api/src/graphql/posts.sdl.ts`
    ✔ Successfully wrote file `./api/src/services/posts/posts.ts`
    ✔ Successfully wrote file `./api/src/services/posts/posts.scenarios.ts`
    ✔ Successfully wrote file `./api/src/services/posts/posts.test.ts`
    ✔ Successfully wrote file `./web/src/scaffold.css`
    ✔ Successfully wrote file `./web/src/lib/formatters.tsx`
    ✔ Successfully wrote file `./web/src/lib/formatters.test.tsx`
    ✔ Successfully wrote file `./web/src/layouts/ScaffoldLayout/ScaffoldLayout.tsx`
    ✔ Successfully wrote file `./web/src/pages/Post/EditPostPage/EditPostPage.tsx`
    ✔ Successfully wrote file `./web/src/pages/Post/PostPage/PostPage.tsx`
    ✔ Successfully wrote file `./web/src/pages/Post/PostsPage/PostsPage.tsx`
    ✔ Successfully wrote file `./web/src/pages/Post/NewPostPage/NewPostPage.tsx`
```

## Prisma Studioでデータを見てみる
```
yarn rw prisma studio
```


## cellを作る

```
yohei@yohei-saitonoMacBook-Air redwoodblog % yarn rw g cell Articles
  ✔ Generating cell files...
    ✔ Successfully wrote file `./web/src/components/ArticlesCell/ArticlesCell.mock.ts`
    ✔ Successfully wrote file `./web/src/components/ArticlesCell/ArticlesCell.test.tsx`
    ✔ Successfully wrote file `./web/src/components/ArticlesCell/ArticlesCell.stories.tsx`
    ✔ Successfully wrote file `./web/src/components/ArticlesCell/ArticlesCell.tsx`
  ↓ Generating types ... [skipped]
    → Skipping type generation: no SDL defined for "articles". To generate types, run 'yarn rw g sdl articles'.
```


## サマリー

```
Summary
To recap, what did we actually do to get this far?

Generate the homepage
Generate the blog layout
Define the database schema
Run migrations to update the database and create a table
Scaffold a CRUD interface to the database table
Create a cell to load the data and take care of loading/empty/failure/success states
Add the cell to the page
The last few steps will become a standard lifecycle of new features as you build a Redwood app.
```


## SDL(schema definition language)を作る
次のようにGraphQLの定義を生成
```
yohei@yohei-saitonoMacBook-Air redwoodblog % yarn rw g sdl Contact
  ✔ Generating SDL files...
    ✔ Successfully wrote file `./api/src/graphql/contacts.sdl.ts`
    ✔ Successfully wrote file `./api/src/services/contacts/contacts.scenarios.ts`
    ✔ Successfully wrote file `./api/src/services/contacts/contacts.test.ts`
    ✔ Successfully wrote file `./api/src/services/contacts/contacts.ts`
  ✔ Generating types ...
```

読み取り専用のSDLが欲しい場合
```
yarn rw g sdl Contact --no-crud
```

GraphQLのデバックはここが便利
http://localhost:8911/graphql
