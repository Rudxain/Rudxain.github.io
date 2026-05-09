# Differential Perma-Cache
It consists on using a tool (such as Git) to download a project (either completely or partially), using the same tool for [delta-updates](https://en.wikipedia.org/wiki/Delta_encoding), and using a light-weight IDE (such as Helix or NeoVim) to browse the project (of course, having a text shell (such as Bash) and Unix-like utilities (such as GNU coreutils) is implied).

The purpose of such a setup is to enable an efficient workflow for general-purpose information retrieval:
- Most files are available [locally](https://www.inkandswitch.com/essay/local-first/), which allows fast opening and saves network bandwidth
- User can use whatever search-engine they want, or whichever is most appropriate, such as: `grep`, Ripgrep, `fzf`, `find`, etc...
- If the VCS is Git, blobs will be cached permanently

All of this is in contrast to web browsers:
- Data might not be available locally, because the browser deletes old cache
- User is at the mercy of whatever search-engine is provided by a website, or the browser's own "find in page" (<kbd>ctrl</kbd>+<kbd>f</kbd>) feature
- Cache is ephemeral, even if a server never changes its response

Overall, a much better experience!
