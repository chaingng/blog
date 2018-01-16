---
title: "gitで特定のコミットの状態に戻す"
date: 2018-01-01T10:00:00+09:00
tags: [ "git"]
---

git resetを使う。  
`git reset --hard [COMMIT_HASH]` で指定したコミットの状態に戻すことができる。

### 戻したいcommitのhashを確認する

```
$ git log
commit 804c6b5c0d5b66caa6e49d788d2e6c4fe2cfa9a0 (HEAD -> master)
Author: Takatomo Honda <chngng0103@gmail.com>
Date:   Sun Dec 10 10:06:45 2017 +0900

    Update me.md

commit caf52bb8b5d8f2111920c9fb8eab9533d2833375
Author: Takatomo Honda <chngng0103@gmail.com>
Date:   Thu Dec 7 13:54:51 2017 +0900

    Update pipenv.md

commit 993ea1d48b0b501cd83fa13a6be917c9280c2df4
Author: Takatomo Honda <chngng0103@gmail.com>
Date:   Thu Dec 7 13:49:30 2017 +0900

    Create pipenv.md

commit 892391f01b8ef60128e2e2b8105a515656020292
Author: Takatomo Honda <chngng0103@gmail.com>
Date:   Mon Dec 4 15:38:51 2017 +0900

    Create nodejs_forever.md

commit 95102e74e1033fb07d4f8e20c01647cbbd28cd21
Author: Takatomo Honda <chngng0103@gmail.com>
Date:   Thu Nov 30 16:31:49 2017 +0900

    Update git_save_pw.md
```

### 指定のコミットに状態をリセット

```
$ git reset --hard 892391f01b8ef60128e2e2b8105a515656020292
HEAD is now at 892391f Create nodejs_forever.md
```

確認すると特定のコミットまで状態が戻っていることがわかる
```
$ git log
commit 892391f01b8ef60128e2e2b8105a515656020292 (HEAD -> master)
Author: Takatomo Honda <chngng0103@gmail.com>
Date:   Mon Dec 4 15:38:51 2017 +0900

    Create nodejs_forever.md

commit 95102e74e1033fb07d4f8e20c01647cbbd28cd21
Author: Takatomo Honda <chngng0103@gmail.com>
Date:   Thu Nov 30 16:31:49 2017 +0900

    Update git_save_pw.md
```

### 最初のコミットの状態に戻す
commitの情報は保持しているので、最初のコミットを指定すれば元に戻すことができる

```
$ git reset --hard 804c6b5c0d5b66caa6e49d788d2e6c4fe2cfa9a0
HEAD is now at 804c6b5 Update me.md
```

状態が最初の状態に戻っていることがわかる
```
$ git log
commit 804c6b5c0d5b66caa6e49d788d2e6c4fe2cfa9a0 (HEAD -> master)
Author: Takatomo Honda <chngng0103@gmail.com>
Date:   Sun Dec 10 10:06:45 2017 +0900

    Update me.md

commit caf52bb8b5d8f2111920c9fb8eab9533d2833375
Author: Takatomo Honda <chngng0103@gmail.com>
Date:   Thu Dec 7 13:54:51 2017 +0900

    Update pipenv.md

commit 993ea1d48b0b501cd83fa13a6be917c9280c2df4
Author: Takatomo Honda <chngng0103@gmail.com>
Date:   Thu Dec 7 13:49:30 2017 +0900

    Create pipenv.md

commit 892391f01b8ef60128e2e2b8105a515656020292
Author: Takatomo Honda <chngng0103@gmail.com>
Date:   Mon Dec 4 15:38:51 2017 +0900

    Create nodejs_forever.md
```

