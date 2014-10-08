
# vim-unite-issue
Vim issue-manager. Browse, time-track, and view issues in Vim.

## Features
- Pure VimL
- Multiple issue providers:
  - GitHub
  - JIRA
- Browse issue list
- View issue and comments as Markdown
- Open issue in browser

## Screenshot
![vim-unite-issue screenshot](https://paste.xinu.at/FVGDx/)

## Planned Features
- Time-tracking per issue
- Publish time-sheets
- Comment reply

## Installation
### Dependencies
- [Shougo/unite]
- [mattn/webapi-vim]
  - curl or wget
- [tyru/open-browser.vim]

Use your favorite plugin manager, mine is [NeoBundle]:
```viml
NeoBundleLazy 'rafi/vim-unite-issue', {
	\  'directory': 'unite-issue',
	\  'unite_sources': [ 'issue' ]
	\  'depends': [
	\    'mattn/webapi-vim', 'tyru/open-browser.vim', 'Shougo/unite.vim'
	\  ]
	\ }
```

## Usage
Open list of issues:
```
:Unite issue:<provider>[:argument]
```
Available actions for candidates:
- `browse`: Open issue in browser
- `view`: View issue and comments as Markdown

### Providers

#### GitHub
- List all personal opened issues: `:Unite issue:github`
- List repository issues: `:Unite issue:github:torvalds/linux`

##### Configuration
```viml
let g:github_token = '0123456789'

" Customize
let g:unite_source_issue_github_state_table = {
  \ 'open': 'O', 'closed': 'C' }
```

#### JIRA
- List all personal unresolved issues: `:Unite issue:jira`
- List custom JQL: `:Unite issue:jira:project=FOO+and+assignee=bar`

##### Configuration
```viml
let g:jira_url = 'https://bugs.acme.com'
let g:jira_username = 'roadrunner'
let g:jira_password = 'meemeep'

" Customize
let g:unite_source_issue_jira_priority_table = {
  \ 10000: '◡', 1: '⚡', 2: 'ᛏ', 3: '●', 4: '○', 5: '▽' }

let g:unite_source_issue_jira_status_table = {
  \ 1: 'plan', 3: 'develop', 4: 'reopened', 5: 'resolved', 6: 'closed',
  \ 10000: 'feedback', 10001: 'stage-test', 10002: 'waiting',
  \ 10003: 'prod-test', 10004: 'pending', 10008: 'review' }

let g:unite_source_issue_jira_type_table = {
  \ 1: 'bug', 2: 'feature', 3: 'task', 4: 'change', 5: 'sub-task',
  \ 6: 'epic', 7: 'story', 8: 'system', 9: 'sub-bug' }
```

## Credits & Contribution

I was inspired by [joker1007/unite-pull-request] and feeling annoyed by needing
a browser to track and browse issues.

This plugin was developed by Rafael Bodill under the [MIT License][license].
Pull requests are welcome.

  [Shougo/unite]: https://github.com/Shougo/unite.vim
  [mattn/webapi-vim]: https://github.com/mattn/webapi-vim
  [tyru/open-browser.vim]: https://github.com/tyru/open-browser.vim
  [NeoBundle]: https://github.com/Shougo/neobundle.vim
  [joker1007/unite-pull-request]: https://github.com/joker1007/unite-pull-request
  [license]: ./LICENSE
