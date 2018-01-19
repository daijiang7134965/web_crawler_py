# web_crawler_py
use webdriver to get data



#coding:utf-8
#读取文件,将文件放入python安装目录里
import csv
#也可以使用with open('rna_seq','rb') as csvfile:
csvfile=file('rna_seq.csv','rb')
reader=csv.reader(csvfile)
column=[row[1:15] for row in reader]
#读取第2到14列元素
#读取全部for line in reader
prient column
#csvfile.close()

#i=0
#gsmlist=[]
#for i,element in enumerate(glist):
  #  str=''.join(glist[i])
	#gsmlist.append(str)



#strcol= ''.join(column)
#list 转化为string
#type(strcol)

#l=column[0]
#l[-1:]    RNA-Seq        l[:1]     12h P. rettgeri heat-killed; Drosophila melanogaster; RNA-Seq     
i=0
glist=[]
for i,element in enumerate(column):
     cir=column[i]
	 sr1=''.join(cir[:1])
	 sr2=''.join(cir[-1:])
    if sr1.startswith('GSM') AND sr2.endswith('RNA-Seq'):
	     glist.append(column[i].retrip(':'))
#筛选GSM和RNA-Seq

i=0
gsmlist=[]
for i,element in enumerate(glist,start=0):
    gsr=''.join(glist[i])
	gs=gsr[0:10]
	gsmlist.append(gs)
#提取GSM
#start 2261

#out=open('gsm.txt','wb')
#out.write(str(gsmurl))
#out.close()
#保存数据为txt 


csvfile=open('glist.csv','wb')
writer=csv.writer(csvfile)
writer.writerows(gsmlist)   #writerows存为多行
csvfile.close()

#with open('gsmlist.csv', 'wb') as csvfile:
    #writer = csv.writer(csvfile, delimiter='\n', quoting=csv.QUOTE_MINIMAL)
	#去逗号保存，writerrow,存为一行，以\n分割
    #writer.writerow(gsmlist)
#保存数据为csv文件

#import requests
#import urllib2
#import re
import time
#from bs4 import BeautifulSoup as bs 
from selenium import webdriver
#打开火狐浏览器 需要V47版本以上的
driver = webdriver.Firefox()
#打开火狐浏览器
url1='https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc='
i=0
sample_name=[]
characteristics=[]
def open_sample():
    for i,element in enumerate(gsmlist):
	        url=url1+gsmlist[i]
	        driver.get(url)
		    time.sleep(2)
		    con=dr.find_element_by_xpath("//table/tbody/tr/td/table[6]/tbody/tr[3]/td[2]/table/tbody/tr/td/table/tbody/tr/td/table[2]/tbody/tr/td/table/tbody/tr[4]/td[2]")
		    text=con.text
		    sample_name.append(text)
		    return sample_name
def open_character():
    for i,element in enumerate(gsmlist):
	        url=url1+gsmlist[i]
	        dr.get(url)
		    time.sleep(2)
	    	con=dr.find_element_by_xpath("//table/tbody/tr/td/table[6]/tbody/tr[3]/td[2]/table/tbody/tr/td/table/tbody/tr/td/table[2]/tbody/tr/td/table/tbody/tr[8]/td[2]   ")
	    	text=con.text.replace('\n',' ')
		    characteristics.append(text)
		    return characteristics
