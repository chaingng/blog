---
title: "spacemacsでクリップボード共有を行う"
date: 2018-04-09T10:00:00+09:00
tags: [ "spacemacs"]
---

spacemacsでコピーしたデータは、デフォルトの設定だとspacemacs外ではペーストできない。  
コピーしたデータをクリップボードにも共有するには、設定を追加する必要がある。

## クリップボード共有のための設定

`~/.spacemacs`のuser-config内に、以下の設定を追加する。

```
(defun dotspacemacs/user-config ()

    ; ...

    (defun copy-to-clipboard ()
      "Copies selection to x-clipboard."
      (interactive)
      (if (display-graphic-p)
          (progn
            (message "Yanked region to x-clipboard!")
            (call-interactively 'clipboard-kill-ring-save)
            )
        (if (region-active-p)
            (progn
              (shell-command-on-region (region-beginning) (region-end) "pbcopy")
              (message "Yanked region to clipboard!")
              (deactivate-mark))
          (message "No region active; can't yank to clipboard!")))
      )

    (defun paste-from-clipboard ()
      "Pastes from x-clipboard."
      (interactive)
      (if (display-graphic-p)
          (progn
            (clipboard-yank)
            (message "graphics active")
            )
        (insert (shell-command-to-string "pbpaste"))
        )
      )
  (evil-leader/set-key "o y" 'copy-to-clipboard)
  (evil-leader/set-key "o p" 'paste-from-clipboard)
)
```

これで、`SPC O Y`にてクリップボードにもデータがコピーされる。  
spacemacsでペーストしたいときには、`SPC O P`とすればよい。
