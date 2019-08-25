## 개요

각종 주가 데이터를 가져오는 스크립트입니다.


### price.py

다음에서 전 종목 시세를 긁어오는 스크립트입니다.
https://finance.daum.net/domestic/all_quotes

#### 사용예시
```
$ ./price.py
{'name': 'AJ네트웍스', 'symbol': '095570', 'price': 4720.0}
{'name': 'AJ렌터카', 'symbol': '068400', 'price': 10550.0}
{'name': 'AK홀딩스', 'symbol': '006840', 'price': 35150.0}
```

### day.py

네이버에서 일자별 시세를 가져오는 스크립트입니다.


#### 사용예시
```
$ ./day.py -s 005930
005930  43800   44200   43650   43950   4637815
```

#### 활용예시

[GNU Parallel](https://www.gnu.org/software/parallel/)을 이용해 프로세스를 10개 띄어 병렬로 데이터를 가져올 수 있습니다.

```
$ cat /tmp/symbols | parallel --jobs 10 -N300 --pipe ./day.py -s - > `date +%Y-%m-%d`.txt
```  

## minute.py

네이버에서 분단위 시세를 가져오는 스크립트입니다.

#### 사용예시
```
$ ./minute.py -s 005930
005930  44300   406234  09:00
005930  44250   39591   09:01
005930  44200   10132   09:02
005930  44250   26397   09:03
005930  44150   35251   09:04
005930  44250   52259   09:05
005930  44200   47983   09:06
005930  44150   26621   09:07
005930  44150   51956   09:08
005930  44100   31060   09:09
005930  44150   4102    09:10
005930  44100   9177    09:11
005930  44050   53945   09:12
005930  44000   56709   09:13
005930  44000   7189    09:14
005930  44050   17476   09:15
```

#### 활용예시

[GNU Parallel](https://www.gnu.org/software/parallel/)을 이용해 프로세스를 10개 띄어 병렬로 데이터를 가져올 수 있습니다.

```
$ cat /tmp/symbols | parallel --jobs 10 -N300 --pipe ./minute.py -s - > `date +%Y-%m-%d`.txt
```  
