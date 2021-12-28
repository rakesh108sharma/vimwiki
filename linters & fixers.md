[[PYTHON]]
# linters and fixers for python

## ale
ale-'engine' needs to be installed first

`Plug 'dense-analysis/ale'`

## linters
`conda/pip install flake8`

`pip install -U mypy`

## fixers

`pip install black`

## vimrc
```
let g:ale_linters = { 'python': ['flake8a', 'mypy']}
let g:ale_fixers = { 'python': ['black']}
let g:ale_fix_on_save = 1
```

