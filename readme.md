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

### `yaml` (헤더와 아웃풋 옵션 설정)
### yaml 영역은 --- 으로 시작해서 --- 으로 끝난다.
### 자세한 내용은 아래 사이트를 참고한다.
#### https://cran.r-project.org/web/packages/ymlthis/vignettes/yaml-fieldguide.html
- date: "`r format(Sys.Date())`" : 자동으로 현재 날짜
- output : 세부 output 옵션을 정한다. 아래 설정은 html, pdf, word 파일로 출력할 때 어떻게 출력할지 각각 설정해준 것이다.
- toc : output 에 table 컨텐츠가 있는지 없는지. no / yes 입력.
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
### <br/><br/><br/>

### `R 코드 작성 방법`
#### {r indel, include=TRUE, echo=FALSE} 이라고 적고 R 코드를 작성한다. indel 이라고 써진 것은 code chunck 의 이름이다.
- include = FALSE 옵션으로 문서에는 포함시키지 않고 몰래 실행할 수 있으며, 주로 최초 설정에 이용된다. TRUE 로 설정하면 output 에 코드 결과가 출력된다.
- echo = TRUE는 stdout 에 코드를 보여준다는 뜻이다 (verbose 옵션과 같음).
- knitr::opts_chunk$set(\[옵션\]) : 추가 옵션을 설정할 수 있다.
  - eval=F - 코드를 실행하지 않는다.
  - echo=F - 코드를 보여주지 않는다.
  - include=F - 실행 결과를 보여주지 않는다.
  - message=F - 실행 때 나오는 메세지를 보여주지 않는다.
  - warning=F - 실행 때 나오는 경고를 보여주지 않는다.
  - error=T - 에러가 있어도 실행하고 에러코드를 보여준다.
  - fig.height = 7 - 그림 높이, R로 그린 그림에만 해당한다.
  - fig.width = 7 - 그림 너비, R로 그린 그림에만 해당한다.
  - fig.align = 'center' - 그림 위치, R로 그린 그림에만 해당한다.
### 예시
##### 아래 \ 는 마크다운 문법 오류때문에 넣은 거다. 
```
\```{r indel, include=TRUE, echo=FALSE}
#knitr::opts_chunk$set(echo = TRUE)
#input <- read.table("snakemake@input$multi_indels", header = T)
input <- read.table("./Results/multisample.InDels.stat.xls", header = T)

sort<-t(input)
colnames(sort) <- sort[1,]
d <- as.data.frame(sort)
d <- d[2:length(sort[,1]),]
DT::datatable(d, options = list(pageLength =20, autoWidth = TRUE))

\```
```
### <br/><br/><br/>

### `구획 나누는 방법`
### 탭으로 구획을 나눠 데이터를 보여주려면 다음과 같이 작성한다.
### 그리고 탭을 생성하려면 ## \[탭 이름\] 으로 작성한다.
```
# 1. Project Information{.tabset}
## Client Order Information
```
#### ![image](https://user-images.githubusercontent.com/62974484/215639045-1f73d521-51a5-400c-b096-c288e6340d78.png)
### <br/>

### `마크다운 테이블 작성 방법`
### | 으로 구분해서 테이블을 작성하면 된다.
### 맨위 || 영역은 헤더 부분이다.
### bold 글씨는 \*\*글씨\*\* 로 묶는다.
### ex)
```
|||
|:---:|:---:|
|**Client**|강병수 대표님|
|**Organization**|SYSOFT|
|**ProjectID**|TBD221311|
|**Service Application**|Whole Genome Re-Sequencing|
|**Species**|Staphylococcus aureus|
|**Assembly Accession Number**|GCF_000013425.1_ASM1342v1|
|**Number of Samples**|60|
|**Genome Source**|[NCBI link](https://www.ncbi.nlm.nih.gov/assembly/GCF_000013425.1/)|
|||
```
### <br/>

### `점 항목`
### 마크다운과 똑같이 - 으로 작성한다.
### bold 처리는 \*\*글씨\*\* 로 묶는다.
#### ![image](https://user-images.githubusercontent.com/62974484/215640357-4798f2e4-70b5-4c94-985f-67cc8a7f1ff9.png)
### <br/>

### `R 테이블 작성 방법`
### DT:datatable(data, option = list(option ... )) 을 이용한다.
### 옵션
- pageLength : 한 페이지에 보여주는 행 개수
- autoWidth : 너비 사이즈 자동 조절
- scrollX : 너비가 한 페이지에 다 안 들어갈 때 옆으로 스크롤해서 볼 수 있도록 함. FALSE 하면 옆으로 그대로 늘어남.
- css 설정 : initComplete = JS("function(settings, json) {$(this.api().table().header()).css({ 쓰고 싶은 css });}")
  - background-color: 헤더 색상 지정
  - color : 행 색상 지정 
#### ![image](https://user-images.githubusercontent.com/62974484/215643480-95bd08bb-653a-411c-b85b-830cac29548e.png)
### ex)
```
\```{r Read_Quality, echo=FALSE, warning=FALSE, include=TRUE}

#input <- read_excel("snakemake@input$sequencing_stat")
input <- read.table("./Results/Sequencing_Statistics_Result.xls", header = T)
sort = subset(input, select=c(SampleID,TotalReads,TotalBases,GC_Rate,Q20_MoreBasesRate,Q30_MoreBasesRate))


colnames(sort)= c("Sample ID", "Total reads", "Total bases", "GC rate","Q20 (%)","Q30 (%)")

DT::datatable(
    sort, 
    options = list(
        pageLength =10, 
        autoWidth = TRUE, 
        #scrollX=T,
        initComplete = JS("function(settings, json) {$(this.api().table().header()).css({'background-color': '#50388B', 'color': '#fff'});}")
    )
)

\```
```
