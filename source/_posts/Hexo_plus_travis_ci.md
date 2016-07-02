---
title: Hexo搭配Travis CI
date: 2016-06-29 21:32:51
tags: Travis CI
---

裝了Hexo之後發現，要寫文章一定要install Hexo在你那一台電腦。
看～這樣不是比medium或logdown還要差QQ

爬了一下網路上的神文，發現可以搭配Travis做auto deployment，興沖沖的想說應該一兩個小時就可以搞定。
沒想到花了我整整兩天時間...
<!--more-->
![Image of Cameron](http://i.imgur.com/qNlwBOL.gif)

在此就把這兩天遇到的問題整理一下:
- 如果domain是`xxx.github.io`，branch[一定要是master](https://help.github.com/articles/user-organization-and-project-pages/)，一開始忘記這件事結果浪費我一堆時間QQ
- .travis.yml file format
  **Correct**
  ```
  script:
    - hexo g
  ```
  **Incorrect**
  ```
  script:
  - hexo g
  ```
- Clone下來的theme不會加到git裡面，為了方便我就直接把theme改名字客製成我想要的樣子。

有個重要觀念，hexo的source放在branch(包含theme, posts, pages)，deploy的static html放在master。Travis config中指定branch執行ops，hexo config中指定master為deployment的位置，祖國同胞有畫了一個[流程圖](http://magicse7en.github.io/img/travis-ci-work-flow.png)，~~不過台灣不是中國的一部份~~，可以參考一下。
> 後記：他好像畫錯了，哈哈祖國哈哈。

總而言之，一些基礎的東西看似簡單但常會忽略，像是Travis的life cycle、Github token跟Travic CI的關係或Github的權限這類雜魚問題，魔鬼總是藏在細節裡。看Travis的console就可以很清楚知道你錯在哪一個步驟，~~比jenkins好看多了~~。

不過我發現最快的方式就是[去看別人的.travis.yml](https://github.com/boogoofrog/boogoofrog.github.io/blob/hexo-source/.travis.yml) lol

# 參考資料
- [用 Travis CI 自動部署網站到 GitHub](https://zespia.tw/blog/2015/01/21/continuous-deployment-to-github-with-travis/)
- [使用Travis CI自动构建hexo博客](http://magicse7en.github.io/2016/03/27/travis-ci-auto-deploy-hexo-github/)
