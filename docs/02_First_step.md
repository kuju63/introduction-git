# First step

## Initialize repository

gitでバージョン管理するためにはバージョン管理されていないディレクトリで`git init`を実行します

```bash
mkdir -p local-sample
cd local-sample
git init
```

実行すると`.git`というディレクトリが作成されます。
この中にリポジトリの情報や設定が格納されていきます。

## First commit

リポジトリへ変更を登録するには2Step必要です

1. リポジトリに変更情報を追加

    `git add .`コマンドで現在のディレクトリ以下すべての変更情報をリポジトリに追加します
    この時点ではまだリポジトリに反映されていないことに気を付けてください

2. リポジトリに変更を反映

    `git commit`コマンドでリポジトリに変更を反映します。
    その際に必ず変更内容をコミットメッセージとして入力する必要があります。

    コミットメッセージは以下のようなフォーマットにするのが望ましいです。

    ```text
    変更内容の要約
    
    変更した理由・背景の説明
    ```

実際に空ファイルを登録してみましょう

``` bash
touch README.md
git add .
git commit
```

コミットメッセージは以下のようにします

```text
Initial commit

This commit is just to add empty file of Read me.
```

## Making changes

README.mdに対して変更をしてみましょう

```bash
echo "introduction-git" > README.md
```

実際にGit上ではどのようになっているかを確認します。
リポジトリとの変更が発生しているかは`git status`コマンドで確認できます。

```bash
git status
On branch master
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md

no changes added to commit (use "git add" and/or "git commit -a")
```

変更したREADME.mdが`modified`として表示されているのがわかります。

詳細な修正箇所は`git diff`コマンドで確認できます。

では、先ほどと同様に変更をコミットしましょう

``` bash
git add .
git commit
```

## View history

ここまででリポジトリには2つのコミットができているはずです。

リポジトリの履歴を確認するには`git log`コマンドを使用します。

```bash
git log
commit 1a402692eb95ced3ce531d6e2f18fd3a036ecb78 (HEAD -> master)      
Author: Kurihara Jun <kurihara.jb@om.asahi-kasei.co.jp>               
Date:   Wed May 19 08:58:34 2021 +0900                                
                                                                      
    Update README.md                                                  
                                                                      
    This commit is to update README.md file which add repository name.
                                                                      
commit c6ca7bbc2fdafadaf94b2582325b51a576957812                       
Author: Kurihara Jun <kurihara.jb@om.asahi-kasei.co.jp>               
Date:   Wed May 19 08:58:00 2021 +0900                                
                                                                      
    Initial commit                                                    
                                                                      
    This commit is just to add empty file of Read me.                 
```

実際に使用していく際には詳細な情報は必要ないため、最小限の情報かつグラフで表示することが多いです。
`git log`コマンドのオプションを追加することで最小限の表示ができます。

```bash
git log --oneline --graph --all           
* 1a40269 (HEAD -> master) Update README.md
* c6ca7bb Initial commit                   
```

## Revert changes

```bash
touch CONTRIBUTING.md
echo "Changed" >> README.md
git add .
git status
On branch master                                   
Changes to be committed:                           
  (use "git restore --staged <file>..." to unstage)
        new file:   CONTRIBUTING.md                
        modified:   README.md                      
```

```bash
git reset HEAD README.md
Unstaged changes after reset:
M       README.md            
```

```bash
git status
On branch master                                                       
Changes to be committed:                                               
  (use "git restore --staged <file>..." to unstage)                    
        new file:   CONTRIBUTING.md                                    
                                                                       
Changes not staged for commit:                                         
  (use "git add <file>..." to update what will be committed)           
  (use "git restore <file>..." to discard changes in working directory)
        modified:   README.md                                          
```

``` bash
git restore README.md
git status
On branch master                                   
Changes to be committed:                           
  (use "git restore --staged <file>..." to unstage)
        new file:   CONTRIBUTING.md                
```

CONTRIBUTING.mdをコミット

```bash
git commit
```

### Revert history

```bash
git log --oneline
229c494 (HEAD -> master) Add CONTRIBUTING.md
1a40269 Update README.md                    
c6ca7bb Initial commit                      
```

コミットID`229c494`を打ち消す

```bash
git revert 229c494
git log --all --oneline --graph
* ad868d6 (HEAD -> master) Revert "Add CONTRIBUTING.md"
* 229c494 Add CONTRIBUTING.md                          
* 1a40269 Update README.md                             
* c6ca7bb Initial commit                               
```

[Next to managing branch](03_managing_branch.md)
