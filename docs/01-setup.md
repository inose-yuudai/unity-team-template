# はじめての準備

最初に 1 回だけやります。全部で 30 分〜1 時間くらいです（Unity を入れる時間が長いです）。

## 1. 道具を入れる（全員）

| 道具 | 何に使う？ | 入手先 |
|---|---|---|
| GitHub のアカウント | チームのファイルを置く場所 | https://github.com/ |
| GitHub Desktop | Git をボタンで使うアプリ | https://desktop.github.com/ |
| Unity Hub | Unity を入れる・開くアプリ | https://unity.com/download |
| Unity（チームで決めたバージョン） | ゲームを作る | Unity Hub の「Installs（インストール）」から |

- GitHub のユーザー名を、先生（またはリーダー）に伝えます。リポジトリに招待されると、メールが届きます。「Accept invitation」を押してください。
- Unity は、**チーム全員が同じバージョン**を入れます。バージョンは README の「Unity のバージョン」に書いてあります。違うバージョンで開くと、ファイルが勝手に書き換わり、ぶつかる原因になります。
- GitHub Desktop の画面は英語です。この手順書では、ボタンの名前を英語のまま書いています。

## 2. リポジトリを自分の PC に持ってくる（clone・全員）

1. GitHub Desktop を開き、GitHub のアカウントでサインインする
2. 上のメニューの「File」→「Clone repository」
3. 一覧からチームのリポジトリを選ぶ
4. 「Local path」（保存する場所）を確かめて「Clone」
   - OneDrive・iCloud Drive・Dropbox などのフォルダの中には置かないでください。同期とぶつかって、ファイルが壊れることがあります。

## 3. Unity のプロジェクトを作る（リーダーだけ・最初の 1 回だけ）

> リーダー以外の人は、とばして「4」へ進んでください。

1. Unity Hub で「New project（新しいプロジェクト）」を押す
2. 上で、チームで決めた Unity のバージョンを選ぶ
3. テンプレート（Universal 2D・Universal 3D など）を選ぶ
4. 右側を、次のように入れる
   - **Project name（プロジェクト名）：`Game`**
   - **Location（保存場所）：2 で clone したフォルダ**
   - 「Use Unity Version Control」などのチェックは**外す**（このチームでは GitHub を使います）
5. 「Create project」を押す。Unity が開くまで待つ
6. Unity を閉じて、GitHub Desktop を見る
   - 左に、変わったファイルの一覧が出ます。`Game/Assets`・`Game/Packages`・`Game/ProjectSettings` の中のファイルなら OK です。
   - **`Game/Library` のファイルが出ていたら、そこで止めて先生に聞いてください。** 入れてはいけない大きいフォルダです。何千個もファイルが出ている時も同じです。
7. 左下の「Summary」に「Unity のプロジェクトを作る」と書いて「Commit to main」を押す
8. 上の「Push origin」を押す
9. README の「Unity のバージョン」を書く
   - バージョンは `Game/ProjectSettings/ProjectVersion.txt` の 1 行目に書いてあります。

この最初の 1 回だけは、main に直接コミットして大丈夫です。次からは、ブランチを作って作業します。

## 4. Unity で開く（リーダー以外）

1. GitHub Desktop で「Fetch origin」→「Pull origin」を押す（リーダーが作った `Game` フォルダが届きます）
2. Unity Hub →「Add（追加）」→「Add project from disk（ディスクから加える）」
3. clone したフォルダの中の **`Game` フォルダ**を選ぶ
4. 一覧に出た `Game` を押して開く
   - 初めて開く時は、数分かかります。
   - 「バージョンが違う」と出たら、開かずに止めます。チームのバージョンを Unity Hub で入れてから開いてください。

## 5. できたか確かめる（全員）

- [ ] Unity でプロジェクトが開けた
- [ ] Unity を閉じたあと、GitHub Desktop の「Changes」が 0 個になっている
  - 何も変えていないのにファイルが出る時は、リーダーか先生に画面を見せてください。

ここまでできたら、[毎日の作業の流れ](02-daily-flow.md) へ進みましょう。
