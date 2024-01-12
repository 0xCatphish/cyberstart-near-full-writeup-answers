import requests

url = 'https://play.cyberstart.com/challenge/W0021/Code'
myobj = 'answer=2457'

x = requests.post(url, data = myobj)

print(x.text)