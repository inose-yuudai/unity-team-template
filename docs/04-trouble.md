# 困った時

わからない時は、無理に進めず、仲間か先生に聞きましょう。

## GitHub Desktop の左側に、変わったファイルが出ない

上から順に確かめます。

1. **「Changes」のタブを見ているか**
   - 左上の「Changes」と「History」のうち、「Changes」を押します。
2. **チームのリポジトリを開いているか**
   - 左上の「Current Repository」が、チームのリポジトリの名前になっているか見ます。違う時は、押して選び直します。
3. **Unity で保存したか**
   - Unity で「File」→「Save」（シーンの保存）と、「File」→「Save Project」（そのほかの変更の保存）を押します。
   - 保存したら、GitHub Desktop の画面を一度クリックします。一覧が新しくなります。
4. **もうコミットしていないか**
   - 「History」のタブに自分のコミットがあれば、コミットは済んでいます。上の「Push origin」を押せば大丈夫です。
5. **Unity のプロジェクトが、clone したフォルダの中にあるか**（Unity のプロジェクトを作った直後は、これがいちばん多い原因です）
   - GitHub Desktop の上のメニュー「Repository」→「Show in Finder」（Windows は「Show in Explorer」）を押すと、clone したフォルダが開きます。
   - その中に `Game` フォルダがなければ、Unity のプロジェクトは別の場所に作られています。
   - 本当の場所は、Unity Hub のプロジェクトの一覧で `Game` の右の「…」→「Show in Finder」（Windows は「Show in Explorer」）を押すとわかります。

### プロジェクトが別の場所にできていた時の直し方

まだ 1 回もコミットしていない時のやり方です。

1. Unity を閉じる
2. `Game` フォルダを**フォルダごと**、clone したフォルダの中に動かす
   - フォルダごと動かすのは大丈夫です。（`Assets` の中のファイルを 1 つずつ動かすのはダメです。）
3. Unity Hub の一覧で、古い `Game` の右の「…」→「Remove project from list」を押して、一覧から外す
4. 「Add」→「Add project from disk」で、動かした `Game` フォルダを選ぶ
5. GitHub Desktop の左側に、`Game/Assets` などのファイルが出たか見る

## リーダー以外の人の PC に、`Game` フォルダが届かない

- GitHub Desktop で「Fetch origin」→「Pull origin」を押したか確かめます。
- それでも届かない時は、リーダーが「Push origin」まで押したか聞きましょう。GitHub のリポジトリのページに `Game` フォルダが見えていれば、Push は済んでいます。

## コンフリクトが出た

GitHub Desktop に「Resolve conflicts before merging」と出ます。あわてなくて大丈夫です。

### シーン・プレハブ（`.unity`・`.prefab`・`.asset`）の時

中身を手で直すのはやめましょう。どちらか一方を選びます。

1. どちらを残すか、相手と話して決める
2. コンフリクトしたファイルの右にある「▼」を押す
3. 次のどちらかを選ぶ
   - 「Use the modified file from main」… main の方を使う（自分の変更は消える）
   - 「Use the modified file from （自分のブランチ）」… 自分の方を使う（相手の変更は消える）
4. 「Continue merge」を押す
5. 消えた方の変更は、あとでもう一度やり直す

### プログラム（`.cs`）の時

1. 「Open in Visual Studio Code」などを押して、ファイルを開く
2. 次のような所を探す

   ```
   <<<<<<< HEAD
   自分の書いた行
   =======
   相手の書いた行
   >>>>>>> main
   ```

3. 残したい行だけにして、`<<<<<<<`・`=======`・`>>>>>>>` の行を消す
4. 保存して GitHub Desktop に戻り、「Continue merge」を押す

途中でわからなくなったら「Abort merge」を押すと、始める前の状態に戻れます。

## まだ Push していないコミットを取り消したい

1. 左上の「History」タブを開く
2. いちばん上のコミットを右クリック →「Undo commit」

変更は消えずに、コミットする前の状態に戻ります。

## Push したコミットを取り消したい

1. 「History」タブで、取り消したいコミットを右クリック →「Revert changes in commit」
2. 「Push origin」を押す

「元に戻す」という新しいコミットが作られます。

## 変更を捨てて、最後のコミットの状態に戻したい

- 「Changes」タブで、ファイルを右クリック →「Discard changes」（全部なら「Discard all changes」）
- **捨てた変更は元に戻せません。** 本当に要らないか確かめてから押しましょう。

## main のまま作業してしまった

### まだコミットしていない時

1. 「Current Branch」→「New Branch」でブランチを作る
2. 「Bring my changes to （新しいブランチ）」を選ぶ

変更は、新しいブランチに移ります。

### コミットしたけど、まだ Push していない時

1. 「History」→ そのコミットを右クリック →「Undo commit」
2. 上の「まだコミットしていない時」と同じように、ブランチを作って変更を移す
3. もう一度コミットする

## Push できない（rejected と出る）

ほかの人が、先に同じブランチに Push しています。「Pull origin」を押してから、もう一度「Push origin」を押しましょう。

## Unity を開くと、表示がおかしい・エラーがたくさん出る

1. Unity のバージョンが、README のバージョンと同じか確かめる
2. 同じなら、Unity を閉じて `Game/Library` フォルダを消し、開き直す
   - Library は、開く時に自動で作り直されます（少し時間がかかります）。

## 何もしていないのに、たくさんのファイルが「Changes」に出る

- Unity のバージョン違いのことが多いです。バージョンをそろえましょう。
- `Library` の中のファイルが出ている時は、`.gitignore` が効いていません。コミットせずに、先生に画面を見せてください。

## 大きいファイルが送れない（100MB を超えている）

コミットを取り消して、そのファイルを外します。小さくできないか（画像なら大きさを下げる、音なら ogg にする）考えましょう。困ったら先生に相談してください。
