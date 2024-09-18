```zsh
pip3 install requests
pip3 install beautifulsoup4
```

```python title:request_syntax
import requests

response = requests.get('https://workey.codeit.kr/ratings/index')

# get status
print(response)

# get html text
print(response.text)
```

```python title:항상것
import requests

from bs4 import BeautifulSoup

response = requests.get('https://workey.codeit.kr/ratings/index')
rating_page = response.text
# 태그 인식 가능하게
soup = BeautifulSoup(rating_page, 'html.parser')

# 보기좋게 print
print(soup.prettify())
# table태그 가져옴
print(soup.select('table'))
```

```python title:select
import requests
from bs4 import BeautifulSoup

response = requests.get('https://workey.codeit.kr/ratings/index')
rating_page = response.text

soup = BeautifulSoup(rating_page, 'html.parser')

# table태그 가져옴
print(soup.select('table'))

# class: program인것들 가져옴
tags = soup.select('td.program')

# slicing 가능
sliced = tags[:4]

# 맨 첫번째것만 가져옴
first_tag = soup.select_one('td.program')

# text만 가져옴
for tag in tags:
    print(tag.get_text())

# tr[1] 밑에 td 가져옴
tr_tags = soup.select('tr')[1]
td_tags = tags.select('td')

# tr[1] 밑에 모든 태그 가져옴
td_tags = tags.select('*')

# img.src만 가져옴
img_tag = soup.select_one('img')['src']

# img 모든 attributes 가져옴
img_tag = soup.select_one('img').attrs
```

```python title:간결하게
div_tag = soup.select_one('div.data') title = div_tag.select_one('h2').get_text() content = div_tag.select_one('p').get_text() link = div_tag.select_one('a')['href']

# 간결하게 가능

div_tag = soup.select_one('div.data') 
title = div_tag.h2.get_text() 
content = div_tag.p.get_text() 
link = div_tag.a['href']
```

```python title:find,find_all
import requests
from bs4 import BeautifulSoup

response = requests.get('https://workey.codeit.kr/ratings/index')
rating_page = response.text

soup = BeautifulSoup(rating_page, 'html.parser')

# 다가져옴
soup.find_all(True)

# list로 가져올 수 있음
soup.find_all(['p', 'a'])

soup.find_all('tagname', attr1='val1', attr2='val2', ...) 
# soup.find_all('p', id="some-id", class_="some-class")
# soup.find_all('p', id=True, class_=False)


soup.select('div.some-class p')

# 중첩이 안돼서 이렇게 해야됨
div_tag = soup.find('div', class_='some-class') 
div_tag.find_all('p')
```

```python title:모든_text_가져옴(list로)
import requests
from bs4 import BeautifulSoup

response = requests.get('https://workey.codeit.kr/music')
rating_page = response.text
soup = BeautifulSoup(rating_page, 'html.parser')

lis = soup.select('ul.popular__order li')

for li in lis:
    print(list(li.stripped_strings))
```



엑셀로
```zsh
pip3 install openpyxl
```

```python title:export_to_excel
import requests
from bs4 import BeautifulSoup
from openpyxl import Workbook

# create work book
wb = Workbook(write_only=True)
#create work sheet
ws = wb.create_sheet('Sheet1')

response = requests.get('https://workey.codeit.kr/ratings/index')
rating_page = response.text
soup = BeautifulSoup(rating_page, 'html.parser')

# append columns(header)
ws.append(['col1', 'col2', 'col3'])
# 첫번째는 header라 두번째부터 가져옴
for tr_tag in soup.select('tr')[1:]:
	td_tags = tr_tag.select('td')
	row = [
	   td_tags[0].get_text(), # col1
	   td_tags[1].get_text(), # col2
	   td_tags[2].get_text(), # col3
	]
	ws.append(row)
# save
wb.save('workbook_name.xlsx')

```

```python title:export_to_csv
import csv
import requests
from bs4 import BeautifulSoup

# CSV 파일 생성
csv_file = open('file_name.csv', 'w')
csv_writer = csv.writer(csv_file)

# 헤더 행 추가
csv_writer.writerow(['col1', 'col2', 'col3'])

response = requests.get("https://workey.codeit.kr/ratings/index")
rating_page = response.text

soup = BeautifulSoup(rating_page, 'html.parser')

for tr_tag in soup.select('tr')[1:]:
    td_tags = tr_tag.select('td')
    row = [
        td_tags[0].get_text(),
        td_tags[1].get_text(),
        td_tags[2].get_text(),
    ]
    # 데이터 행 추가
    csv_writer.writerow(row)

# CSV 파일 닫기
csv_file.close()

```