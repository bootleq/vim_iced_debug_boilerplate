# Study of vim-iced #356 (Resolved)

## Setup

Clone this project

```shell
  mkdir ~/tmp
  git clone git@github.com:bootleq/vim_iced_debug_boilerplate.git ~/tmp/iced_test_356
```

Ref [minimal_configuration][], install vim stuff to `/tmp`.

```shell
  mkdir -p /tmp/vim-iced-test/pack/iced/start
  git clone https://github.com/guns/vim-sexp \
        /tmp/vim-iced-test/pack/iced/start/vim-sexp
  git clone https://github.com/liquidz/vim-iced \
        /tmp/vim-iced-test/pack/iced/start/vim-iced
```

Unlike the instruction, we will use `test_config.vim` in this directory.



## Reproduce

- Start REPL first

```shell
  cd clj/
  /tmp/vim-iced-test/pack/iced/start/vim-iced/bin/iced repl

```

- Start vim in project dir

```shell
  cd iced_test_356
  vim -u test_config.vim clj/test/bootleq/iced_debug/core.clj
```

In Vim:

```vim
  :IcedConnect
  G
  :IcedTestUnderCursor
```

Check result:

- Sign column should has an error sign, at the failing line (7).
- Open `:cwindow`, see if the filename correct, or has `NO_SOURCE_FILE` in it.


## Other Info

- If start vim in `clj` directory, `IcedTestNs` works, while `IcedTestUnderCursor` still doesn't.


## Solution

See original issue, this is confirmed a clojure project setup problem.


[minimal_configuration]: https://liquidz.github.io/vim-iced/#minimal_configuration
