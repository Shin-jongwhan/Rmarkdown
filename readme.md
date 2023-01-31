# Rmarkdown
## 230131
### https://blog.zarathu.com/posts/2019-01-03-rmarkdown/
### <br/><br/><br/>

--------------------------------------------------------------------------------------------
### R 다운로드
#### https://cran.yu.ac.kr/
### R studio 다운로드
#### https://posit.co/
### <br/><br/><br/>

### output 옵션 설정
#### ![image](https://user-images.githubusercontent.com/62974484/215626796-d895667d-c267-4d79-9b53-9fd708e93e7c.png)
#### ![image](https://user-images.githubusercontent.com/62974484/215627012-d2737450-1465-4394-9cc2-1527757e7f74.png)
### <br/><br/><br/>

### 윈도우 R studio 에서 실행하는 방법
#### ![image](https://user-images.githubusercontent.com/62974484/215626666-8fa45579-900b-4ddc-ae38-ce0f015186e5.png)
#### ![image](https://user-images.githubusercontent.com/62974484/215626706-0e691163-abc2-417a-aa5f-e1b644e9a263.png)
### <br/><br/><br/>

### Linux 에서 실행하는 방법
```
Rscript -e "library(knitr); stitch('test.Rmd')"
```
#### ![image](https://user-images.githubusercontent.com/62974484/215626544-cbf92857-4c79-4d73-8638-255fb8275784.png)
### <br/><br/><br/>

--------------------------------------------------------------------------------------------
## 사용 방법
### <br/>

### yaml (헤더와 아웃풋 옵션 설정)
### yaml 영역은 --- 으로 시작해서 --- 으로 끝난다.
- date: "`r format(Sys.Date())`" : 자동으로 현재 날짜
```
---
title: "R Markdown 기초"
subtitle: "Rmarkdown test"
author: "신종환"
date: "`r format(Sys.Date())`"
output:
  html_document:
    fig_height: 6
    fig_width: 10
    highlight: textmate
    theme: cosmo
    toc: yes
    toc_depth: 3
    toc_float: yes
  pdf_document:
    fig_height: 6
    fig_width: 10
    toc: no
  word_document:
    fig_height: 6
    fig_width: 9
    toc: no
---
```
