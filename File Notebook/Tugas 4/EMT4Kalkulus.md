# Tugas 5 Aplikasi Komputer


22301244037


Pendidikan Matematika A


# Kalkulus dengan EMT

Materi Kalkulus mencakup di antaranya:


* 
Fungsi (fungsi aljabar, trigonometri, eksponensial, logaritma,
* komposisi fungsi)

* 
Limit Fungsi,

* 
Turunan Fungsi,

* 
Integral Tak Tentu,

* 
Integral Tentu dan Aplikasinya,

* 
Barisan dan Deret (kekonvergenan barisan dan deret).


EMT (bersama Maxima) dapat digunakan untuk melakukan semua perhitungan
di dalam kalkulus, baik secara numerik maupun analitik (eksak).


## Mendefinisikan Fungsi

Terdapat beberapa cara mendefinisikan fungsi pada EMT, yakni:


* 
Menggunakan format nama_fungsi := rumus fungsi (untuk fungsi
* numerik),

* 
Menggunakan format nama_fungsi &amp;= rumus fungsi (untuk fungsi
* simbolik, namun dapat dihitung secara numerik),

* 
Menggunakan format nama_fungsi &amp;&amp;= rumus fungsi (untuk fungsi
* simbolik murni, tidak dapat dihitung langsung),

* 
Fungsi sebagai program EMT.


Setiap format harus diawali dengan perintah function (bukan sebagai
ekspresi).


Berikut adalah adalah beberapa contoh cara mendefinisikan fungsi:


$$f(x)=2x^2+e^{\sin(x)}.$$\>function f(x) := 2\*x^2+exp(sin(x)) // fungsi numerik

\>f(0), f(1), f(pi)


    1
    4.31977682472
    20.7392088022

\>f(a) // tidak dapat dihitung nilainya


    Variable or function a not found.
    Error in:
    f(a) // tidak dapat dihitung nilainya ...
       ^

Silakan Anda plot kurva fungsi di atas!


Berikutnya kita definisikan fungsi:


\>plot2d("2\*x^2+exp(sin(x))"):

\>function g(x) := sqrt(x^2-3\*x)/(x+1)

\>g(3)


    0

\>g(0)


    0

\>g(4) // kompleks, tidak dapat dihitung oleh fungsi numerik


    0.4

Silakan Anda plot kurva fungsi di atas!


\>plot2d("sqrt(x^2-3\*x)/(x+1)"):

\>function f(x) := (x^2-3\*x+1)

\>f(g(0)) // komposisi fungsi


    1

\>g(f(5))


    0.781735959971

\>function h(x) := f(g(x)) // definisi komposisi fungsi 

\>h(5) // sama dengan f(g(5))


    -0.303361052306

Silakan Anda plot kurva fungsi komposisi fungsi f dan g:


dan


bersama-sama kurva fungsi f dan g dalam satu bidang koordinat.


\>plot2d("h(x)"):

\>f(0:10) // nilai-nilai f(0), f(1), f(2), ..., f(10)


    [0,  1,  8,  27,  64,  125,  216,  343,  512,  729,  1000]

\>fmap(0:10) // sama dengan f(0:10), berlaku untuk semua fungsi


    [0,  1,  8,  27,  64,  125,  216,  343,  512,  729,  1000]

\>gmap(200:210)


    [0.987534,  0.987596,  0.987657,  0.987718,  0.987778,  0.987837,
    0.987896,  0.987954,  0.988012,  0.988069,  0.988126]

Misalkan kita akan mendefinisikan fungsi


Fungsi tersebut tidak dapat didefinisikan sebagai fungsi numerik
secara "inline" menggunakan format :=, melainkan didefinisikan sebagai
program. Perhatikan, kata "map" digunakan agar fungsi dapat menerima
vektor sebagai input, dan hasilnya berupa vektor. Jika tanpa kata
"map" fungsinya hanya dapat menerima input satu nilai.


\>function map f(x) ...


      if x>0 then return x^3
      else return x^2
      endif;
    endfunction
</pre>
\>f(1)


    1

\>f(-2)


    4

\>f(-3)


    9

\>f(-5:5)


    [25,  16,  9,  4,  1,  0,  1,  8,  27,  64,  125]

\>aspect(1.5); plot2d("f(x)",-5,5):

\>function f(x) &= 2\*E^x // fungsi simbolik


    
                                        x
                                     2 E
    

\>$f(a) // nilai fungsi secara simbolik

\>f(E) // nilai fungsi berupa bilangan desimal


    30.308524483

\>$f(E), $float(%)

\>function g(x) &= 3\*x+1


    
                                   3 x + 1
    

\>function h(x) &= f(g(x)) // komposisi fungsi


    
                                     3 x + 1
                                  2 E
    

\>plot2d("h(x)",-1,1):


# Latihan

Bukalah buku Kalkulus. Cari dan pilih beberapa (paling sedikit 5 fungsi berbeda
tipe/bentuk/jenis) fungsi dari buku tersebut, kemudian definisikan fungsi-fungsi tersebut dan
komposisinya di EMT pada baris-baris perintah berikut (jika perlu tambahkan lagi). Untuk setiap
fungsi, hitung beberapa nilainya, baik untuk satu nilai maupun vektor. Gambar grafik
fungsi-fungsi tersebut dan komposisi-komposisi 2 fungsi.


Juga, carilah fungsi beberapa (dua) variabel. Lakukan hal sama seperti di atas.


\>function k(x):= x^3-x^2+2\*x-3

\>f(2)


    14.7781121979

\>function j(x):= sqrt(x-1)/3x

\>j(2)


    0.166666666667

\>plot2d("k(x)-j(x)"):

\>fmap(0:20)


    [2,  5.43656,  14.7781,  40.1711,  109.196,  296.826,  806.858,
    2193.27,  5961.92,  16206.2,  44052.9,  119748,  325510,  884827,
    2.40521e+06,  6.53803e+06,  1.77722e+07,  4.83099e+07,  1.3132e+08,
    3.56965e+08,  9.7033e+08]

\>gmap(0:100)


    [1,  4,  7,  10,  13,  16,  19,  22,  25,  28,  31,  34,  37,  40,  43,
    46,  49,  52,  55,  58,  61,  64,  67,  70,  73,  76,  79,  82,  85,
    88,  91,  94,  97,  100,  103,  106,  109,  112,  115,  118,  121,
    124,  127,  130,  133,  136,  139,  142,  145,  148,  151,  154,  157,
    160,  163,  166,  169,  172,  175,  178,  181,  184,  187,  190,  193,
    196,  199,  202,  205,  208,  211,  214,  217,  220,  223,  226,  229,
    232,  235,  238,  241,  244,  247,  250,  253,  256,  259,  262,  265,
    268,  271,  274,  277,  280,  283,  286,  289,  292,  295,  298,  301]

\>function map f(x)


    if x<=0 then return x^2
    else return x^3
    endif:
    endfunction
</pre>
\>f(2)


    8

\>f(10:20)


    [1000,  1331,  1728,  2197,  2744,  3375,  4096,  4913,  5832,  6859,
    8000]

\>f(-1)


    1

\>aspect(3,4), plot2d("f(x)",10,20):

\>function u(x)&=sin(x)+1


    
                                  sin(x) + 1
    

\>u(2)


    1.90929742683

\>u(32)


    1.55142668124

\>function a(x)&= sin(x)-cos(x-2)


    
                             sin(x) - cos(x - 2)
    

\>a(5)


    0.0310682219373

\>plot2d("sin(x)-cos(x-2)"):

\>function d(x)&= 2\*x^2-3\*x-4


    
                                   2
                                2 x  - 3 x - 4
    

\>d(2)


    -2

\>plot2d("2\*x^2-3\*x-4"):


# Menghitung Limit

Perhitungan limit pada EMT dapat dilakukan dengan menggunakan fungsi Maxima, yakni "limit".
Fungsi "limit" dapat digunakan untuk menghitung limit fungsi dalam bentuk ekspresi maupun fungsi
yang sudah didefinisikan sebelumnya. Nilai limit dapat dihitung pada sebarang nilai atau pada tak
hingga (-inf, minf, dan inf). Limit kiri dan limit kanan juga dapat dihitung, dengan cara memberi
opsi "plus" atau "minus". Hasil limit dapat berupa nilai, "und" (tak definisi), "ind" (tak tentu
namun terbatas), "infinity" (kompleks tak hingga).


Perhatikan beberapa contoh berikut. Perhatikan cara menampilkan perhitungan secara lengkap, tidak
hanya menampilkan hasilnya saja.


\>$showev('limit(sqrt(x^2-3\*x)/(x+1),x,inf))

\>$limit((x^3-13\*x^2+51\*x-63)/(x^3-4\*x^2-3\*x+18),x,3)


maxima: 'limit((x^3-13*x^2+51*x-63)/(x^3-4*x^2-3*x+18),x,3)=limit((x^3-13*x^2+51*x-63)/(x^3-4*x^2-3*x+18),x,3)


Fungsi tersebut diskontinu di titik x=3. Berikut adalah grafik
fungsinya.


\>aspect(1.5); plot2d("(x^3-13\*x^2+51\*x-63)/(x^3-4\*x^2-3\*x+18)",0,4); plot2d(3,-4/5,\>points,style="ow",\>add):

\>$limit(2\*x\*sin(x)/(1-cos(x)),x,0)


maxima: 'limit(2*x*sin(x)/(1-cos(x)),x,0)=limit(2*x*sin(x)/(1-cos(x)),x,0)


Fungsi tersebut diskontinu di titik x=0. Berikut adalah grafik fungsinya.


\>plot2d("2\*x\*sin(x)/(1-cos(x))",-pi,pi); plot2d(0,4,\>points,style="ow",\>add):

\>$limit(cot(7\*h)/cot(5\*h),h,0)


maxima: showev('limit(cot(7*h)/cot(5*h),h,0))


Fungsi tersebut juga diskontinu (karena tidak terdefinisi) di x=0. Berikut adalah grafiknya.


\>plot2d("cot(7\*x)/cot(5\*x)",-0.001,0.001); plot2d(0,5/7,\>points,style="ow",\>add):

\>$showev('limit(1/(2\*x-1),x,0))


Tunjukkan limit tersebut dengan grafik, seperti contoh-contoh sebelumnya.


\>plot2d("1/2\*x-1",-0.001,0.001); plot2d(0,-1,\>points,style="owo",\>add):

\>$showev('limit((x^2-3\*x-10)/(x-5),x,5))


Tunjukkan limit tersebut dengan grafik, seperti contoh-contoh sebelumnya.


\>plot2d("(x^2-3\*x-10)/(x-5)",-0,5); plot2d(0,7,\>points,style="ow",\>add):

\>$showev('limit(sqrt(x^2+x)-x,x,inf))


Tunjukkan limit tersebut dengan grafik, seperti contoh-contoh sebelumnya.


\>plot2d("sqrt(x^2+x)",-0.001,0.001,); plot2d(0,1/2,\>points,style="ow",\>add):

\>$showev('limit(abs(x-1)/(x-1),x,1,minus))


Hitung limit di atas untuk x menuju 1 dari kanan.


Tunjukkan limit tersebut dengan grafik, seperti contoh-contoh
sebelumnya.


\>plot2d("abs(x-1)/(x-1)",-0.001,1); plot2d(0,-1,\>points,style="ow",\>add):

\>$showev('limit(sin(x)/x,x,0))

\>plot2d("sin(x)/x",-pi,pi); plot2d(0,1,\>points,style="ow",\>add):

\>$showev('limit(sin(x^3)/x,x,0))


Tunjukkan limit tersebut dengan grafik, seperti contoh-contoh
sebelumnya.


\>plot2d("sin(x^3)/x",-0.001,0.001); plot2d(0,,\>points,style="ow",\>add):

\>$showev('limit(log(x), x, minf))

\>plot2d("log(x)",-0.001,0.001); plot2d(0,0,\>points,style="ow",\>add):

\>$showev('limit((-2)^x,x, inf))

\>plot2d("-2^x",-0.001,0.001); plot2d(0,0,\>points,style="ow",\>add):

\>$showev('limit(t-sqrt(2-t),t,2,minus))

\>plot2d("x-sqrt(2-x)",-0.001,0.002); plot2d(0,-2,\>points,style="ow",\>add):

\>$showev('limit(t-sqrt(2-t),t,2,plus))

\>$showev('limit(t-sqrt(2-t),t,5,plus)) // Perhatikan hasilnya

\>plot2d("x-sqrt(2-x)",0,2):

\>$showev('limit((x^2-9)/(2\*x^2-5\*x-3),x,3))


Tunjukkan limit tersebut dengan grafik, seperti contoh-contoh sebelumnya.


\>plot2d("(x^2-9)/(2\*x^2-5\*x-3)",-0.001,0.003); plot2d(0,6/7,\>points,style="ow",\>add):

\>$showev('limit((1-cos(x))/x,x,0))


Tunjukkan limit tersebut dengan grafik, seperti contoh-contoh sebelumnya.


\>plot2d("1-cos(x)/x",-pi,pi); plot2d(0,0,\>points,style="ow",\>add):

\>$showev('limit((x^2+abs(x))/(x^2-abs(x)),x,0))


Tunjukkan limit tersebut dengan grafik, seperti contoh-contoh sebelumnya.


\>plot2d("x^2+abs(x)/(x^2-abs(x))",-0.001,0.001); plot2d(-1,0,\>points,style="ow",\>add):

\>$showev('limit((1+1/x)^x,x,inf))

\>plot2d("(1+1/x)^x",0,1000):

\>$showev('limit((1+k/x)^x,x,inf))

\>$showev('limit((1+x)^(1/x),x,0))


Tunjukkan limit tersebut dengan grafik, seperti contoh-contoh sebelumnya.


\>plot2d("(1+x)^(1/x)",0,0):

\>$showev('limit((x/(x+k))^x,x,inf))

\>$showev('limit((E^x-E^2)/(x-2),x,2))


Tunjukkan limit tersebut dengan grafik, seperti contoh-contoh sebelumnya.


\>plot2d("(E^x-E^2)/(x-2)",0,2):

\>$showev('limit(sin(1/x),x,0))

\>plot2d("sin(1/x)",-pi,pi):

\>$showev('limit(sin(1/x),x,inf))

\>plot2d("sin(1/x)",-0.001,0.001):


# Latihan

Bukalah buku Kalkulus. Cari dan pilih beberapa (paling sedikit 5 fungsi berbeda
tipe/bentuk/jenis) fungsi dari buku tersebut, kemudian definisikan di EMT pada
baris-baris perintah berikut (jika perlu tambahkan lagi). Untuk setiap fungsi, hitung
nilai limit fungsi tersebut di beberapa nilai dan di tak hingga. Gambar grafik fungsi
tersebut untuk mengkonfirmasi nilai-nilai limit tersebut.


\>$showev('limit(sin(1/x)-cos(x),x,inf))

\>plot2d("sin(1/x)-cos(x)",-pi,pi):

\>$showev('limit((2\*x^2-3\*x-4)/(x^2-3),x,inf))

\>plot2d("(2\*x^2-3\*x-4)/(x^2-3)",0,1000):

\>$showev('limit(ln(x),x,inf))

\>plot2d("ln(x)",0,1000):

\>$showev('limit(log(x)+cos(x),x,inf))

\>plot2d("log(x)+cos(x)",0,1000):

\>$showev('limit(sin(x)-cos(x)+tan(x),x,pi))

\>plot2d("sin(x)-cos(x)+tan(x)",0,1):

\>$showev('limit(2/x+3\*x^3+2\*x^2-3\*x,x,x))

\>plot2d("2/x+3\*x^3+2\*x^2-3\*x",-1000,1000):


# Turunan Fungsi

Definisi turunan:


Berikut adalah contoh-contoh menentukan turunan fungsi dengan
menggunakan definisi turunan (limit).


\>$showev('limit(((x+h)^2-x^2)/h,h,0)) // turunan x^2

\>p &= expand((x+h)^2-x^2)|simplify; $p //pembilang dijabarkan dan disederhanakan

\>q &=ratsimp(p/h); $q // ekspresi yang akan dihitung limitnya disederhanakan

\>$limit(q,h,0) // nilai limit sebagai turunan

\>$showev('limit(((x+h)^n-x^n)/h,h,0)) // turunan x^n


Mengapa hasilnya seperti itu? Tuliskan atau tunjukkan bahwa hasil limit tersebut
benar, sehingga benar turunan fungsinya benar.  Tulis penjelasan Anda di komentar
ini.


Sebagai petunjuk, ekspansikan (x+h)^n dengan menggunakan teorema binomial.


\>$showev('limit((sin(x+h)-sin(x))/h,h,0)) // turunan sin(x)


Mengapa hasilnya seperti itu? Tuliskan atau tunjukkan bahwa hasil limit tersebut


benar, sehingga benar turunan fungsinya benar.  Tulis penjelasan Anda di komentar
ini.


Sebagai petunjuk, ekspansikan sin(x+h) dengan menggunakan rumus jumlah dua sudut.


\>$showev('limit((log(x+h)-log(x))/h,h,0)) // turunan log(x)


Mengapa hasilnya seperti itu? Tuliskan atau tunjukkan bahwa hasil limit tersebut


benar, sehingga benar turunan fungsinya benar.  Tulis penjelasan Anda di komentar
ini.


Sebagai petunjuk, gunakan sifat-sifat logaritma dan hasil limit pada bagian
sebelumnya di atas.


\>$showev('limit((1/(x+h)-1/x)/h,h,0)) // turunan 1/x

\>$showev('limit((E^(x+h)-E^x)/h,h,0)) // turunan f(x)=e^x


    Answering "Is x an integer?" with "integer"
    Answering "Is x an integer?" with "integer"
    Answering "Is x an integer?" with "integer"
    Answering "Is x an integer?" with "integer"
    Answering "Is x an integer?" with "integer"
    Maxima is asking
    Acceptable answers are: yes, y, Y, no, n, N, unknown, uk
    Is x an integer?
    
    Use assume!
    Error in:
     $showev('limit((E^(x+h)-E^x)/h,h,0)) // turunan f(x)=e^x ...
                                         ^

Maxima bermasalah dengan limit:


Oleh karena itu diperlukan trik khusus agar hasilnya benar.


\>$showev('limit((E^h-1)/h,h,0))

\>$showev('factor(E^(x+h)-E^x))

\>$showev('limit(factor((E^(x+h)-E^x)/h),h,0)) // turunan f(x)=e^x

\>function f(x) &= x^x


    
                                       x
                                      x
    

\>$showev('limit(f(x),x,0))


Silakan Anda gambar kurva


\>plot2d("x^x",-100,100):


## Turunan



Definisi turunan:


Berikut adalah contoh-contoh menentukan turunan fungsi dengan
menggunakan definisi turunan (limit).


\>$showev('limit((f(x+h)-f(x))/h,h,0)) // turunan f(x)=x^x


Di sini Maxima juga bermasalah terkait limit:


Dalam hal ini diperlukan asumsi nilai x.


\>&assume(x\>0); $showev('limit((f(x+h)-f(x))/h,h,0)) // turunan f(x)=x^x


Mengapa hasilnya seperti itu? Tuliskan atau tunjukkan bahwa hasil
limit tersebut benar, sehingga benar


turunan fungsinya benar. Tulis penjelasan Anda di komentar ini.


Sebagai petunjuk, ekspansikan (x+h)ˆn dengan menggunakan teorema
binomial.




Untuk




Dengan




maka




Jadi, terbukti benar bahwa


\>&forget(x\>0) // jangan lupa, lupakan asumsi untuk kembali ke semula


    
                                   [x &gt; 0]
    

\>&forget(x<0)


    
                                   [x &lt; 0]
    

\>&facts()


    
                                   [x &gt; 0]
    

\>$showev('limit((asin(x+h)-asin(x))/h,h,0)) // turunan arcsin(x)


Mengapa hasilnya seperti itu? Tuliskan atau tunjukkan bahwa hasil limit tersebut benar, sehingga
benar turunan fungsinya benar. Tulis penjelasan Anda di komentar ini.


\>$showev('limit((tan(x+h)-tan(x))/h,h,0)) // turunan tan(x)


Mengapa hasilnya seperti itu? Tuliskan atau tunjukkan bahwa hasil limit tersebut benar, sehingga
benar turunan fungsinya benar. Tulis penjelasan Anda di komentar ini.


\>function f(x) &= sinh(x) // definisikan f(x)=sinh(x)


    
                                   sinh(x)
    

\>function df(x) &= limit((f(x+h)-f(x))/h,h,0); $df(x) // df(x) = f'(x)


Hasilnya adalah cosh(x), karena


\>plot2d(["f(x)","df(x)"],-pi,pi,color=[blue,red]):

\>function f(x) &= sin(3\*x^5+7)^2


    
                                   2        5
                                sin (7 + 3 x )
    

\>diff(f,3), diffc(f,3)


    1198.32948904
    1198.72863721

Apakah perbedaan diff dan diffc?


\>$showev('diff(f(x),x))

\>$% with x=3

\>$float(%)

\>plot2d(f,0,3.1):

\>function f(x) &=5\*cos(2\*x)-2\*x\*sin(2\*x) // mendifinisikan fungsi f


    
                          5 cos(2 x) - 2 x sin(2 x)
    

\>function df(x) &=diff(f(x),x) // fd(x) = f'(x)


    
                         - 4 x cos(2 x) - 12 sin(2 x)
    

\>$'f(1)=f(1), $float(f(1)), $'f(2)=f(2), $float(f(2)) // nilai f(1) dan f(2)

\>xp=solve("df(x)",1,2,0) // solusi f'(x)=0 pada interval [1, 2]


    1.35822987384

\>df(xp), f(xp) // cek bahwa f'(xp)=0 dan nilai ekstrim di titik tersebut


    0
    -5.67530133759

\>plot2d(["f(x)","df(x)"],0,2\*pi,color=[blue,red]): //grafik fungsi dan turunannya


Perhatikan titik-titik "puncak" grafik y=f(x) dan nilai turunan pada saat grafik fungsinya mencapai titik "puncak" tersebut.


    

    

# Integral

EMT dapat digunakan untuk menghitung integral, baik integral tak tentu maupun
integral tentu. Untuk integral tak tentu (simbolik) sudah tentu EMT menggunakan
Maxima, sedangkan untuk perhitungan integral tentu EMT sudah menyediakan beberapa
fungsi yang mengimplementasikan algoritma kuadratur (perhitungan integral tentu
menggunakan metode numerik).


Pada notebook ini akan ditunjukkan perhitungan integral tentu dengan menggunakan
Teorema Dasar Kalkulus:


Fungsi untuk menentukan integral adalah integrate. Fungsi ini dapat digunakan untuk
menentukan, baik integral tentu maupun tak tentu (jika fungsinya memiliki
antiderivatif). Untuk perhitungan integral tentu fungsi integrate menggunakan metode
numerik (kecuali fungsinya tidak integrabel, kita tidak akan menggunakan metode ini).


\>$showev('integrate(x^n,x))


    Answering "Is n equal to -1?" with "no"

\>$showev('integrate(1/(1+x),x))

\>$showev('integrate(1/(1+x^2),x))

\>$showev('integrate(1/sqrt(1-x^2),x))

\>$showev('integrate(sin(x),x,0,pi))

\>plot2d("sin(x)",0,2\*pi):

\>$showev('integrate(sin(x),x,a,b))

\>$showev('integrate(x^n,x,a,b))


    Answering "Is n positive, negative or zero?" with "positive"

\>$showev('integrate(x^2\*sqrt(2\*x+1),x))

\>$showev('integrate(x^2\*sqrt(2\*x+1),x,0,2))

\>$ratsimp(%)

\>$showev('integrate((sin(sqrt(x)+a)\*E^sqrt(x))/sqrt(x),x,0,pi^2))

\>$factor(%)

\>function map f(x) &= E^(-x^2)


    
                                        2
                                     - x
                                    E
    

\>$showev('integrate(f(x),x))


Fungsi f tidak memiliki antiturunan, integralnya masih memuat integral
lain.


Kita tidak dapat menggunakan teorema Dasar kalkulus untuk menghitung
integral tentu fungsi tersebut jika semua batasnya berhingga. Dalam
hal ini dapat digunakan metode numerik (rumus kuadratur).


Misalkan kita akan menghitung:


maxima: 'integrate(f(x),x,0,pi)


\>x=0:0.1:pi-0.1; plot2d(x,f(x+0.1),\>bar); plot2d("f(x)",0,pi,\>add):


Integral tentu


maxima: 'integrate(f(x),x,0,pi)


dapat dihampiri dengan jumlah luas persegi-persegi panjang di bawah kurva y=f(x)
tersebut. Langkah-langkahnya adalah sebagai berikut.


\>t &= makelist(a,a,0,pi-0.1,0.1); // t sebagai list untuk menyimpan nilai-nilai x

\>fx &= makelist(f(t[i]+0.1),i,1,length(t)); // simpan nilai-nilai f(x)

\>// jangan menggunakan x sebagai list, kecuali Anda pakar Maxima!


Hasilnya adalah:


maxima: 'integrate(f(x),x,0,pi) = 0.1*sum(fx[i],i,1,length(fx))


Jumlah tersebut diperoleh dari hasil kali lebar sub-subinterval (=0.1)
dan jumlah nilai-nilai f(x) untuk x = 0.1, 0.2, 0.3, ..., 3.2.


\>0.1\*sum(f(x+0.1)) // cek langsung dengan perhitungan numerik EMT


    0.836219610253

Untuk mendapatkan nilai integral tentu yang mendekati nilai sebenarnya, lebar
sub-intervalnya dapat diperkecil lagi, sehingga daerah di bawah kurva tertutup
semuanya, misalnya dapat digunakan lebar subinterval 0.001. (Silakan dicoba!)


Meskipun Maxima tidak dapat menghitung integral tentu fungsi tersebut untuk
batas-batas yang berhingga, namun integral tersebut dapat dihitung secara eksak jika
batas-batasnya tak hingga. Ini adalah salah satu keajaiban di dalam matematika, yang
terbatas tidak dapat dihitung secara eksak, namun yang tak hingga malah dapat
dihitung secara eksak.


\>$showev('integrate(f(x),x,0,inf))


Tunjukkan kebenaran hasil di atas!


Berikut adalah contoh lain fungsi yang tidak memiliki antiderivatif, sehingga integral tentunya hanya
dapat dihitung dengan metode numerik.


\>function f(x) &= x^x


    
                                       x
                                      x
    

\>$showev('integrate(f(x),x,0,1))

\>x=0:0.1:1-0.01; plot2d(x,f(x+0.01),\>bar); plot2d("f(x)",0,1,\>add):


Maxima gagal menghitung integral tentu tersebut secara langsung menggunakan perintah
integrate. Berikut kita lakukan seperti contoh sebelumnya untuk mendapat hasil atau
pendekatan nilai integral tentu tersebut.


\>t &= makelist(a,a,0,1-0.01,0.01);

\>fx &= makelist(f(t[i]+0.01),i,1,length(t));


maxima: 'integrate(f(x),x,0,1) = 0.01*sum(fx[i],i,1,length(fx))


Apakah hasil tersebut cukup baik? perhatikan gambarnya.


\>function f(x) &= sin(3\*x^5+7)^2


    
                                   2        5
                                sin (7 + 3 x )
    

\>integrate(f,0,1)


    0.542581176074

\>&showev('integrate(f(x),x,0,1))


    
             1                           1              pi
            /                      gamma(-) sin(14) sin(--)
            [     2        5             5              10
            I  sin (7 + 3 x ) dx = ------------------------
            ]                                  1/5
            /                              10 6
             0
                    4/5                    1
     - (- 60 + ((- 6    I gamma_incomplete(-, - 6 I)
                                           5
        4/5                    1
     + 6    I gamma_incomplete(-, 6 I)) cos(14)
                               5
         4/5                  1            4/5                  1
     + (6    gamma_incomplete(-, - 6 I) + 6    gamma_incomplete(-, 6 I))
                              5                                 5
                  pi
     sin(14)) sin(--))/120
                  10
    

\>&float(%)


    
             1.0
            /
            [       2            5
            I    sin (7.0 + 3.0 x ) dx = 
            ]
            /
             0.0
    0.09820784258795788 - 0.008333333333333333
     (- 60.0 + 0.3090169943749474 (0.9906073556948704
     (4.192962712629476 gamma__incomplete(0.2, - 6.0 I)
     + 4.192962712629476 gamma__incomplete(0.2, 6.0 I))
     + 0.1367372182078336 (- 4.192962712629476 I
     gamma__incomplete(0.2, - 6.0 I) + 4.192962712629476 I
     gamma__incomplete(0.2, 6.0 I))))
    

\>$showev('integrate(x\*exp(-x),x,0,1)) // Integral tentu (eksak)


# Aplikasi Integral Tentu

\>plot2d("x^3-x",-0.1,1.1); plot2d("-x^2",\>add);  ...  
\>   b=solve("x^3-x+x^2",0.5); x=linspace(0,b,200); xi=flipx(x); ...  
\>   plot2d(x|xi,x^3-x|-xi^2,\>filled,style="|",fillcolor=1,\>add): // Plot daerah antara 2 kurva

\>a=solve("x^3-x+x^2",0), b=solve("x^3-x+x^2",1) // absis titik-titik potong kedua kurva


    0
    0.61803398875

\>integrate("(-x^2)-(x^3-x)",a,b) // luas daerah yang diarsir


    0.0758191713542

Hasil tersebut akan kita bandingkan dengan perhitungan secara analitik.


\>a &= solve((-x^2)-(x^3-x),x); $a // menentukan absis titik potong kedua kurva secara eksak

\>$showev('integrate(-x^2-x^3+x,x,0,(sqrt(5)-1)/2)) // Nilai integral secara eksak

\>$float(%)


## Panjang Kurva

Hitunglah panjang kurva berikut ini dan luas daerah di dalam kurva tersebut.


dengan


\>t=linspace(0,2pi,1000); r=1+sin(3\*t)/2; x=r\*cos(t); y=r\*sin(t); ...  
\>   plot2d(x,y,\>filled,fillcolor=red,style="/",r=1.5): // Kita gambar kurvanya terlebih dahulu

\>function r(t) &= 1+sin(3\*t)/2; $'r(t)=r(t)

\>function fx(t) &= r(t)\*cos(t); $'fx(t)=fx(t)

\>function fy(t) &= r(t)\*sin(t); $'fy(t)=fy(t)

\>function ds(t) &= trigreduce(radcan(sqrt(diff(fx(t),t)^2+diff(fy(t),t)^2))); $'ds(t)=ds(t)


    Maxima said:
    diff: second argument must be a variable; found errexp1
     -- an error. To debug this try: debugmode(true);
    
    Error in:
    ... e(radcan(sqrt(diff(fx(t),t)^2+diff(fy(t),t)^2))); $'ds(t)=ds(t ...
                                                         ^

\>$integrate(ds(x),x,0,2\*pi) //panjang (keliling) kurva


Maxima gagal melakukan perhitungan eksak integral tersebut.


Berikut kita hitung integralnya secara umerik dengan perintah EMT.


\>integrate("ds(x)",0,2\*pi)


    Function ds not found.
    Try list ... to find functions!
    Error in expression: ds(x)
     %mapexpression1:
        return expr(x,args());
    Error in map.
     %evalexpression:
        if maps then return %mapexpression1(x,f$;args());
    gauss:
        if maps then y=%evalexpression(f$,a+h-(h*xn)',maps;args());
    adaptivegauss:
        t1=gauss(f$,c,c+h;args(),=maps);
    Try "trace errors" to inspect local variables after errors.
    integrate:
        return adaptivegauss(f$,a,b,eps*1000;args(),=maps);

Spiral Logaritmik


\>a=0.1; plot2d("exp(a\*x)\*cos(x)","exp(a\*x)\*sin(x)",r=2,xmin=0,xmax=2\*pi):

\>&kill(a) // hapus expresi a


    
                                     done
    

\>function fx(t) &= exp(a\*t)\*cos(t); $'fx(t)=fx(t)

\>function fy(t) &= exp(a\*t)\*sin(t); $'fy(t)=fy(t)

\>function df(t) &= trigreduce(radcan(sqrt(diff(fx(t),t)^2+diff(fy(t),t)^2))); $'df(t)=df(t)


    Maxima said:
    diff: second argument must be a variable; found errexp1
     -- an error. To debug this try: debugmode(true);
    
    Error in:
    ... e(radcan(sqrt(diff(fx(t),t)^2+diff(fy(t),t)^2))); $'df(t)=df(t ...
                                                         ^

\>S &=integrate(df(t),t,0,2\*%pi); $S // panjang kurva (spiral)


    Maxima said:
    defint: variable of integration cannot be a constant; found errexp1
     -- an error. To debug this try: debugmode(true);
    
    Error in:
    S &amp;=integrate(df(t),t,0,2*%pi); $S // panjang kurva (spiral) ...
                                  ^

\>S(a=0.1) // Panjang kurva untuk a=0.1


    Function S not found.
    Try list ... to find functions!
    Error in:
    S(a=0.1) // Panjang kurva untuk a=0.1 ...
            ^

Soal:


Tunjukkan bahwa keliling lingkaran dengan jari-jari r adalah K=2.pi.r.


Berikut adalah contoh menghitung panjang parabola.


\>plot2d("x^2",xmin=-1,xmax=1):

\>$showev('integrate(sqrt(1+diff(x^2,x)^2),x,-1,1))

\>$float(%)

\>x=-1:0.2:1; y=x^2; plot2d(x,y);  ...  
\>     plot2d(x,y,points=1,style="o#",add=1):


Panjang tersebut dapat dihampiri dengan menggunakan jumlah panjang ruas-ruas garis yang menghubungkan titik-titik pada parabola
tersebut.


\>i=1:cols(x)-1; sum(sqrt((x[i+1]-x[i])^2+(y[i+1]-y[i])^2))


    2.95191957027

Hasilnya mendekati panjang yang dihitung secara eksak. Untuk mendapatkan hampiran yang cukup akurat, jarak antar titik dapat
diperkecil, misalnya 0.1, 0.05, 0.01, dan seterusnya. Cobalah Anda ulangi perhitungannya dengan nilai-nilai tersebut.


## Koordinat Kartesius

Berikut diberikan contoh perhitungan panjang kurva menggunakan koordinat Kartesius. Kita akan hitung panjang kurva dengan
persamaan implisit:


\>z &= x^3+y^3-3\*x\*y; $z

\>plot2d(z,r=2,level=0,n=100):


Kita tertarik pada kurva di kuadran pertama.


\>plot2d(z,a=0,b=2,c=0,d=2,level=[-10;0],n=100,contourwidth=3,style="/"):


Kita selesaikan persamaannya untuk x.


\>$z with y=l\*x, sol &= solve(%,x); $sol


Kita gunakan solusi tersebut untuk mendefinisikan fungsi dengan Maxima.


\>function f(l) &= rhs(sol[1]); $'f(l)=f(l)


Fungsi tersebut juga dapat digunaka untuk menggambar kurvanya. Ingat, bahwa fungsi tersebut adalah nilai x dan nilai y=l*x, yakni
x=f(l) dan y=l*f(l).


\>plot2d(&f(x),&x\*f(x),xmin=-0.5,xmax=2,a=0,b=2,c=0,d=2,r=1.5):


Elemen panjang kurva adalah:


\>function ds(l) &= ratsimp(sqrt(diff(f(l),l)^2+diff(l\*f(l),l)^2)); $'ds(l)=ds(l)

\>$integrate(ds(l),l,0,1)


Integral tersebut tidak dapat dihitung secara eksak menggunakan Maxima. Kita hitung integral etrsebut secara numerik dengan Euler.
Karena kurva simetris, kita hitung untuk nilai variabel integrasi dari 0 sampai 1, kemudian hasilnya dikalikan 2. 


\>2\*integrate("ds(x)",0,1)


    4.91748872168

\>2\*romberg(&ds(x),0,1)// perintah Euler lain untuk menghitung nilai hampiran integral yang sama


    4.91748872168

Perhitungan di datas dapat dilakukan untuk sebarang fungsi x dan y dengan mendefinisikan fungsi EMT, misalnya kita beri nama
panjangkurva. Fungsi ini selalu memanggil Maxima untuk menurunkan fungsi yang diberikan.


\>function panjangkurva(fx,fy,a,b) ...


    ds=mxm("sqrt(diff(@fx,x)^2+diff(@fy,x)^2)");
    return romberg(ds,a,b);
    endfunction
</pre>
\>panjangkurva("x","x^2",-1,1) // cek untuk menghitung panjang kurva parabola sebelumnya


    2.95788571509

Bandingkan dengan nilai eksak di atas.


\>2\*panjangkurva(mxm("f(x)"),mxm("x\*f(x)"),0,1) // cek contoh terakhir, bandingkan hasilnya!


    4.91748872168

Kita hitung panjang spiral Archimides berikut ini dengan fungsi tersebut.


\>plot2d("x\*cos(x)","x\*sin(x)",xmin=0,xmax=2\*pi,square=1):

\>panjangkurva("x\*cos(x)","x\*sin(x)",0,2\*pi)


    21.2562941482

Berikut kita definisikan fungsi yang sama namun dengan Maxima, untuk perhitungan eksak.


\>&kill(ds,x,fx,fy)


    
                                     done
    

\>function ds(fx,fy) &&= sqrt(diff(fx,x)^2+diff(fy,x)^2)


    
                               2              2
                      sqrt(diff (fx, x) + diff (fy, x))
    

\>sol &= ds(x\*cos(x),x\*sin(x)); $sol // Kita gunakan untuk menghitung panjang kurva terakhir di atas

\>$sol | trigreduce | expand, $integrate(%,x,0,2\*pi), %()


    21.2562941482

Hasilnya sama dengan perhitungan menggunakan fungsi EMT.


Berikut adalah contoh lain penggunaan fungsi Maxima tersebut.


\>plot2d("3\*x^2-1","3\*x^3-1",xmin=-1/sqrt(3),xmax=1/sqrt(3),square=1):

\>sol &= radcan(ds(3\*x^2-1,3\*x^3-1)); $sol

\>$showev('integrate(sol,x,0,1/sqrt(3))), $2\*float(%) // panjang kurva di atas


## Sikloid

Berikut kita akan menghitung panjang kurva lintasan (sikloid) suatu titik pada lingkaran yang berputar ke kanan pada permukaan
datar. Misalkan jari-jari lingkaran tersebut adalah r. Posisi titik pusat lingkaran pada saat t adalah:


Misalkan posisi titik pada lingkaran tersebut mula-mula (0,0) dan posisinya pada saat t adalah:


Berikut kita plot lintasan tersebut dan beberapa posisi lingkaran ketika t=0, t=pi/2, t=r*pi.


\>x &= r\*(t-sin(t))


    
            [0, 1.66665833335744e-7 r, 1.33330666692022e-6 r, 
    4.499797504338432e-6 r, 1.066581336583994e-5 r, 
    2.083072932167196e-5 r, 3.599352055540239e-5 r, 
    5.71526624672386e-5 r, 8.530603082730626e-5 r, 
    1.214508019889565e-4 r, 1.665833531718508e-4 r, 
    2.216991628251896e-4 r, 2.877927110806339e-4 r, 
    3.658573803051457e-4 r, 4.568853557635201e-4 r, 
    5.618675264007778e-4 r, 6.817933857540259e-4 r, 
    8.176509330039827e-4 r, 9.704265741758145e-4 r, 
    0.001141105023499428 r, 0.001330669204938795 r, 
    0.001540100153900437 r, 0.001770376919130678 r, 
    0.002022476464811601 r, 0.002297373572865413 r, 
    0.002596040745477063 r, 0.002919448107844891 r, 
    0.003268563311168871 r, 0.003644351435886262 r, 
    0.004047774895164447 r, 0.004479793338660443 r, 0.0049413635565565 r, 
    0.005433439383882244 r, 0.005956971605131645 r, 
    0.006512907859185624 r, 0.007102192544548636 r, 
    0.007725766724910044 r, 0.00838456803503801 r, 
    0.009079530587017326 r, 0.009811584876838586 r, 0.0105816576913495 r, 
    0.01139067201557714 r, 0.01223954694042984 r, 0.01312919757078923 r, 
    0.01406053493400045 r, 0.01503446588876983 r, 0.01605189303448024 r, 
    0.01711371462093175 r, 0.01822082445851714 r, 0.01937411182884202 r, 
    0.02057446139579705 r, 0.02182275311709253 r, 0.02311986215626333 r, 
    0.02446665879515308 r, 0.02586400834688696 r, 0.02731277106934082 r, 
    0.02881380207911666 r, 0.03036795126603076 r, 0.03197606320812652 r, 
    0.0336389770872163 r, 0.03535752660496472 r, 0.03713253989951881 r, 
    0.03896483946269502 r, 0.0408552420577305 r, 0.04280455863760801 r, 
    0.04481359426396048 r, 0.04688314802656623 r, 0.04901401296344043 r, 
    0.05120697598153157 r, 0.05346281777803219 r, 0.05578231276230905 r, 
    0.05816622897846346 r, 0.06061532802852698 r, 0.0631303649963022 r, 
    0.06571208837185505 r, 0.06836123997666599 r, 0.07107855488944881 r, 
    0.07386476137264342 r, 0.07672058079958999 r, 0.07964672758239233 r, 
    0.08264390910047736 r, 0.0857128256298576 r, 0.08885417027310427 r, 
    0.09206862889003742 r, 0.09535688002914089 r, 0.0987195948597075 r, 
    0.1021574371047232 r, 0.1056710629744951 r, 0.1092611211010309 r, 
    0.1129282524731764 r, 0.1166730903725168 r, 0.1204962603100498 r, 
    0.1243983799636342 r, 0.1283800591162231 r, 0.1324418995948859 r, 
    0.1365844952106265 r, 0.140808431699002 r, 0.1451142866615502 r, 
    0.1495026295080298 r, 0.1539740213994798 r]
    

\>y &= r\*(1-cos(t))


    
            [0, 4.999958333473664e-5 r, 1.999933334222437e-4 r, 
    4.499662510124569e-4 r, 7.998933390220841e-4 r, 
    0.001249739605033717 r, 0.00179946006479581 r, 
    0.002448999746720415 r, 0.003198293697380561 r, 
    0.004047266988005727 r, 0.004995834721974179 r, 
    0.006043902043303184 r, 0.00719136414613375 r, 0.00843810628521191 r, 
    0.009784003787362772 r, 0.01122892206395776 r, 0.01277271662437307 r, 
    0.01441523309043924 r, 0.01615630721187855 r, 0.01799576488272969 r, 
    0.01993342215875837 r, 0.02196908527585173 r, 0.02410255066939448 r, 
    0.02633360499462523 r, 0.02866202514797045 r, 0.03108757828935527 r, 
    0.03361002186548678 r, 0.03622910363410947 r, 0.03894456168922911 r, 
    0.04175612448730281 r, 0.04466351087439402 r, 0.04766643011428662 r, 
    0.05076458191755917 r, 0.0539576564716131 r, 0.05724533447165381 r, 
    0.06062728715262111 r, 0.06410317632206519 r, 0.06767265439396564 r, 
    0.07133536442348987 r, 0.07509094014268702 r, 0.07893900599711501 r, 
    0.08287917718339499 r, 0.08691105968769186 r, 0.09103425032511492 r, 
    0.09524833678003664 r, 0.09955289764732322 r, 0.1039475024744748 r, 
    0.1084317118046711 r, 0.113005077220716 r, 0.1176671413898787 r, 
    0.1224174381096274 r, 0.1272554923542488 r, 0.1321808203223502 r, 
    0.1371929294852391 r, 0.1422913186361759 r, 0.1474754779404944 r, 
    0.152744888986584 r, 0.1580990248377314 r, 0.1635373500848132 r, 
    0.1690593208998367 r, 0.1746643850903219 r, 0.1803519821545206 r, 
    0.1861215433374662 r, 0.1919724916878484 r, 0.1979042421157076 r, 
    0.2039162014509444 r, 0.2100077685026351 r, 0.216178334119151 r, 
    0.2224272812490723 r, 0.2287539850028937 r, 0.2351578127155118 r, 
    0.2416381240094921 r, 0.2481942708591053 r, 0.2548255976551299 r, 
    0.2615314412704124 r, 0.2683111311261794 r, 0.2751639892590951 r, 
    0.2820893303890569 r, 0.2890864619877229 r, 0.2961546843477643 r, 
    0.3032932906528349 r, 0.3105015670482534 r, 0.3177787927123868 r, 
    0.3251242399287333 r, 0.3325371741586922 r, 0.3400168541150183 r, 
    0.3475625318359485 r, 0.3551734527599992 r, 0.3628488558014202 r, 
    0.3705879734263036 r, 0.3783900317293359 r, 0.3862542505111889 r, 
    0.3941798433565377 r, 0.4021660177127022 r, 0.4102119749689023 r, 
    0.418316910536117 r, 0.4264800139275439 r, 0.4347004688396462 r, 
    0.4429774532337832 r, 0.451310139418413 r]
    

Berikut kita gambar sikloid untuk r=1.


\>ex &= x-sin(x); ey &= 1-cos(x); aspect(1);

\>plot2d(ex,ey,xmin=0,xmax=4pi,square=1); ...  
\>     plot2d("2+cos(x)","1+sin(x)",xmin=0,xmax=2pi,\>add,color=blue); ...  
\>     plot2d([2,ex(2)],[1,ey(2)],color=red,\>add); ...  
\>     plot2d(ex(2),ey(2),\>points,\>add,color=red); ...  
\>     plot2d("2pi+cos(x)","1+sin(x)",xmin=0,xmax=2pi,\>add,color=blue); ...  
\>     plot2d([2pi,ex(2pi)],[1,ey(2pi)],color=red,\>add);  ...  
\>     plot2d(ex(2pi),ey(2pi),\>points,\>add,color=red):


    Error : [0,1.66665833335744e-7*r-sin(1.66665833335744e-7*r),1.33330666692022e-6*r-sin(1.33330666692022e-6*r),4.499797504338432e-6*r-sin(4.499797504338432e-6*r),1.066581336583994e-5*r-sin(1.066581336583994e-5*r),2.083072932167196e-5*r-sin(2.083072932167196e-5*r),3.599352055540239e-5*r-sin(3.599352055540239e-5*r),5.71526624672386e-5*r-sin(5.71526624672386e-5*r),8.530603082730626e-5*r-sin(8.530603082730626e-5*r),1.214508019889565e-4*r-sin(1.214508019889565e-4*r),1.665833531718508e-4*r-sin(1.665833531718508e-4*r),2.216991628251896e-4*r-sin(2.216991628251896e-4*r),2.877927110806339e-4*r-sin(2.877927110806339e-4*r),3.658573803051457e-4*r-sin(3.658573803051457e-4*r),4.5688535576352e-4*r-sin(4.5688535576352e-4*r),5.618675264007778e-4*r-sin(5.618675264007778e-4*r),6.817933857540259e-4*r-sin(6.817933857540259e-4*r),8.176509330039827e-4*r-sin(8.176509330039827e-4*r),9.704265741758145e-4*r-sin(9.704265741758145e-4*r),0.001141105023499428*r-sin(0.001141105023499428*r),0.001330669204938795*r-sin(0.001330669204938795*r),0.001540100153900437*r-sin(0.001540100153900437*r),0.001770376919130678*r-sin(0.001770376919130678*r),0.002022476464811601*r-sin(0.002022476464811601*r),0.002297373572865413*r-sin(0.002297373572865413*r),0.002596040745477063*r-sin(0.002596040745477063*r),0.002919448107844891*r-sin(0.002919448107844891*r),0.003268563311168871*r-sin(0.003268563311168871*r),0.003644351435886262*r-sin(0.003644351435886262*r),0.004047774895164447*r-sin(0.004047774895164447*r),0.004479793338660443*r-sin(0.004479793338660443*r),0.0049413635565565*r-sin(0.0049413635565565*r),0.005433439383882244*r-sin(0.005433439383882244*r),0.005956971605131645*r-sin(0.005956971605131645*r),0.006512907859185624*r-sin(0.006512907859185624*r),0.007102192544548636*r-sin(0.007102192544548636*r),0.007725766724910044*r-sin(0.007725766724910044*r),0.00838456803503801*r-sin(0.00838456803503801*r),0.009079530587017326*r-sin(0.009079530587017326*r),0.009811584876838586*r-sin(0.009811584876838586*r),0.0105816576913495*r-sin(0.0105816576913495*r),0.01139067201557714*r-sin(0.01139067201557714*r),0.01223954694042984*r-sin(0.01223954694042984*r),0.01312919757078923*r-sin(0.01312919757078923*r),0.01406053493400045*r-sin(0.01406053493400045*r),0.01503446588876983*r-sin(0.01503446588876983*r),0.01605189303448024*r-sin(0.01605189303448024*r),0.01711371462093175*r-sin(0.01711371462093175*r),0.01822082445851714*r-sin(0.01822082445851714*r),0.01937411182884202*r-sin(0.01937411182884202*r),0.02057446139579705*r-sin(0.02057446139579705*r),0.02182275311709253*r-sin(0.02182275311709253*r),0.02311986215626333*r-sin(0.02311986215626333*r),0.02446665879515308*r-sin(0.02446665879515308*r),0.02586400834688696*r-sin(0.02586400834688696*r),0.02731277106934082*r-sin(0.02731277106934082*r),0.02881380207911666*r-sin(0.02881380207911666*r),0.03036795126603076*r-sin(0.03036795126603076*r),0.03197606320812652*r-sin(0.03197606320812652*r),0.0336389770872163*r-sin(0.0336389770872163*r),0.03535752660496472*r-sin(0.03535752660496472*r),0.03713253989951881*r-sin(0.03713253989951881*r),0.03896483946269502*r-sin(0.03896483946269502*r),0.0408552420577305*r-sin(0.0408552420577305*r),0.04280455863760801*r-sin(0.04280455863760801*r),0.04481359426396048*r-sin(0.04481359426396048*r),0.04688314802656623*r-sin(0.04688314802656623*r),0.04901401296344043*r-sin(0.04901401296344043*r),0.05120697598153157*r-sin(0.05120697598153157*r),0.05346281777803219*r-sin(0.05346281777803219*r),0.05578231276230905*r-sin(0.05578231276230905*r),0.05816622897846346*r-sin(0.05816622897846346*r),0.06061532802852698*r-sin(0.06061532802852698*r),0.0631303649963022*r-sin(0.0631303649963022*r),0.06571208837185505*r-sin(0.06571208837185505*r),0.06836123997666599*r-sin(0.06836123997666599*r),0.07107855488944881*r-sin(0.07107855488944881*r),0.07386476137264342*r-sin(0.07386476137264342*r),0.07672058079958999*r-sin(0.07672058079958999*r),0.07964672758239233*r-sin(0.07964672758239233*r),0.08264390910047736*r-sin(0.08264390910047736*r),0.0857128256298576*r-sin(0.0857128256298576*r),0.08885417027310427*r-sin(0.08885417027310427*r),0.09206862889003742*r-sin(0.09206862889003742*r),0.09535688002914089*r-sin(0.09535688002914089*r),0.0987195948597075*r-sin(0.0987195948597075*r),0.1021574371047232*r-sin(0.1021574371047232*r),0.1056710629744951*r-sin(0.1056710629744951*r),0.1092611211010309*r-sin(0.1092611211010309*r),0.1129282524731764*r-sin(0.1129282524731764*r),0.1166730903725168*r-sin(0.1166730903725168*r),0.1204962603100498*r-sin(0.1204962603100498*r),0.1243983799636342*r-sin(0.1243983799636342*r),0.1283800591162231*r-sin(0.1283800591162231*r),0.1324418995948859*r-sin(0.1324418995948859*r),0.1365844952106265*r-sin(0.1365844952106265*r),0.140808431699002*r-sin(0.140808431699002*r),0.1451142866615502*r-sin(0.1451142866615502*r),0.1495026295080298*r-sin(0.1495026295080298*r),0.1539740213994798*r-sin(0.1539740213994798*r)] does not produce a real or column vector
    
    Error generated by error() command
    
    adaptiveeval:
        error(f$|" does not produce a real or column vector"); 
    Try "trace errors" to inspect local variables after errors.
    plot2d:
        dw/n,dw/n^2,dw/n;args());

Berikut dihitung panjang lintasan untuk 1 putaran penuh. (Jangan salah menduga bahwa panjang lintasan 1 putaran penuh sama dengan
keliling lingkaran!)


\>ds &= radcan(sqrt(diff(ex,x)^2+diff(ey,x)^2)); $ds=trigsimp(ds) // elemen panjang kurva sikloid


    Maxima said:
    diff: second argument must be a variable; found errexp1
     -- an error. To debug this try: debugmode(true);
    
    Error in:
    ds &amp;= radcan(sqrt(diff(ex,x)^2+diff(ey,x)^2)); $ds=trigsimp(ds ...
                                                 ^

\>ds &= trigsimp(ds); $ds

\>$showev('integrate(ds,x,0,2\*pi)) // hitung panjang sikloid satu putaran penuh


    Maxima said:
    defint: variable of integration must be a simple or subscripted variable.
    defint: found errexp1
    #0: showev(f='integrate(ds,[0,1.66665833335744e-7*r,1.33330666692022e-6*r,4.499797504338432e-6*r,1.06658133658399...)
     -- an error. To debug this try: debugmode(true);
    
    Error in:
     $showev('integrate(ds,x,0,2*pi)) // hitung panjang sikloid sat ...
                                     ^

\>integrate(mxm("ds"),0,2\*pi) // hitung secara numerik


    Illegal function result in map.
     %evalexpression:
        if maps then return %mapexpression1(x,f$;args());
    gauss:
        if maps then y=%evalexpression(f$,a+h-(h*xn)',maps;args());
    adaptivegauss:
        t1=gauss(f$,c,c+h;args(),=maps);
    Try "trace errors" to inspect local variables after errors.
    integrate:
        return adaptivegauss(f$,a,b,eps*1000;args(),=maps);

\>romberg(mxm("ds"),0,2\*pi) // cara lain hitung secara numerik


    Wrong argument!
    
    Cannot combine a symbolic expression here.
    Did you want to create a symbolic expression?
    Then start with &amp;.
    
    Try "trace errors" to inspect local variables after errors.
    romberg:
        if cols(y)==1 then return y*(b-a); endif;
    Error in:
    romberg(mxm("ds"),0,2*pi) // cara lain hitung secara numerik ...
                             ^

Perhatikan, seperti terlihat pada gambar, panjang sikloid lebih besar daripada keliling lingkarannya, yakni:


## Kurvatur (Kelengkungan) Kurva

image: Osculating.png


Aslinya, kelengkungan kurva diferensiabel (yakni, kurva mulus yang tidak lancip) di titik P didefinisikan melalui lingkaran
oskulasi (yaitu, lingkaran yang melalui titik P dan terbaik memperkirakan, paling banyak menyinggung kurva di sekitar P). Pusat
dan radius kelengkungan kurva di P adalah pusat dan radius lingkaran oskulasi. Kelengkungan adalah kebalikan dari radius
kelengkungan:


dengan R adalah radius kelengkungan. (Setiap lingkaran memiliki kelengkungan ini pada setiap titiknya, dapat diartikan, setiap
lingkaran berputar 2pi sejauh 2piR.)


Definisi ini sulit dimanipulasi dan dinyatakan ke dalam rumus untuk kurva umum. Oleh karena itu digunakan definisi lain yang
ekivalen.


## Definisi Kurvatur dengan Fungsi Parametrik Panjang Kurva



Setiap kurva diferensiabel dapat dinyatakan dengan persamaan parametrik terhadap panjang kurva s:


dengan x dan y adalah fungsi riil yang diferensiabel, yang memenuhi:


Ini berarti bahwa vektor singgung


memiliki norm 1 dan merupakan vektor singgung satuan.


Apabila kurvanya memiliki turunan kedua, artinya turunan kedua x dan y ada, maka T'(s) ada. Vektor ini merupakan normal kurva yang
arahnya menuju pusat kurvatur, norm-nya merupakan nilai kurvatur (kelengkungan):


Nilai


disebut jari-jari (radius) kelengkungan kurva.


Bilangan riil


disebut nilai kelengkungan bertanda.


Contoh:


Akan ditentukan kurvatur lingkaran


\>fx &= r\*cos(t); fy &=r\*sin(t);

\>&assume(t\>0,r\>0); s &=integrate(sqrt(diff(fx,t)^2+diff(fy,t)^2),t,0,t); s // elemen panjang kurva, panjang busur lingkaran (s)


    Maxima said:
    diff: second argument must be a variable; found errexp1
     -- an error. To debug this try: debugmode(true);
    
    Error in:
    ... =integrate(sqrt(diff(fx,t)^2+diff(fy,t)^2),t,0,t); s // elemen ...
                                                         ^

\>&kill(s); fx &= r\*cos(s/r); fy &=r\*sin(s/r); // definisi ulang persamaan parametrik terhadap s dengan substitusi t=s/r

\>k &= trigsimp(sqrt(diff(fx,s,2)^2+diff(fy,s,2)^2)); $k // nilai kurvatur lingkaran dengan menggunakan definisi di atas


Untuk representasi parametrik umum, misalkan


merupakan persamaan parametrik untuk kurva bidang yang terdiferensialkan dua kali. Kurvatur untuk kurva tersebut didefinisikan
sebagai


Selanjutnya, pembilang pada persamaan di atas dapat dicari sebagai berikut.


Jadi, rumus kurvatur untuk kurva parametrik


adalah


Jika kurvanya dinyatakan dengan persamaan parametrik pada koordinat
kutub


maka rumus kurvaturnya adalah


(Silakan Anda turunkan rumus tersebut!)


Contoh:


Lingkaran dengan pusat (0,0) dan jari-jari r dapat dinyatakan dengan
persamaan parametrik


Nilai kelengkungan lingkaran tersebut adalah


Hasil cocok dengan definisi kurvatur suatu kelengkungan.


Kurva


dapat dinyatakan ke dalam persamaan parametrik


sehingga kurvaturnya adalah


Contoh:


Akan ditentukan kurvatur parabola


\>function f(x) &= a\*x^2+b\*x+c; $y=f(x)

\>function k(x) &= (diff(f(x),x,2))/(1+diff(f(x),x)^2)^(3/2); $'k(x)=k(x) // kelengkungan parabola 


    Maxima said:
    diff: second argument must be a variable; found errexp1
     -- an error. To debug this try: debugmode(true);
    
    Error in:
    ... (x) &amp;= (diff(f(x),x,2))/(1+diff(f(x),x)^2)^(3/2); $'k(x)=k(x)  ...
                                                         ^

\>function f(x) &= x^2+x+1; $y=f(x) // akan kita plot kelengkungan parabola untuk a=b=c=1

\>function k(x) &= (diff(f(x),x,2))/(1+diff(f(x),x)^2)^(3/2); $'k(x)=k(x) // kelengkungan parabola 


    Maxima said:
    diff: second argument must be a variable; found errexp1
     -- an error. To debug this try: debugmode(true);
    
    Error in:
    ... (x) &amp;= (diff(f(x),x,2))/(1+diff(f(x),x)^2)^(3/2); $'k(x)=k(x)  ...
                                                         ^

Berikut kita gambar parabola tersebut beserta kurva kelengkungan, kurva jari-jari kelengkungan dan salah satu lingkaran oskulasi
di titik puncak parabola. Perhatikan, puncak parabola dan jari-jari lingkaran oskulasi di puncak parabola adalah


sehingga pusat lingkaran oskulasi adalah (-1/2, 5/4).


\>plot2d(["f(x)", "k(x)"],-2,1, color=[blue,red]); plot2d("1/k(x)",-1.5,1,color=green,\>add); ...  
\>   plot2d("-1/2+1/k(-1/2)\*cos(x)","5/4+1/k(-1/2)\*sin(x)",xmin=0,xmax=2pi,\>add,color=blue):


    Error : f(x) does not produce a real or column vector
    
    Error generated by error() command
    
     %ploteval:
        error(f$|" does not produce a real or column vector"); 
    adaptiveevalone:
        s=%ploteval(g$,t;args());
    Try "trace errors" to inspect local variables after errors.
    plot2d:
        dw/n,dw/n^2,dw/n,auto;args());

Untuk kurva yang dinyatakan dengan fungsi implisit


dengan turunan-turunan parsial


berlaku


sehingga kurvaturnya adalah


(Silakan Anda turunkan sendiri!)


Contoh 1:


Parabola


dapat dinyatakan ke dalam persamaan implisit


\>function F(x,y) &=a\*x^2+b\*x+c-y; $F(x,y)

\>Fx &= diff(F(x,y),x), Fxx &=diff(F(x,y),x,2), Fy &=diff(F(x,y),y), Fxy &=diff(diff(F(x,y),x),y), Fyy &=diff(F(x,y),y,2)  


    
                                                                2 a x + b
    
    
                                                                   2 a
    
    
                                                                   - 1
    
    
                                                                    0
    
    
                                                                    0
    

\>function k(x) &= (Fy^2\*Fxx-2\*Fx\*Fy\*Fxy+Fx^2\*Fyy)/(Fx^2+Fy^2)^(3/2); $'k(x)=k(x) // kurvatur parabola tersebut


Hasilnya sama dengan sebelumnya yang menggunakan persamaan parabola biasa.


# Latihan

* 
Bukalah buku Kalkulus.

* 
Cari dan pilih beberapa (paling sedikit 5 fungsi berbeda
* tipe/bentuk/jenis) fungsi dari buku tersebut, kemudian definisikan di
* EMT pada baris-baris perintah berikut (jika perlu tambahkan lagi).

* 
Untuk setiap fungsi, tentukan anti turunannya (jika ada), hitunglah
* integral tentu dengan batas-batas yang menarik (Anda tentukan
* sendiri), seperti contoh-contoh tersebut.

* 
Lakukan hal yang sama untuk fungsi-fungsi yang tidak dapat
* diintegralkan (cari sedikitnya 3 fungsi).

* 
Gambar grafik fungsi dan daerah integrasinya pada sumbu koordinat
* yang sama.

* 
Gunakan integral tentu untuk mencari luas daerah yang dibatasi oleh
* dua kurva yang berpotongan di dua titik. (Cari dan gambar kedua kurva
* dan arsir (warnai) daerah yang dibatasi oleh keduanya.)

* 
Gunakan integral tentu untuk menghitung volume benda putar kurva y=
* f(x) yang diputar mengelilingi sumbu x dari x=a sampai x=b, yakni


(Pilih fungsinya dan gambar kurva dan benda putar yang dihasilkan.
Anda dapat mencari contoh-contoh bagaimana cara menggambar benda hasil
perputaran suatu kurva.)


- Gunakan integral tentu untuk menghitung panjang kurva y=f(x) dari
x=a sampai x=b dengan menggunakan rumus:


(Pilih fungsi dan gambar kurvanya.)


- Apabila fungsi dinyatakan dalam koordinat kutub x=f(r,t), y=g(r,t),
r=h(t), x=a bersesuaian dengan t=t0 dan x=b bersesuian dengan t=t1,
maka rumus di atas akan menjadi:


* 
Pilih beberapa kurva menarik (selain lingkaran dan parabola) dari
* buku  kalkulus. Nyatakan setiap kurva tersebut dalam bentuk:
*   a. koordinat Kartesius (persamaan y=f(x))
*   b. koordinat kutub ( r=r(theta))
*   c. persamaan parametrik x=x(t), y=y(t)
*   d. persamaan implit F(x,y)=0

* 
Tentukan kurvatur masing-masing kurva dengan menggunakan keempat
* representasi tersebut (hasilnya harus sama).

* 
Gambarlah kurva asli, kurva kurvatur, kurva jari-jari lingkaran
* oskulasi, dan salah satu lingkaran oskulasinya.


# Barisan dan Deret

(Catatan: bagian ini belum lengkap. Anda dapat membaca contoh-contoh pengguanaan EMT dan
Maxima untuk menghitung limit barisan, rumus jumlah parsial suatu deret, jumlah tak hingga
suatu deret konvergen, dan sebagainya. Anda dapat mengeksplor contoh-contoh di EMT atau
perbagai panduan penggunaan Maxima di software Maxima atau dari Internet.)


Barisan dapat didefinisikan dengan beberapa cara di dalam EMT, di antaranya:


* 
dengan cara yang sama seperti mendefinisikan vektor dengan elemen-elemen beraturan
* (menggunakan titik dua ":");

* 
menggunakan perintah "sequence" dan rumus barisan (suku ke -n);

* 
menggunakan perintah "iterate" atau "niterate";

* 
menggunakan fungsi Maxima "create_list" atau "makelist" untuk menghasilkan barisan
* simbolik;

* 
menggunakan fungsi biasa yang inputnya vektor atau barisan;

* 
menggunakan fungsi rekursif.


EMT menyediakan beberapa perintah (fungsi) terkait barisan, yakni:


* 
sum: menghitung jumlah semua elemen suatu barisan

* 
cumsum: jumlah kumulatif suatu barisan

* 
differences: selisih antar elemen-elemen berturutan


EMT juga dapat digunakan untuk menghitung jumlah deret berhingga maupun deret tak hingga,
dengan menggunakan perintah (fungsi) "sum". Perhitungan dapat dilakukan secara numerik
maupun simbolik dan eksak.


Berikut adalah beberapa contoh perhitungan barisan dan deret menggunakan EMT.


\>1:10 // barisan sederhana


    [1,  2,  3,  4,  5,  6,  7,  8,  9,  10]

\>1:2:30


    [1,  3,  5,  7,  9,  11,  13,  15,  17,  19,  21,  23,  25,  27,  29]

# Iterasi dan Barisan

EMT menyediakan fungsi iterate("g(x)", x0, n) untuk melakukan iterasi


Berikut ini disajikan contoh-contoh penggunaan iterasi dan rekursi
dengan EMT. Contoh pertama menunjukkan pertumbuhan dari nilai awal
1000 dengan laju pertambahan 5%, selama 10 periode.


\>q=1.05; iterate("x\*q",1000,n=10)'


             1000 
             1050 
           1102.5 
          1157.63 
          1215.51 
          1276.28 
           1340.1 
           1407.1 
          1477.46 
          1551.33 
          1628.89 

Contoh berikutnya memperlihatkan bahaya menabung di bank pada masa sekarang! Dengan bunga
tabungan sebesar 6% per tahun atau 0.5% per bulan dipotong pajak 20%, dan biaya administrasi
10000 per bulan, tabungan sebesar 1 juta tanpa diambil selama sekitar 10 tahunan akan habis
diambil oleh bank!


\>r=0.005; plot2d(iterate("(1+0.8\*r)\*x-10000",1000000,n=130)):


Silakan Anda coba-coba, dengan tabungan minimal berapa agar tidak akan habis diambil oleh
bank dengan ketentuan bunga dan biaya administrasi seperti di atas.


Berikut adalah perhitungan minimal tabungan agar aman di bank dengan bunga sebesar r dan
biaya administrasi a, pajak bunga 20%.


\>$solve(0.8\*r\*A-a,A), $% with [r=0.005, a=10] 


Berikut didefinisikan fungsi untuk menghitung saldo tabungan, kemudian dilakukan iterasi.


\>function saldo(x,r,a) := round((1+0.8\*r)\*x-a,2);

\>iterate({{"saldo",0.005,10}},1000,n=6)


    [1000,  994,  987.98,  981.93,  975.86,  969.76,  963.64]

\>iterate({{"saldo",0.005,10}},2000,n=6)


    [2000,  1998,  1995.99,  1993.97,  1991.95,  1989.92,  1987.88]

\>iterate({{"saldo",0.005,10}},2500,n=6)


    [2500,  2500,  2500,  2500,  2500,  2500,  2500]

Tabungan senilai 2,5 juta akan aman dan tidak akan berubah nilai (jika tidak ada penarikan),
sedangkan jika tabungan awal kurang dari 2,5 juta, lama kelamaan akan berkurang meskipun
tidak pernah dilakukan penarikan uang tabungan.


\>iterate({{"saldo",0.005,10}},3000,n=6)


    [3000,  3002,  3004.01,  3006.03,  3008.05,  3010.08,  3012.12]

Tabungan yang lebih dari 2,5 juta baru akan bertambah jika tidak ada penarikan.


Untuk barisan yang lebih kompleks dapat digunakan fungsi "sequence()". Fungsi ini menghitung
nilai-nilai x[n] dari semua nilai sebelumnya, x[1],...,x[n-1] yang diketahui.


Berikut adalah contoh barisan Fibonacci.


\>sequence("x[n-1]+x[n-2]",[1,1],15)


    [1,  1,  2,  3,  5,  8,  13,  21,  34,  55,  89,  144,  233,  377,  610]

Barisan Fibonacci memiliki banyak sifat menarik, salah satunya adalah akar pangkat ke-n suku
ke-n akan konvergen ke pecahan emas:


\>$'(1+sqrt(5))/2=float((1+sqrt(5))/2)

\>plot2d(sequence("x[n-1]+x[n-2]",[1,1],250)^(1/(1:250))):


Barisan yang sama juga dapat dihasilkan dengan menggunakan loop.


\>x=ones(500); for k=3 to 500; x[k]=x[k-1]+x[k-2]; end;


Rekursi dapat dilakukan dengan menggunakan rumus yang tergantung pada semua elemen
sebelumnya. Pada contoh berikut, elemen ke-n merupakan jumlah (n-1) elemen sebelumnya,
dimulai dengan 1 (elemen ke-1). Jelas, nilai elemen ke-n adalah 2^(n-2), untuk n=2, 4, 5,
....


\>sequence("sum(x)",1,10)


    [1,  1,  2,  4,  8,  16,  32,  64,  128,  256]

Selain menggunakan ekspresi dalam x dan n, kita juga dapat menggunakan fungsi.


Pada contoh berikut, digunakan iterasi


dengan A suatu matriks 2x2, dan setiap x[n] merupakan matriks/vektor 2x1.


\>A=[1,1;1,2]; function suku(x,n) := A.x[,n-1]

\>sequence("suku",[1;1],6)


    Real 2 x 6 matrix
    
                1             2             5            13     ...
                1             3             8            21     ...

Hasil yang sama juga dapat diperoleh dengan menggunakan fungsi perpangkatan matriks
"matrixpower()". Cara ini lebih cepat, karena hanya menggunakan perkalian matriks sebanyak
log_2(n).


\>sequence("matrixpower(A,n).[1;1]",1,6)


    Real 2 x 6 matrix
    
                1             5            13            34     ...
                1             8            21            55     ...

# Spiral Theodorus

image: Spiral_of_Theodorus.png


Spiral Theodorus (spiral segitiga siku-siku) dapat digambar secara rekursif. Rumus
rekursifnya adalah:


yang menghasilkan barisan bilangan kompleks.


\>function g(n) := 1+I/sqrt(n)


Rekursinya dapat dijalankan sebanyak 17 untuk menghasilkan barisan 17 bilangan kompleks,
kemudian digambar bilangan-bilangan kompleksnya.


\>x=sequence("g(n-1)\*x[n-1]",1,17); plot2d(x,r=3.5); textbox(latex("Spiral\\ Theodorus"),0.4):


Selanjutnya dihubungan titik 0 dengan titik-titik kompleks tersebut menggunakan loop.


\>for i=1:cols(x); plot2d([0,x[i]],\>add); end:

\> 


Spiral tersebut juga dapat didefinisikan menggunakan fungsi rekursif, yang tidak memmerlukan
indeks dan bilangan kompleks. Dalam hal ini diigunakan vektor kolom pada bidang.


\>function gstep (v) ...


    w=[-v[2];v[1]];
    return v+w/norm(w);
    endfunction
</pre>
Jika dilakukan iterasi 16 kali dimulai dari [1;0] akan didapatkan matriks yang memuat
vektor-vektor dari setiap iterasi.


\>x=iterate("gstep",[1;0],16); plot2d(x[1],x[2],r=3.5,\>points):


# Kekonvergenan

Terkadang kita ingin melakukan iterasi sampai konvergen. Apabila iterasinya tidak konvergen
setelah ditunggu lama, Anda dapat menghentikannya dengan menekan tombol [ESC].


\>iterate("cos(x)",1) // iterasi x(n+1)=cos(x(n)), dengan x(0)=1.


    0.739085133216

Iterasi tersebut konvergen ke penyelesaian persamaan


Iterasi ini juga dapat dilakukan pada interval, hasilnya adalah barisan interval yang memuat
akar tersebut.


\>hasil := iterate("cos(x)",~1,2~) //iterasi x(n+1)=cos(x(n)), dengan interval awal (1, 2)


    ~0.739085133211,0.7390851332133~

Jika interval hasil tersebut sedikit diperlebar, akan terlihat bahwa interval tersebut
memuat akar persamaan x=cos(x).


\>h=expand(hasil,100), cos(h) << h


    ~0.73908513309,0.73908513333~
    1

Iterasi juga dapat digunakan pada fungsi yang didefinisikan.


\>function f(x) := (x+2/x)/2


Iterasi x(n+1)=f(x(n)) akan konvergen ke akar kuadrat 2.


\>iterate("f",2), sqrt(2)


    1.41421356237
    1.41421356237

Jika pada perintah iterate diberikan tambahan parameter n, maka hasil iterasinya akan
ditampilkan mulai dari iterasi pertama sampai ke-n.


\>iterate("f",2,5)


    [2,  1.5,  1.41667,  1.41422,  1.41421,  1.41421]

Untuk iterasi ini tidak dapat dilakukan terhadap interval.


\>niterate("f",~1,2~,5)


    [ ~1,2~,  ~1,2~,  ~1,2~,  ~1,2~,  ~1,2~,  ~1,2~ ]

Perhatikan, hasil iterasinya sama dengan interval awal. Alasannya adalah perhitungan dengan
interval bersifat terlalu longgar. Untuk meingkatkan perhitungan pada ekspresi dapat
digunakan pembagian intervalnya, menggunakan fungsi ieval().


\>function s(x) := ieval("(x+2/x)/2",x,10)


Selanjutnya dapat dilakukan iterasi hingga diperoleh hasil optimal, dan intervalnya tidak
semakin mengecil. Hasilnya berupa interval yang memuat akar persamaan:


Satu-satunya solusi adalah


\>iterate("s",~1,2~)


    ~1.41421356236,1.41421356239~

Fungsi "iterate()" juga dapat bekerja pada vektor. Berikut adalah contoh fungsi vektor, yang
menghasilkan rata-rata aritmetika dan rata-rata geometri.


Iterasi ke-n disimpan pada vektor kolom x[n].


\>function g(x) := [(x[1]+x[2])/2;sqrt(x[1]\*x[2])]


Iterasi dengan menggunakan fungsi tersebut akan konvergen ke rata-rata aritmetika dan
geometri dari nilai-nilai awal. 


\>iterate("g",[1;5])


          2.60401 
          2.60401 

Hasil tersebut konvergen agak cepat, seperti kita cek sebagai berikut.


\>iterate("g",[1;5],4)


                1             3       2.61803       2.60403       2.60401 
                5       2.23607       2.59002       2.60399       2.60401 

Iterasi pada interval dapat dilakukan dan stabil, namun tidak menunjukkan bahwa limitnya
pada batas-batas yang dihitung.


\>iterate("g",[~1~;~5~],4)


    Interval 2 x 5 matrix
    
    ~0.999999999999999778,1.00000000000000022~     ...
    ~4.99999999999999911,5.00000000000000089~     ...

Iterasi berikut konvergen sangat lambat.


\>iterate("sqrt(x)",2,10)


    [2,  1.41421,  1.18921,  1.09051,  1.04427,  1.0219,  1.01089,
    1.00543,  1.00271,  1.00135,  1.00068]

Kekonvergenan iterasi tersebut dapat dipercepatdengan percepatan Steffenson:


\>steffenson("sqrt(x)",2,10)


    [1.04888,  1.00028,  1,  1]

# Iterasi menggunakan Loop yang ditulis Langsung

Berikut adalah beberapa contoh penggunaan loop untuk melakukan iterasi yang ditulis langsung
pada baris perintah.


\>x=2; repeat x=(x+2/x)/2; until x^2~=2; end; x,


    1.41421356237

Penggabungan matriks menggunakan tanda "|" dapat digunakan untuk menyimpan semua hasil
iterasi.


\>v=[1]; for i=2 to 8; v=v|(v[i-1]\*i); end; v,


    [1,  2,  6,  24,  120,  720,  5040,  40320]

hasil iterasi juga dapat disimpan pada vektor yang sudah ada.


\>v=ones(1,100); for i=2 to cols(v); v[i]=v[i-1]\*i; end; ...  
\>   plot2d(v,logplot=1); textbox(latex(&log(n)),x=0.5):

\>A =[0.5,0.2;0.7,0.1]; b=[2;2]; ...  
\>   x=[1;1]; repeat xnew=A.x-b; until all(xnew~=x); x=xnew; end; ...  
\>   x,


         -7.09677 
         -7.74194 

# Iterasi di dalam Fungsi

Fungsi atau program juga dapat menggunakan iterasi dan dapat digunakan untuk melakukan iterasi. Berikut adalah beberapa contoh
iterasi di dalam fungsi.


Contoh berikut adalah suatu fungsi untuk menghitung berapa lama suatu iterasi konvergen. Nilai fungsi tersebut adalah hasil akhir
iterasi dan banyak iterasi sampai konvergen.


\>function map hiter(f$,x0) ...


    x=x0;
    maxiter=0;
    repeat
      xnew=f$(x);
      maxiter=maxiter+1;
      until xnew~=x;
      x=xnew;
    end;
    return maxiter;
    endfunction
</pre>
Misalnya, berikut adalah iterasi untuk mendapatkan hampiran akar kuadrat 2, cukup cepat,
konvergen pada iterasi ke-5, jika dimulai dari hampiran awal 2.


\>hiter("(x+2/x)/2",2)


    5

Karena fungsinya didefinisikan menggunakan "map". maka nilai awalnya dapat berupa vektor.


\>x=1.5:0.1:10; hasil=hiter("(x+2/x)/2",x); ...  
\>     plot2d(x,hasil):


Dari gambar di atas terlihat bahwa kekonvergenan iterasinya semakin lambat, untuk nilai awal
semakin besar, namun penambahnnya tidak kontinu. Kita dapat menemukan kapan maksimum
iterasinya bertambah.


\>hasil[1:10]


    [4,  5,  5,  5,  5,  5,  6,  6,  6,  6]

\>x[nonzeros(differences(hasil))]


    [1.5,  2,  3.4,  6.6]

maksimum iterasi sampai konvergen meningkat pada saat nilai awalnya 1.5, 2, 3.4, dan 6.6.


Contoh berikutnya adalah metode Newton pada polinomial kompleks berderajat 3.


\>p &= x^3-1; newton &= x-p/diff(p,x); $newton


Selanjutnya didefinisikan fungsi untuk melakukan iterasi (aslinya 10 kali).


\>function iterasi(f$,x,n=10) ...


    loop 1 to n; x=f$(x); end;
    return x;
    endfunction
</pre>
Kita mulai dengan menentukan titik-titik grid pada bidang kompleksnya.


\>r=1.5; x=linspace(-r,r,501); Z=x+I\*x'; W=iterasi(newton,Z);


Berikut adalah akar-akar polinomial di atas.


\>z=&solve(p)()


    [ -0.5+0.866025i,  -0.5-0.866025i,  1+0i  ]

Untuk menggambar hasil iterasinya, dihitung jarak dari hasil iterasi ke-10 ke masing-masing
akar, kemudian digunakan untuk menghitung warna yang akan digambar, yang menunjukkan limit
untuk masing-masing nilai awal. 


Fungsi plotrgb() menggunakan jendela gambar terkini untuk menggambar warna RGB sebagai
matriks.


\>C=rgb(max(abs(W-z[1]),1),max(abs(W-z[2]),1),max(abs(W-z[3]),1)); ...  
\>     plot2d(none,-r,r,-r,r); plotrgb(C):


# Iterasi Simbolik

Seperti sudah dibahas sebelumnya, untuk menghasilkan barisan ekspresi simbolik dengan Maxima
dapat digunakan fungsi makelist().


\>&powerdisp:true // untuk menampilkan deret pangkat mulai dari suku berpangkat terkecil


    
                                     true
    

\>deret &= makelist(taylor(exp(x),x,0,k),k,1,3); $deret // barisan deret Taylor untuk e^x


Untuk mengubah barisan deret tersebut menjadi vektor string di EMT digunakan fungsi
mxm2str(). Selanjutnya, vektor string/ekspresi hasilnya dapat digambar seperti menggambar
vektor eskpresi pada EMT.


\>plot2d("exp(x)",0,3); // plot fungsi aslinya, e^x

\>plot2d(mxm2str("deret"),\>add,color=4:6): // plot ketiga deret taylor hampiran fungsi tersebut


Selain cara di atas dapat juga dengan cara menggunakan indeks pada vektor/list yang
dihasilkan.


\>$deret[3]

\>plot2d(["exp(x)",&deret[1],&deret[2],&deret[3]],0,3,color=1:4):

\>$sum(sin(k\*x)/k,k,1,5)


Berikut adalah cara menggambar kurva


\>plot2d(&sum(sin((2\*k+1)\*x)/(2\*k+1),k,0,20),0,2pi):


Hal serupa juga dapat dilakukan dengan menggunakan matriks, misalkan kita akan menggambar
kurva


\>x=linspace(0,2pi,1000); k=1:100; y=sum(sin(k\*x')/k)'; plot2d(x,y):


# Tabel Fungsi

Terdapat cara menarik untuk menghasilkan barisan dengan ekspresi Maxima. Perintah
mxmtable() berguna untuk menampilkan dan menggambar barisan dan menghasilkan barisan sebagai
vektor kolom. 


Sebagai contoh berikut adalah barisan turunan ke-n x^x di x=1.


\>mxmtable("diffat(x^x,x=1,n)","n",1,8,frac=1);


            1 
            2 
            3 
            8 
           10 
           54 
          -42 
          944 

\>$'sum(k, k, 1, n) = factor(ev(sum(k, k, 1, n),simpsum=true)) // simpsum:menghitung deret secara simbolik

\>$'sum(1/(3^k+k), k, 0, inf) = factor(ev(sum(1/(3^k+k), k, 0, inf),simpsum=true))


Di sini masih gagal, hasilnya tidak dihitung.


\>$'sum(1/x^2, x, 1, inf)= ev(sum(1/x^2, x, 1, inf),simpsum=true) // ev: menghitung nilai ekspresi

\>$'sum((-1)^(k-1)/k, k, 1, inf) = factor(ev(sum((-1)^(x-1)/x, x, 1, inf),simpsum=true))


Di sini masih gagal, hasilnya tidak dihitung.


\>$'sum((-1)^k/(2\*k-1), k, 1, inf) = factor(ev(sum((-1)^k/(2\*k-1), k, 1, inf),simpsum=true))

\>$ev(sum(1/n!, n, 0, inf),simpsum=true)


Di sini masih gagal, hasilnya tidak dihitung, harusnya hasilnya e.


\>&assume(abs(x)<1); $'sum(a\*x^k, k, 0, inf)=ev(sum(a\*x^k, k, 0, inf),simpsum=true), &forget(abs(x)<1);


Deret geometri tak hingga, dengan asumsi rasional antara -1 dan 1.


\>$'sum(x^k/k!,k,0,inf)=ev(sum(x^k/k!,k,0,inf),simpsum=true)

\>$limit(sum(x^k/k!,k,0,n),n,inf)

\>function d(n) &= sum(1/(k^2-k),k,2,n); $'d(n)=d(n)

\>$d(10)=ev(d(10),simpsum=true)

\>$d(100)=ev(d(100),simpsum=true)


# Deret Taylor

Deret Taylor suatu fungsi f yang diferensiabel sampai tak hingga di sekitar x=a adalah:


\>$'e^x =taylor(exp(x),x,0,10) // deret Taylor e^x di sekitar x=0, sampai suku ke-11

\>$'log(x)=taylor(log(x),x,1,10)// deret log(x) di sekitar x=1


    

