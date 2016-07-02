---
title: Hexo搭配Travis CI
date: 2016-06-29 21:32:51
tags: Travis CI
---

裝了Hexo之後發現，要寫文章一定要install Hexo在你那一台電腦。
看～這樣不是比medium或logdown還要差QQ

爬了一下網路上的神文，發現可以搭配Travis做auto deployment，興沖沖的想說應該一兩個小時就可以搞定。
沒想到花了我整整兩天時間...
![Image of Cameron](http://i.imgur.com/qNlwBOL.gif)

在此就把這兩天遇到的坑整理一下...
- 如果domain是`xxx.github.io`，branch[一定要是master](https://help.github.com/articles/user-organization-and-project-pages/)，一開始忘記這件事浪費一堆時間
- .travis.yml file format
  - [x] Correct
  ```
  script:
    - hexo g
  ```
  - [ ] Incorrect
  ```
  script:
  - hexo g
  ```
- 
不過我發現最快的方式就是[去看別人的.travis.yml](https://github.com/boogoofrog/boogoofrog.github.io/blob/hexo-source/.travis.yml) lol
### 參考資料
-[用 Travis CI 自動部署網站到 GitHub](https://zespia.tw/blog/2015/01/21/continuous-deployment-to-github-with-travis/)
