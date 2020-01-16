---
aliases:
- /tools/2014/06/18_pretty-recursive-grep.html
- /post/2014/pretty-recursive-grep/
categories:
- tools
date: 2014-06-18T00:00:00Z
tags:
- shell
title: Pretty Recursive Grep
type: post
year: '2014'
---
[ack]: http://beyondgrep.com
*TL;DR* Set `GREP_OPTIONS='-RI --color=auto'`. Or install [ack][].
<!--more-->

[GNU grep]: http://www.gnu.org/software/grep/

I'm looking for TODO entries in source code on a machine that does not have
[ack][] installed. It does have [GNU grep][], though.

Obviously I want to search subdirectories. I can choose between
`--recursive`, `-R`, or using `rgrep` on this particular machine.

I am usually searching through source code. I hardly ever want
binary files to match. That means `--binary-file=without-match` 
or `-I`.

Finally, I like pretty colors. The `--color=auto` option makes me
happy.

That leaves me with this invocation.

~~~ console
$ grep --recursive --binary-file=without-match --color=auto 'TODO' .
~~~ 

Or maybe the short form would be easier.

~~~ console
$ rgrep -I --color=auto 'TODO' .
~~~ 

[environment variables]: http://www.gnu.org/software/grep/manual/html_node/Environment-Variables.html

Probably smartest to look at what [environment variables][] I could set
up in order to skip remembering this stuff at all.

~~~ bash
export GREP_OPTIONS='-RI --color=auto'
~~~ 

Pop that in my `.bashrc` and I'm set.

~~~ console
$ grep 'TODO' .
~~~ 

All right. Back to work.