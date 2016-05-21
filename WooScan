#coding:utf-8
import requests
import re
wooyun_confirm='http://www.wooyun.org/bugs/new_confirm'
wooyun_url='http://www.wooyun.org'
wooyun_url_result=re.compile('<a href="(/bugs/wooyun-\d*-\d*)">(.*?)</a>')
url_page='http://www.wooyun.org/bugs/new_confirm/page/'
page_id=74#yeshu
out_file=open('wooyun_data.txt','w')
#wooyun_name_result=re.compile('<a href=.*>(.*)</a>')
req_header = {'User-Agent':'Mozilla/5.0 (Windows NT 6.1) AppleWebKit/537.11 (KHTML, like Gecko) Chrome/23.0.1271.64 Safari/537.11',
  'Accept':'text/html;q=0.9,*/*;q=0.8',
  'Accept-Charset':'ISO-8859-1,utf-8;q=0.7,*;q=0.3',
  'Accept-Encoding':'gzip',
 'Connection':'close',
'Referer':None 
                          }


def get_html(url):
	return requests.get(url,headers=req_header).text

def get_data(html):
	wooyun_vul_list=wooyun_url_result.findall(html)
	#wooyun_name_list=wooyun_name_result.findall(html)
	for wooyun_vul_url in wooyun_vul_list:
		wooyun_url_page=wooyun_url+wooyun_vul_url[0]#每页每个漏洞的链接
		vul_str= "%s\t%s"%(wooyun_url_page,wooyun_vul_url[1])
		#out_file.write(wooyun_url_page,wooyun_vul_url[1])
		#print '\033[1;34;40m'
		print vul_str
		#print '\033[0m'
		#out_file.write("%s\t%s"%(wooyun_url_page,wooyun_vul_url[1]))
		#print wooyun_vul_url

def spider_data(url):
	for i in range(1,page_id):
		html=get_html(url+str(i))
		get_data(html)
		print i


if __name__ == '__main__':
	print '\033[1;34;40m'
	spider_data(url_page)
	out_file.close()
