# How to use `git bisect`

Find the change that introduced a bug in your code.

The `git bisect` command helps you to find which change introduced a bug in your code. It’s easy and quick, but most people don’t know about it.

## The problem

You notice that in the most recent commit (let’s say `4a4e`), a feature is not working, and you remember than at some point in the past (let’s say commit `f8a4`) is was working just fine. The task is to find out which commit introduced the bug.

## How does it work?

Git uses the bisection algorithm to help you search the offending commit. To start, you need to mark a `bad` commit and a `good` commit, git will checkout a commit in the middle for you to test. Then you mark it either as `good` or `bad`, and then the process starts again.

## How?

Just checkout the bad commit (`4a4e`) and start `git bisect`:

```bash
(4a4e) $ git bisect start
(4a4e) $ git bisect bad
(4a4e) $ git bisect good f8a4
```









| Step 1   | Step 2   | Step 3   | Step 4   | Step 5   | Step 6   | Step 7   |
|----------|----------|----------|----------|----------|----------|----------|
| `4a4e` :anguished: |     |          |          |          |          |          |
| `cfaf`   |          |          |          |          |          |          |
| `e6f1`   |          |          |          |          |          |          |
| `77ca`   |          |          |          |          |          |          |
| `9e15`   |          |          |          |          |          |          |
| `f99c`   |          |          |          |          |          |          |
| `1642`   |          |          |          |          |          |          |
| `4ba6`   |          |          |          |          |          |          |
| `7e56`   |          |          |          |          |          |          |
| `397b`   |          |          |          |          |          |          |
| `7eb5`   |          |          |          |          |          |          |
| `4203`   |          |          |          |          |          |          |
| `09af`   |          |          |          |          |          |          |
| `6d3b`   |          |          |          |          |          |          |
| `0219`   |          |          |          |          |          |          |
| `34a1` ? | `34a1` :anguished: | `34a1` :anguished: |          |          |          |          |
| `1054`   | `1054`   | `1054`   |          |          |          |          |
| `bcab`   | `bcab`   | `bcab`   |          |          |          |          |
| `4ae6`   | `4ae6`   | `4ae6` ? | `4ae6` :anguished: |          |          |          |
| `7d75`   | `7d75`   | `7d75`   | `7d75`   |          |          |          |
| `e079`   | `e079`   | `e079`   | `e079` ? | `e079` :anguished: | `e079` :anguished: | `e079` :sunglasses: |
| `8013`   | `8013`   | `8013`   | `8013`   | `8013` ? | `801e` :smiley: |          |
| `7487`   | `7487` ? | `7487` :smiley: | `7487` :smiley: | `7487` :smiley: |         |          |
| `f3b2`   | `f3b2`   |          |          |          |          |          |
| `b12a`   | `b12a`   |          |          |          |          |          |
| `301f`   | `301f`   |          |          |          |          |          |
| `5151`   | `5151`   |          |          |          |          |          |
| `2dac`   | `2dac`   |          |          |          |          |          |
| `1ed8`   | `1ed8`   |          |          |          |          |          |
| `f8a4` :smiley: | `f8a4` :smiley: |          |          |          |          |          |
| `...`    |          |          |          |          |          |          |  
