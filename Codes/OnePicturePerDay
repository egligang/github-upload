import requests
import bs4

import tkinter
import tkinter.messagebox
import tkinter.font as tkfont

from PIL import Image
from PIL import ImageTk

response = requests.get('http://wufazhuce.com')
soup = bs4.BeautifulSoup(response.text,'html.parser')
#获取图片并保存到本地
img_url = soup.select('div[class = "item active"]')[0].a.img.get('src')
path = 'D://Picture//01.jpg'
file = open(path,'wb')
r = requests.get(img_url)
file.write(r.content)
file.close()

#获取文字
label_text = soup.select('div [class = "fp-one-cita"]')[0].text.strip()

#创建TK窗口
root=tkinter.Tk()
root.title('每日一图')#标题

#打开可以图片并处理成TK可用的格式
img = Image.open(path)
tkImage = ImageTk.PhotoImage(img)

#创建图片并显示
label = tkinter.Label(root, image = tkImage)
label.pack()

#创建文字
ft = tkfont.Font(family = 'Fixdsys', size = 15, weight = tkfont.BOLD)
label1 = tkinter.Label(root, text = label_text, font = ft)
label1['wraplength'] = 700
label1.pack()

root.mainloop()
