```python
df['time_data'] = pd.to_datetime(df['time_data'])
# convert object type to datetime

pd.to_timedelta(df['time_data'], unit='D')
# convert number to day(unit='D': return day)


df = pd.read_csv("data/dataFrame.csv", parse_dates=['order_time', 'shipping_time'])
# import할때 한번에 처리할 수도 있음

order_df['order_time'] = order_df['order_time'].dt.strftime('%d %b %Y, %I:%M %p')
# `%d`는 일자, `%B`는 영어로 된 월 이름, `%Y`는 연도(4자리), `%I`는 시간(12시간 기준), `%M`은 분, 마지막으로 `%p`는 오전/오후(AM/PM)


df['time_data'].dt.date
# get datetime data

df['time_data'].dt.year
df['time_data'].dt.month
df['time_data'].dt.day
# get only year/month/day

df['time_data'].dt.dayofweek
# 날짜가 몇번째 요일에 해당하는지(3: 목요일)
```

```python
order_df['order_time'].dt.tz_localize('Asia/Seoul')
# UTC +??:00

import pytz 
for tz in pytz.all_timezones: 
	print(tz)
# get all timezones
```


#### Indexing
```python
df.set_index('time_data').sort_index()
# set index and sort

df.loc['2024']
# get all 2024 data

df.loc['2024-06']
# get all 2024-06 data

df.loc['2015':'2017']
# get 2015/01/01 ~ 2017/12/31 data
```