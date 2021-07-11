## :speech_balloon:Git Flow Project Implementation
This will serve as a guideline for implementing new projects using git flow workflow. 

###### By: [arquizade](https://github.com/arquizade")
-------------
#### :bookmark: Git flow workflow diagram

![](https://zepel.io/blog/content/images/2020/05/GitFlow-git-workflow-2.png)

> Image by zepel.io
-------------
#### :bookmark: Server design layout
![](https://docs.google.com/drawings/d/e/2PACX-1vTl0_x8AEl95GC7XEAX8oejkpo6zuJ-XcwmBEeabKvq8ZqRllFCm0pPNyop52iQSg1Iy1DaJlcFeyMd/pub?w=1440&h=1080)

-------------

##### :bulb: Getting Started
Installation process for windows, linux and mac
- On macOS systems, you can execute brew install git-flow
- On windows you will need to download git and install git-flow
- On linux, execute sudo apt install git-flow

##### :video_game: Initializing Git Flow
Execute this command inside git project terminal (master)
```
$ git flow init -d
```
(-d) command will set the config default
```
Initialized empty Git repository in ~/project/.git/
No branches exist yet. Base branches must be created now.
Branch name for production releases: [main]
Branch name for "next release" development: [develop]

How to name your supporting branch prefixes?
Feature branches? [feature/]
Release branches? [release/]
Bugfix branches? [bugfix/]
Hotfix branches? [hotfix/]
Support branches? [support/]
Version tag prefix? []
```
Then it will set develop as working branch
```
$ git branch -a
* develop
 main
```

##### :pushpin: Creating feature branch (start code edit) `your@[DEV]develop-branch`

```
$ git pull origin develop
$ git flow feature start feature_branch
```
...Code...Code..code here then save file, add and commit
```
$ git add to_do_file
$ git commit -m 'update to do file'
```
##### :pushpin: Finishing feature branch (satisfied with the code) `your@[DEV]develop-branch`
```
$ git flow feature finish feature_branch
$ git push origin develop
```

##### :pushpin: Release branch (for QA test) `your@[STAGE]release-branch`
```
$ git flow release start 0.1.0
Switched to a new branch 0.1.0
```
...:memo: Execute test here... :ship: if approved and release is stable and ready to ship.. if not do not execute this command..

```
$ git flow release finish 0.1.0
$ git push origin --tags
```

...:warning: if release have issues or bug fix
```
$ git flow bugfix start 'bugfix_branch'
```
...:crystal_ball: developer do the magic trick to fix the issue.. satisfied with the code
```
$ git flow bugfix finish 'bugfix_branch'
```
...:computer: then create new release and delete the previous
```
$ git flow release delete -r release/0.1.0
$ git flow release start 0.1.1
```
....:thumbsup: QA do the test again and when satisfied with the fix ..
```
$ git flow release finish 0.1.1
$ git push origin --tags
```
...:checkered_flag: when you excute the release finish command it will automatically merge to master and develop branch ~ but not in production server

##### :pushpin: Deploying to production `your@[PROD]master-branch`
```
$ git pull origin master
```

##### :pushpin: Maintenance or “hotfix” branches are used to quickly patch production release `your@[DEV]develop-branch`
```
$ git pull origin master
$ git flow hotfix start hotfix_branch
..
...
....
$ git flow hotfix finish hotfix_branch
```
...:wrench: then access the production server and execute the command
```
$ git pull origin master
```
-------------
#### :paperclip: Additional Command:
Showing the difference with the updated codes
```
$ git diff
```

```git
diff --git a/index.html b/index.html
index d17f10e..6c12524 100644
--- a/index.html
+++ b/index.html
@@ -1,4 +1,4 @@
-edit line
+Title Header
 Lorem ipsum, dolor sit amet consectetur adipisicing elit. Sit fuga fugiat, asperiores dolor delectus atque iure, aliquid optio labore quod voluptate in necessitatibus harum quaerat corrupti inventore a recusandae ad.
```
> :tv: [Using git diff video explanation](https://www.youtube.com/watch?v=RophmTcbf8o)
-------------
## :book: References
[Gitflow](https://git.logikum.hu/flow "Git Flow's Documentation")
[Management Workflow](https://rubygarage.org/blog/git-and-release-management-workflow "A Step-by-Step Guide Git-Flow")
[Gitflow Commands](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow "Tutorials gitflow workflow")
[Branching Strategy](https://zepel.io/blog/5-git-workflows-to-improve-development/ "Improve your development process")