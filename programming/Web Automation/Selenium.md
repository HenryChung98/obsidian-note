```zsh
pip3 install selenium
```

```python title:setup
# 라이브러리 임포트
from time import sleep
from selenium import webdriver
from selenium.webdriver.common.by import By

# 크롬 드라이버 생성
driver = webdriver.Chrome()
# 사이트 로딩될때까지 기다려줌
driver.implicitly_wait(3)
# 사이트 접속하기
driver.get('https://codeit.kr')
# beautifulSoup처럼 요소받아옴
driver.find_element(by=By.CSS_SELECTOR, value='.class-name')
# 5초 기다리기
sleep(5)

# 크롬 드라이버 종료
driver.quit()
```

```python title:selector
from selenium.webdriver.common.by import By

# css로 찾기
driver.find_element(by=By.CSS_SELECTOR, value='#app > nav > div > a')
# 태그로 찾기
driver.find_element(by=By.TAG_NAME, value='tag_name')
# id로 찾기
driver.find_element(by=By.ID, value='id-name')
# class로 찾기
driver.find_element(by=By.CLASS_NAME, value='class-name')


# 매칭되는 모든 요소 찾기(return list)
driver.find_elements(by=By.CSS_SELECTOR, value='selector')
```

```python title:wait_implicitly/explicitly
from selenium.webdriver.support import expected_conditions as EC
from selenium.webdriver.support.ui import WebDriverWait

# 그냥 기다림
driver.implicitly_wait(3)


# 조건이 충족할때까지 기다림
WebDriverWait(driver, 3).until(EC.element_to_be_clickable((By.CSS_SELECTOR, "#app > nav > div > a")))
```

```python title:창이_안꺼지도록정

# 크롬 옵션 설정
chrome_options = webdriver.ChromeOptions()
chrome_options.add_experimental_option("detach", True)  # 크롬 창이 종료되지 않도록 설정

driver = webdriver.Chrome(options=chrome_options)  # 옵션 적용
```

```python title:e.g.
from time import sleep
from selenium import webdriver
from selenium.webdriver.common.by import By

chrome_options = webdriver.ChromeOptions() 
chrome_options.add_experimental_option("detach", True) 
driver = webdriver.Chrome(options=chrome_options)
driver.implicitly_wait(3)
driver.get('https://workey.codeit.kr/costagram')

wait = WebDriverWait(driver,3)

# 에러 방지
sleep(1)

# beautifulSoup처럼 요소받아옴
# inspector -> right-click that you want to -> copy -> copy selector로 해도 됨

# 클릭(로그인 창 열기)
driver.find_element(by=By.CSS_SELECTOR, value='#app > nav > div > a').click()

# 클릭이 가능해질때까지 기다림
wait.until(EC.element_to_be_clickable((By.CSS_SELECTOR, "#app > nav > div > a")))

# 아이디 입력
driver.find_element(by=By.CSS_SELECTOR, value='.login-container__login-input').send_keys('codeit')

# 비밀번호 입력
driver.find_element(by=By.CSS_SELECTOR, value='.login-container__password-input').send_keys('datascience')

# 로그인 버튼 클릭
driver.find_element(by=By.CSS_SELECTOR, value='.login-container__login-button').click()
```

