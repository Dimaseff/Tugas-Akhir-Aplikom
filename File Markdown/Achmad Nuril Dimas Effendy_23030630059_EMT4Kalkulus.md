# Kalkulus dengan EMT
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
Barisan dan Deret (kekonvergenan barisan dan deret),

* 
Fungsi Multivariabel


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


Berikut adalah adalah beberapa contoh cara mendefinisikan fungsi.


\>function f(x) := 2\*x^2+exp(sin(x)) // fungsi numerik

\>f(0), f(1), f(pi)


    1
    4.31977682472
    20.7392088022

\>function g(x) := sqrt(x^2-3\*x)/(x+1)

\>g(3)


    0

\>g(0)


    0

\>g(1)


    Floating point error!
    Error in sqrt
    Try "trace errors" to inspect local variables after errors.
    g:
        useglobal; return sqrt(x^2-3*x)/(x+1) 
    Error in:
    g(1) ...
        ^

Nb: Floating point error karena untuk x=1, g(x) akan bernilai imajiner


yaitu


\>f(g(5)) // komposisi fungsi


    2.20920171961

\>g(f(5))


    0.950898070639

\>f(0:10) // nilai-nilai f(1), f(2), ..., f(10)


    [1,  4.31978,  10.4826,  19.1516,  32.4692,  50.3833,  72.7562,
    99.929,  130.69,  163.51,  200.58]

\>fmap(0:10) // sama dengan f(0:10), berlaku untuk semua fungsi


    [1,  4.31978,  10.4826,  19.1516,  32.4692,  50.3833,  72.7562,
    99.929,  130.69,  163.51,  200.58]

Misalkan kita akan mendefinisikan fungsi


$$f(x) = \begin{cases} x^3 & x>0 \\ x^2 & x\le 0. \end{cases}$$Fungsi tersebut tidak dapat didefinisikan sebagai fungsi numerik
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

\>f(-5:5)


    [25,  16,  9,  4,  1,  0,  1,  8,  27,  64,  125]

\>aspect(1.5); plot2d("f(x)",-5,5):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-002.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-002.png)

\>function f(x) &= 2\*E^x // fungsi simbolik


    
                                        x
                                     2 E
    

\>function g(x) &= 3\*x+1


    
                                   3 x + 1
    

\>function h(x) &= f(g(x)) // komposisi fungsi


    
                                     3 x + 1
                                  2 E
    

# Latihan

Bukalah buku Kalkulus. Cari dan pilih beberapa (paling sedikit 5
fungsi berbeda tipe/bentuk/jenis) fungsi dari buku tersebut, kemudian
definisikan di EMT pada baris-baris perintah berikut (jika perlu
tambahkan lagi). Untuk setiap fungsi, hitung beberapa nilainya, baik
untuk satu nilai maupun vektor. Gambar grafik tersebut.


Juga, carilah fungsi beberapa (dua) variabel. Lakukan hal sama seperti
di atas.


1. Untuk fungsi


$$k(x) = x^2-4$$

tentukan nilai


a. k(-4)


b. k(4)


\>function k(x) := x^2 -4

\>k(-4), k(4)


    Function k not found.
    Try list ... to find functions!
    Error in:
    k(-4), k(4) ...
         ^

\>plot2d("k",-4,4):


    Variable k not found!
    Use global variables or parameters for string evaluation.
    Error in expression: k
     %ploteval:
        y0=f$(x[1],args());
    adaptiveevalone:
        s=%ploteval(g$,t;args());
    Try "trace errors" to inspect local variables after errors.
    plot2d:
        dw/n,dw/n^2,dw/n,auto;args());

2. Untuk fungsi


$$z(x) = \frac{x^2-16}{x-4}$$

hitunglah masing-masing nilai.


a. z(6)


b. z(2)


\>function z(x) := (x^2-16)/(x-4)

\>z(6), z(2)


    10
    6

\>plot2d("z",-4,6):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-005.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-005.png)

3. Untuk fungsi


$$r(x) = x^3 - 3x^2 + 2x - 4$$

tentukan nilai r(4), r(-6), r(8)


\>function f(x) := x^3-3\*x^2+2\*x-4

\>f(4), f(-6), f(8)


    20
    -340
    332

\>plot2d("x^3-3\*x^2+2\*x-4",-2,9):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-007.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-007.png)

4. Tentukan nilai f(200) dari fungsi berikut


$$f(x) = \sqrt{x-64}$$\>function f(x) := sqrt(x-64)

\>f(200)


    11.6619037897

\>plot2d("sqrt(x-64)",0,200):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-009.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-009.png)

5. Untuk fungsi


$$f(x) = x^2-3x+2$$$$dan$$$$g(x) = x+3$$

cari nilai fog(-4), gof(0)


\>function f(x) := x^2-3\*x+2; $f(x)

\>function g(x) := x+3; $g(x)

\>f(g(-4)), g(f(0))


    6
    5

\>plot2d("(x+3)^2-3\*(x+3)+2",-2,2):


6. Tentukan nilai dari


$$f(x,y):=x^2+y^2+2x-2y+1$$

dengan x=1 dan y=3


\>function f(x,y):= x^2+y^2+2\*x-2\*y+1

\>f(1,3)


    7

\>plot3d("x^2+y^2+2\*x-2\*y+1"):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-014.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-014.png)

# Menghitung Limit

Perhitungan limit pada EMT dapat dilakukan dengan menggunakan fungsi Maxima, yakni "limit".
Fungsi "limit" dapat digunakan untuk menghitung limit fungsi dalam bentuk ekspresi maupun
fungsi yang sudah didefinisikan sebelumnya. Nilai limit dapat dihitung pada sebarang nilai
atau pada tak hingga (-inf, minf, dan inf). Limit kiri dan limit kanan juga dapat dihitung,
dengan cara memberi opsi "plus" atau "minus". Hasil limit dapat berupa nilai, "und' (tak
definisi), "ind" (tak tentu namun terbatas), "infinity" (kompleks tak hingga).


Perhatikan beberapa contoh berikut. Perhatikan cara menampilkan perhitungan secara lengkap,
tidak hanya menampilkan hasilnya saja.


\>$showev('limit(1/(2\*x-1),x,0))


$$\lim_{x\rightarrow 0}{\frac{1}{2\,x-1}}=-1$$\>$showev('limit((x^2-3\*x-10)/(x-5),x,5))


$$\lim_{x\rightarrow 5}{\frac{x^2-3\,x-10}{x-5}}=7$$\>$showev('limit(sin(x)/x,x,0))


$$\lim_{x\rightarrow 0}{\frac{\sin x}{x}}=1$$\>plot2d("sin(x)/x",-pi,pi):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-018.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-018.png)

\>$showev('limit(sin(x^3)/x,x,0))


$$\lim_{x\rightarrow 0}{\frac{\sin x^3}{x}}=0$$\>$showev('limit(log(x), x, minf))


$$\lim_{x\rightarrow  -\infty }{\log x}={\it infinity}$$\>$showev('limit((-2)^x,x, inf))


$$\lim_{x\rightarrow \infty }{\left(-2\right)^{x}}={\it infinity}$$\>$showev('limit(t-sqrt(2-t),t,2,minus))


$$\lim_{t\uparrow 2}{t-\sqrt{2-t}}=2$$\>$showev('limit(t-sqrt(2-t),t,5,plus)) // Perhatikan hasilnya


$$\lim_{t\downarrow 5}{t-\sqrt{2-t}}=5-\sqrt{3}\,i$$\>plot2d("x-sqrt(2-x)",-2,5):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-024.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-024.png)

\>$showev('limit((x^2-9)/(2\*x^2-5\*x-3),x,3))


$$\lim_{x\rightarrow 3}{\frac{x^2-9}{2\,x^2-5\,x-3}}=\frac{6}{7}$$\>$showev('limit((1-cos(x))/x,x,0))


$$\lim_{x\rightarrow 0}{\frac{1-\cos x}{x}}=0$$\>$showev('limit((x^2+abs(x))/(x^2-abs(x)),x,0))


$$\lim_{x\rightarrow 0}{\frac{\left| x\right| +x^2}{x^2-\left| x  \right| }}=-1$$\>$showev('limit((1+1/x)^x,x,inf))


$$\lim_{x\rightarrow \infty }{\left(\frac{1}{x}+1\right)^{x}}=e$$\>$showev('limit((1+k/x)^x,x,inf))


$$\lim_{x\rightarrow \infty }{\left(\frac{k}{x}+1\right)^{x}}=e^{k}$$\>$showev('limit((1+x)^(1/x),x,0))


$$\lim_{x\rightarrow 0}{\left(x+1\right)^{\frac{1}{x}}}=e$$\>$showev('limit((x/(x+k))^x,x,inf))


$$\lim_{x\rightarrow \infty }{\left(\frac{x}{x+k}\right)^{x}}=e^ {- k   }$$\>$showev('limit(sin(1/x),x,0))


$$\lim_{x\rightarrow 0}{\sin \left(\frac{1}{x}\right)}={\it ind}$$\>$showev('limit(sin(1/x),x,inf))


$$\lim_{x\rightarrow \infty }{\sin \left(\frac{1}{x}\right)}=0$$\>plot2d("sin(1/x)",-5,5):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-034.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-034.png)

# Latihan

Bukalah buku Kalkulus. Cari dan pilih beberapa (paling sedikit 5
fungsi berbeda tipe/bentuk/jenis) fungsi dari buku tersebut, kemudian
definisikan di EMT pada baris-baris perintah berikut (jika perlu
tambahkan lagi). Untuk setiap fungsi, hitung nilai limit fungsi
tersebut di beberapa nilai dan di tak hingga. Gambar grafik fungsi
tersebut untuk mengkonfirmasi nilai-nilai limit tersebut.


1. Hitunglah nilai limit berikut.


$$\lim_{x\to 3}(x-8)$$\>$showev('limit((x-8),x,3))


$$\lim_{x\rightarrow 3}{x-8}=-5$$2. Hitunglah nilai limit berikut.


$$\lim_{x\to 2}\frac{x^2-4}{x+2}$$\>$showev('limit((x^2-4)/(x=2),x,2))


$$\lim_{x\rightarrow 2}{\frac{x^2-4}{x}=\frac{x^2-4}{2}}=\left(0=0  \right)$$3. Hitunglah nilai limit berikut dan gambarlah grafiknya.


$$\lim_{t\to 1}\frac{t^2-1}{sin(t-1)}$$\>$showev('limit((t^2-1)/sin(t-1),t,1))


$$\lim_{t\rightarrow 1}{\frac{t^2-1}{\sin \left(t-1\right)}}=2$$\>(plot2d("(x^2-1)/sin(x-1)", -10,10)):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-041.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-041.png)

4. Tentukan nilai limit berikut.


$$\lim_{x\to -1}\frac{\sqrt{1-2x}}{(4x+2)^2}$$\>$showev('limit((sqrt(1-2\*x))/((4\*x+2)^2), x, -1))


$$\lim_{x\rightarrow -1}{\frac{\sqrt{1-2\,x}}{\left(4\,x+2\right)^2}}=  \frac{\sqrt{3}}{4}$$5. Tentukan nilai limit berikut.


$$\lim_{t\to 0}\frac{(t-sin(t))^2}{t^2}$$\>$showev('limit(((t-sin(t))^2)/(t^2),t,0))


$$\lim_{t\rightarrow 0}{\frac{\left(t-\sin t\right)^2}{t^2}}=0$$\>(plot2d("((x-sin(x))^2)/(x^2)",-5,5)):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-046.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-046.png)

\>  


# Turunan Fungsi

Definisi turunan:


Berikut adalah contoh-contoh menentukan turunan fungsi dengan
menggunakan definisi turunan (limit).


\>$showev('limit(((x+h)^n-x^n)/h,h,0)) // turunan x^n


$$\lim_{h\rightarrow 0}{\frac{\left(x+h\right)^{n}-x^{n}}{h}}=n\,x^{n  -1}$$Mengapa hasilnya seperti itu? Tuliskan atau tunjukkan bahwa hasil
limit tersebut benar, sehingga benar turunan fungsinya benar.  Tulis
penjelasan Anda di komentar ini.


Sebagai petunjuk, ekspansikan (x+h)^n dengan menggunakan teorema
binomial.


## BUKTI

$$f'(x) = \lim_{h\to 0} \frac{f(x+h)-f(x)}{h}$$

Untuk


$$f(x)=x^{n}$$$$\frac{d}{dx}sin(x) = \lim_{h\to 0} \frac{(x+h)^{n}-x^{n}}{h}$$

Dengan


$$(a+b)^{n}=\sum_{k=0}^n a^{k}b^{n-k}$$

maka


$$= \lim_{h\to 0} \frac{(x^{n}+\frac{n}{1!}x^{n-1}h+\frac{n(n-1)}{2!}x^{n-2}h^2+\frac{n(n-1)(n-2)}{3!}x^{n-3}h^{3}+...)-x^{n}}{h}$$$$= \lim_{h\to 0} \frac{n.x^{n-1}h+\frac{n(n-1)}{2!}x^{n-2}h^2+\frac{n(n-1)(n-2)}{3!}x^{n-3}h^{3}+...}{h}$$$$= \lim_{h\to 0} n.x^{n-1}+\frac{n(n-1)}{2!}.x^{n-2}h+\frac{n(n-1)(n-2)}{3!}.x^{n-3}h^{2}+...$$$$= n.x^{n-1}+0+0+...+0$$$$= n.x^{n-1}$$

Jadi, terbukti benar bahwa


$$f'(x^n) = n.x^{n-1}$$---

\>$showev('limit((sin(x+h)-sin(x))/h,h,0)) // turunan sin(x)


$$\lim_{h\rightarrow 0}{\frac{\sin \left(x+h\right)-\sin x}{h}}=\cos   x$$Mengapa hasilnya seperti itu? Tuliskan atau tunjukkan bahwa hasil
limit tersebut


benar, sehingga benar turunan fungsinya benar.  Tulis penjelasan Anda
di komentar ini.


Sebagai petunjuk, ekspansikan sin(x+h) dengan menggunakan rumus jumlah
dua sudut.


## Bukti

$$f'(x) = \lim_{h\to 0} \frac{sin(x+h)-sin(x)}{h}$$$$sin(a+b)=sin(a)cos(a)+cos(a)sin(b)$$$$= \lim_{h\to 0} \frac{sin(x)cos(h)+cos(x)sin(h)-sin(x)}{h}$$$$= \lim_{h\to 0} sinx.\frac{cos(h)-1}{h}+\lim_{h\to 0} cos(x).\frac{sin(h)}{h}$$$$= sin(x).0+cos(x).1$$$$= cos(x)$$Jadi, terbukti benar bahwa


$$f'(sin(x)) = cos(x)$$---

\>$showev('limit((log(x+h)-log(x))/h,h,0)) // turunan log(x)


$$\lim_{h\rightarrow 0}{\frac{\log \left(x+h\right)-\log x}{h}}=  \frac{1}{x}$$Mengapa hasilnya seperti itu? Tuliskan atau tunjukkan bahwa hasil
limit tersebut


benar, sehingga benar turunan fungsinya benar.  Tulis penjelasan Anda
di komentar ini.


Sebagai petunjuk, gunakan sifat-sifat logaritma dan hasil limit pada
bagian sebelumnya di atas.


## Bukti

$$f'(x) = \lim_{h\to 0} \frac{log(x+h)-log x}{h}$$$$=\lim_{h\to 0} \frac{\frac{d}{dh}(log(x+h)-log x)}{\frac{d}{dh}(h)}$$$$=\lim_{h\to 0} \frac{\frac{1}{x+h}}{1}$$$$=\lim_{h\to 0} \frac{1}{x+h}$$$$=\frac{1}{x}$$

Jadi, terbukti benar bahwa


$$f'(x) = \lim_{h\to 0} \frac{log(x+h)-log x}{h} = \frac{1}{x}$$---

\>$showev('limit((1/(x+h)-1/x)/h,h,0)) // turunan 1/x


$$\lim_{h\rightarrow 0}{\frac{\frac{1}{x+h}-\frac{1}{x}}{h}}=-\frac{1  }{x^2}$$\>$showev('limit((E^(x+h)-E^x)/h,h,0)) // turunan f(x)=e^x


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


$$\lim_{h\to 0}\frac{e^{x+h}-e^x}{h}.$$Oleh karena itu diperlukan trik khusus agar hasilnya benar.


\>$showev('limit((E^h-1)/h,h,0))


$$\lim_{h\rightarrow 0}{\frac{e^{h}-1}{h}}=1$$\>$factor(E^(x+h)-E^x)


$$\left(e^{h}-1\right)\,e^{x}$$\>$showev('limit(factor((E^(x+h)-E^x)/h),h,0)) // turunan f(x)=e^x


$$\left(\lim_{h\rightarrow 0}{\frac{e^{h}-1}{h}}\right)\,e^{x}=e^{x}$$\>function f(x) &= x^x


    
                                       x
                                      x
    

\>$showev('limit((f(x+h)-f(x))/h,h,0)) // turunan f(x)=x^x


$$\lim_{h\rightarrow 0}{\frac{\left(x+h\right)^{x+h}-x^{x}}{h}}=  {\it infinity}$$Di sini Maxima juga bermasalah terkait limit:


$$\lim_{h\to 0} \frac{(x+h)^{x+h}-x^x}{h}.$$Dalam hal ini diperlukan asumsi nilai x.


\>&assume(x\>0); $showev('limit((f(x+h)-f(x))/h,h,0)) // turunan f(x)=x^x


$$\lim_{h\rightarrow 0}{\frac{\left(x+h\right)^{x+h}-x^{x}}{h}}=x^{x}  \,\left(\log x+1\right)$$\>&forget(x\>0) // jangan lupa, lupakan asumsi untuk kembali ke semula


    
                                   [x &gt; 0]
    

\>&forget(x<0)


    
                                   [x &lt; 0]
    

\>&facts()


    
                                      []
    

\>$showev('limit((asin(x+h)-asin(x))/h,h,0)) // turunan arcsin(x)


$$\lim_{h\rightarrow 0}{\frac{\arcsin \left(x+h\right)-\arcsin x}{h}}=  \frac{1}{\sqrt{1-x^2}}$$\>$showev('limit((tan(x+h)-tan(x))/h,h,0)) // turunan tan(x)


$$\lim_{h\rightarrow 0}{\frac{\tan \left(x+h\right)-\tan x}{h}}=  \frac{1}{\cos ^2x}$$\>function f(x) &= sinh(x) // definisikan f(x)=sinh(x)


    
                                   sinh(x)
    

\>function df(x) &= limit((f(x+h)-f(x))/h,h,0); $df(x) // df(x) = f'(x)


$$\frac{e^ {- x }\,\left(e^{2\,x}+1\right)}{2}$$Hasilnya adalah cosh(x), karena


$$\frac{e^x+e^{-x}}{2}=\cosh(x).$$\>plot2d(["f(x)","df(x)"],-pi,pi,color=[blue,red]):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-085.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-085.png)

# Latihan

Bukalah buku Kalkulus. Cari dan pilih beberapa (paling sedikit 5
fungsi berbeda tipe/bentuk/jenis) fungsi dari buku tersebut, kemudian
definisikan di EMT pada baris-baris perintah berikut (jika perlu
tambahkan lagi). Untuk setiap fungsi, tentukan turunannya dengan
menggunakan definisi turunan (limit), seperti contoh-contoh tersebut.
Gambar grafik fungsi asli dan fungsi turunannya pada sumbu koordinat
yang sama.


1. Tentukan nilai turunan berikut dan sketsakan grafiknya.


$$f(x)=3x^2+4$$\>function f(x) &= 4\*x^2+8; $f(x)


$$4\,x^2+8$$\>function df(x) &= limit((f(x+h)-f(x))/h,h,0); &df(x)//df(x)=f'(x)


    
                                     8 x
    

\>plot2d(["f(x)","df(x)"],-pi,pi,color=[red,green]):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-088.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-088.png)

2. Carilah turunan dari fungsi berikut


$$f(x)=\frac{4x-1}{x-2}$$\>function f(x) &= (x-1)/(x-2); $f(x)


$$\frac{x-1}{x-2}$$\>function df(x) &= limit((f(x+h)-f(x))/h,h,0); $df(x) // df(x) = f'(x)


$$-\frac{1}{x^2-4\,x+4}$$\>plot2d(["f(x)","df(x)"],-10,10,color=[blue,red]):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-092.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-092.png)

3. Carilah turunan dari fungsi berikut


$$f(x)= \frac{3}{\sqrt{x-2}}$$\>function f(x) &= 3/sqrt(x-2); $f(x)


$$\frac{3}{\sqrt{x-2}}$$\>function df(x) &= limit((f(x+h)-f(x))/h,h,0); $df(x) // df(x) = f'(x)function f(x) &= 3/sqrt(x-2); $f(x)


$$-\frac{3}{2\,\left(x-2\right)^{\frac{3}{2}}}$$\>plot2d(["f(x)","df(x)"],-10,10,color=[yellow,red]):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-096.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-096.png)

4. Carilah turunan fungsi berikut.


$$f(x) = 2sin(x)+3cos(x)$$\>function f(x) &= (4\*sin(x)+6\*cos(x)); $f(x)


$$4\,\sin x+6\,\cos x$$\>function df(x) &= limit((f(x+h)-f(x))/h,h,0); &df(x)


    
                          - 2 (3 sin(x) - 2 cos(x))
    

\>plot2d(["f(x)","df(x)"],-pi,pi,color=[blue,yellow]):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-099.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-099.png)

5. Tentukan turunan dan grafik fungsi berikut.


$$f(x) = \frac{sin(x)+cos(x)}{cos(x)}$$\>function f(x) &= (sin(x)+cos(x))/(cos(x)); $f(x)


$$\frac{\sin x+\cos x}{\cos x}$$\>function df(x) &= limit((f(x+h)-f(x))/h,h,0); $df(x) // df(x) = f'(x)


$$\frac{\sin ^2x+\cos ^2x}{\cos ^2x}$$\>plot2d(["f(x)","df(x)"],-pi,pi,color=[blue,yellow]):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-103.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-103.png)

\>    


# Integral

EMT dapat digunakan untuk menghitung integral, baik integral tak tentu
maupun integral tentu. Untuk integral tak tentu (simbolik) sudah tentu
EMT menggunakan Maxima, sedangkan untuk perhitungan integral tentu EMT
sudah menyediakan beberapa fungsi yang mengimplementasikan algoritma
kuadratur (perhitungan integral tentu menggunakan metode numerik).


Pada notebook ini akan ditunjukkan perhitungan integral tentu dengan
menggunakan Teorema Dasar Kalkulus:


$$\int_a^b f(x)\ dx = F(b)-F(a), \quad \text{ dengan  } F'(x) = f(x).$$Fungsi untuk menentukan integral adalah integrate. Fungsi ini dapat
digunakan untuk menentukan, baik integral tentu maupun tak tentu (jika
fungsinya memiliki antiderivatif). Untuk perhitungan integral tentu
fungsi integrate menggunakan metode numerik (kecuali fungsinya tidak
integrabel, kita tidak akan menggunakan metode ini).


\>$showev('integrate(x^n,x))


    Answering "Is n equal to -1?" with "no"

$$\int {x^{n}}{\;dx}=\frac{x^{n+1}}{n+1}$$\>$showev('integrate(1/(1+x),x))


$$\int {\frac{1}{x+1}}{\;dx}=\log \left(x+1\right)$$\>$showev('integrate(1/(1+x^2),x))


$$\int {\frac{1}{x^2+1}}{\;dx}=\arctan x$$\>$showev('integrate(1/sqrt(1-x^2),x))


$$\int {\frac{1}{\sqrt{1-x^2}}}{\;dx}=\arcsin x$$\>$showev('integrate(sin(x),x,0,pi))


$$\int_{0}^{\pi}{\sin x\;dx}=2$$\>$showev('integrate(sin(x),x,a,b))


$$\int_{a}^{b}{\sin x\;dx}=\cos a-\cos b$$\>$showev('integrate(x^n,x,a,b))


    Answering "Is n positive, negative or zero?" with "positive"

$$\int_{a}^{b}{x^{n}\;dx}=\frac{b^{n+1}}{n+1}-\frac{a^{n+1}}{n+1}$$\>$showev('integrate(x^2\*sqrt(2\*x+1),x))


$$\int {x^2\,\sqrt{2\,x+1}}{\;dx}=\frac{\left(2\,x+1\right)^{\frac{7  }{2}}}{28}-\frac{\left(2\,x+1\right)^{\frac{5}{2}}}{10}+\frac{\left(  2\,x+1\right)^{\frac{3}{2}}}{12}$$\>$showev('integrate(x^2\*sqrt(2\*x+1),x,0,2))


$$\int_{0}^{2}{x^2\,\sqrt{2\,x+1}\;dx}=\frac{2\,5^{\frac{5}{2}}}{21}-  \frac{2}{105}$$\>$ratsimp(%)


$$\int_{0}^{2}{x^2\,\sqrt{2\,x+1}\;dx}=\frac{2\,5^{\frac{7}{2}}-2}{  105}$$\>$showev('integrate((sin(sqrt(x)+a)\*E^sqrt(x))/sqrt(x),x,0,pi^2))


$$\int_{0}^{\pi^2}{\frac{\sin \left(\sqrt{x}+a\right)\,e^{\sqrt{x}}}{  \sqrt{x}}\;dx}=\left(-e^{\pi}-1\right)\,\sin a+\left(e^{\pi}+1  \right)\,\cos a$$\>$factor(%)


$$\int_{0}^{\pi^2}{\frac{\sin \left(\sqrt{x}+a\right)\,e^{\sqrt{x}}}{  \sqrt{x}}\;dx}=\left(-e^{\pi}-1\right)\,\left(\sin a-\cos a\right)$$\>function map f(x) &= E^(-x^2)


    
                                        2
                                     - x
                                    E
    

\>$showev('integrate(f(x),x))


$$\int {e^ {- x^2 }}{\;dx}=\frac{\sqrt{\pi}\,\mathrm{erf}\left(x  \right)}{2}$$Fungsi f tidak memiliki antiturunan, integralnya masih memuat integral
lain.


$$erf(x) = \int \frac{e^{-x^2}}{\sqrt{\pi}} \ dx.$$Kita tidak dapat menggunakan teorema Dasar kalkulus untuk menghitung
integral tentu fungsi tersebut jika semua batasnya berhingga. Dalam
hal ini dapat digunakan metode numerik (rumus kuadratur).


Misalkan kita akan menghitung:


$$\int_{0}^{\pi}{e^ {- x^2 }\;dx}$$\>x=0:0.1:pi-0.1; plot2d(x,f(x+0.1),\>bar); plot2d("f(x)",0,pi,\>add):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-120.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-120.png)

Integral tentu


$$\int_{0}^{\pi}{e^ {- x^2 }\;dx}$$dapat dihampiri dengan jumlah luas persegi-persegi panjang di bawah
kurva y=f(x) tersebut. Langkah-langkahnya adalah sebagai berikut.


\>t &= makelist(a,a,0,pi-0.1,0.1); // t sebagai list untuk menyimpan nilai-nilai x

\>fx &= makelist(f(t[i]+0.1),i,1,length(t)); // simpan nilai-nilai f(x)

\>// jangan menggunakan x sebagai list, kecuali Anda pakar Maxima!


Hasilnya adalah:


$$\int_{0}^{\pi}{e^ {- x^2 }\;dx}=0.8362196102528469$$Jumlah tersebut diperoleh dari hasil kali lebar sub-subinterval (=0.1)
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


$$\int_{0}^{\infty }{e^ {- x^2 }\;dx}=\frac{\sqrt{\pi}}{2}$$Berikut adalah contoh lain fungsi yang tidak memiliki antiderivatif, sehingga
integral tentunya hanya dapat dihitung dengan metode numerik.


\>function f(x) &= x^x


    
                                       x
                                      x
    

\>$showev('integrate(f(x),x,0,1))


$$\int_{0}^{1}{x^{x}\;dx}=\int_{0}^{1}{x^{x}\;dx}$$\>x=0:0.1:1-0.01; plot2d(x,f(x+0.01),\>bar); plot2d("f(x)",0,1,\>add):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-125.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-125.png)

Maxima gagal menghitung integral tentu tersebut secara langsung menggunakan perintah
integrate. Berikut kita lakukan seperti contoh sebelumnya untuk mendapat hasil atau
pendekatan nilai integral tentu tersebut.


\>t &= makelist(a,a,0,1-0.01,0.01);

\>fx &= makelist(f(t[i]+0.01),i,1,length(t));


$$\int_{0}^{1}{x^{x}\;dx}=0.7834935879025506$$Apakah hasil tersebut cukup baik? perhatikan gambarnya.


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


$$V = \int_a^b \pi (f(x)^2\ dx.$$(Pilih fungsinya dan gambar kurva dan benda putar yang dihasilkan.
Anda dapat mencari contoh-contoh bagaimana cara menggambar benda hasil
perputaran suatu kurva.)


- Gunakan integral tentu untuk menghitung panjang kurva y=f(x) dari
x=a sampai x=b dengan menggunakan rumus:


$$S = \int_a^b \sqrt{1+(f'(x))^2} \ dx.$$(Pilih fungsi dan gambar kurvanya.)


1. Tentukan panjang kurva dan volume benda putar kurva y=f(x) yang
diputar mengelilingi sumbu x dari x=0 sampai x=4


$$f(x)= x^3$$\>function f(x)&=x^3; $f(x)


$$x^3$$\>$showev('integrate(pi\*(f(x))^2,x,0,4))


$$\pi\,\int_{0}^{4}{x^6\;dx}=\frac{16384\,\pi}{7}$$turunan fungsi f(x)


\>function df(x) &= limit((f(x+h)-f(x))/h,h,0); $df(x) // df(x) = f'(x)


$$3\,x^2$$panjang kurva


\>$showev('integrate(sqrt((1+df(x)^2)),x,0,4))


$$\int_{0}^{4}{\sqrt{9\,x^4+1}\;dx}=\int_{0}^{4}{\sqrt{9\,x^4+1}\;dx}$$grafik benda putar mengelilingi sumbu x


\> plot3d("x^3",2,0,2,rotate=2):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-134.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-134.png)

2. Tentukan panjang kurva dan volume benda putar kurva y=f(x) yang
diputar mengelilingi sumbu x dari x=-1 sampai x=2


$$f(x) = 3x^2+2x+1$$volume benda putar


\>function f(x)&=3\*x^2+2\*x+1; $f(x) 


$$3\,x^2+2\,x+1$$\>$showev('integrate(pi\*(f(x))^2,x,-1,2))


$$\pi\,\int_{-1}^{2}{\left(3\,x^2+2\,x+1\right)^2\;dx}=\frac{717\,\pi  }{5}$$menentukan turunan fungsi f(x)


\>function df(x) &= limit((f(x+h)-f(x))/h,h,0); $df(x) // df(x) = f'(x)


$$6\,x+2$$menentukan panjang kurva


\>$showev('integrate(sqrt((1+df(x)^2)),x,-1,2))


$$\int_{-1}^{2}{\sqrt{\left(6\,x+2\right)^2+1}\;dx}=\frac{  {\rm asinh}\; 14+14\,\sqrt{197}}{12}+\frac{{\rm asinh}\; 4+4\,\sqrt{  17}}{12}$$menggambar plot benda putar mengelilingi sumbu x


\>plot3d("3x^2+2x+1",2,-1,2,rotate=2):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-140.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-140.png)

3. Integral tentu dengan batas [-1,1] dari fungsi berikut


$$f(x)=x^2+8x-9$$\>function map f(x) &= (x^2+8\*x-9); $f(x)


$$x^2+8\,x-9$$mencari nilai dari integral tentu fungsi f(x) dengan batas [-1,1]


\>$showev('integrate(f(x), x, -1, 1))


$$\int_{-1}^{1}{x^2+8\,x-9\;dx}=-\frac{52}{3}$$4. Tentukan panjang kurva dan volume benda putar kurva y=f(x) yang
diputar mengelilingi sumbu x dari x=0 sampai x=2


\>$showev('integrate(pi\*(f(x))^2,x,0,2))


$$\pi\,\int_{0}^{2}{\left(x^2+8\,x-9\right)^2\;dx}=\frac{1006\,\pi}{  15}$$\>function df(x) &= limit((f(x+h)-f(x))/h,h,0); $df(x) // df(x) = f'(x)


$$2\,x+8$$menentukan pangjang kurva


\>$showev('integrate(sqrt((1+df(x)^2)),x,0,2))


$$\int_{0}^{2}{\sqrt{\left(2\,x+8\right)^2+1}\;dx}=\frac{  {\rm asinh}\; 12+12\,\sqrt{145}}{4}-\frac{{\rm asinh}\; 8+8\,\sqrt{  65}}{4}$$menggambar plot


\>plot3d("4x^2+1",2,0,2,rotate=2):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-147.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-147.png)

5. Tentukan integral fungsi berikut.


$$f(x)= \frac{\sqrt{2x}}{x}+\frac{3}{x^5}$$\>function f(x) &= (sqrt(2\*x))/x +3/x^5 ; $f(x)


$$\frac{\sqrt{2}}{\sqrt{x}}+\frac{3}{x^5}$$\>$showev('integrate((((sqrt(2\*x))/x) +(3/x^5)),x))


$$\int {\frac{\sqrt{2}}{\sqrt{x}}+\frac{3}{x^5}}{\;dx}=2^{\frac{3}{2}  }\,\sqrt{x}-\frac{3}{4\,x^4}$$\>x=0:0.1:5-0.1; plot2d(x,f(x+0.1),\>bar); plot2d("f(x)",0,5,\>add):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-151.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-151.png)

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

\>sum(1:2:30), sum(1/(1:2:30))


    225
    2.33587263431

\>$'sum(k, k, 1, n) = factor(ev(sum(k, k, 1, n),simpsum=true)) // simpsum:menghitung deret secara simbolik


$$\sum_{k=1}^{n}{k}=\frac{n\,\left(n+1\right)}{2}$$\>$'sum(1/(3^k+k), k, 0, inf) = factor(ev(sum(1/(3^k+k), k, 0, inf),simpsum=true))


$$\sum_{k=0}^{\infty }{\frac{1}{3^{k}+k}}=\sum_{k=0}^{\infty }{\frac{  1}{3^{k}+k}}$$Di sini masih gagal, hasilnya tidak dihitung.


\>$'sum(1/x^2, x, 1, inf)= ev(sum(1/x^2, x, 1, inf),simpsum=true) // ev: menghitung nilai ekspresi


$$\sum_{x=1}^{\infty }{\frac{1}{x^2}}=\frac{\pi^2}{6}$$\>$'sum((-1)^(k-1)/k, k, 1, inf) = factor(ev(sum((-1)^(x-1)/x, x, 1, inf),simpsum=true))


$$\sum_{k=1}^{\infty }{\frac{\left(-1\right)^{k-1}}{k}}=-\sum_{x=1}^{  \infty }{\frac{\left(-1\right)^{x}}{x}}$$Di sini masih gagal, hasilnya tidak dihitung.


\>$'sum((-1)^k/(2\*k-1), k, 1, inf) = factor(ev(sum((-1)^k/(2\*k-1), k, 1, inf),simpsum=true))


$$\sum_{k=1}^{\infty }{\frac{\left(-1\right)^{k}}{2\,k-1}}=\sum_{k=1  }^{\infty }{\frac{\left(-1\right)^{k}}{2\,k-1}}$$\>$ev(sum(1/n!, n, 0, inf),simpsum=true)


$$\sum_{n=0}^{\infty }{\frac{1}{n!}}$$Di sini masih gagal, hasilnya tidak dihitung, harusnya hasilnya e.


\>&assume(abs(x)<1); $'sum(a\*x^k, k, 0, inf)=ev(sum(a\*x^k, k, 0, inf),simpsum=true), &forget(abs(x)<1);


$$a\,\sum_{k=0}^{\infty }{x^{k}}=\frac{a}{1-x}$$Deret geometri tak hingga, dengan asumsi rasional antara -1 dan 1.


\> 


# Deret Taylor

Deret Taylor suatu fungsi f yang diferensiabel sampai tak hingga di sekitar x=a adalah:


\>$'e^x =taylor(exp(x),x,0,10) // deret Taylor e^x di sekitar x=0, sampai suku ke-11


$$e^{x}=\frac{x^{10}}{3628800}+\frac{x^9}{362880}+\frac{x^8}{40320}+  \frac{x^7}{5040}+\frac{x^6}{720}+\frac{x^5}{120}+\frac{x^4}{24}+  \frac{x^3}{6}+\frac{x^2}{2}+x+1$$\>$'log(x)=taylor(log(x),x,1,10)// deret log(x) di sekitar x=1


$$\log x=x-\frac{\left(x-1\right)^{10}}{10}+\frac{\left(x-1\right)^9  }{9}-\frac{\left(x-1\right)^8}{8}+\frac{\left(x-1\right)^7}{7}-  \frac{\left(x-1\right)^6}{6}+\frac{\left(x-1\right)^5}{5}-\frac{  \left(x-1\right)^4}{4}+\frac{\left(x-1\right)^3}{3}-\frac{\left(x-1  \right)^2}{2}-1$$# Fungsi Multivariabel

Fungsi multivariabel adalah sebuah konsep dalam matematika yang
menggambarkan hubungan antara satu variabel output dengan dua atau
lebih variabel input. Berbeda dengan fungsi satu variabel yang hanya
melibatkan satu variabel bebas, fungsi multivariabel melibatkan
beberapa variabel bebas yang secara bersama-sama menentukan nilai dari
variabel terikat. Fungsi multivariabel biasanya digunakan untuk
menggambarkan hubungan yang kompleks dalam bidang seperti fisika,
ekonomi, teknik, dan berbagai ilmu lainnya.


Secara umum, jika f adalah sebuah fungsi multivariabel, maka bentuk
umumnya dapat dinyatakan sebagai:


$$z=f(x_1,x_2,...,x_n)$$

dimana x1,x2,...,xn adalah variabel bebas (input) menunjukkan jumlah
variabel dan z adalah variable terikat (output).


contoh :


Luas Persegi Panjang: Luas persegi panjang (L) adalah fungsi dari
panjang (p) dan lebar (l). Kita dapat menuliskannya sebagai L(p, l) =
p * l. Di sini, L adalah variabel terikat, sedangkan p dan l adalah
variabel bebas.


Diberikan fungsi:


$$x^2+2xy+y^2$$\>function f(x,y) &= x^6 + 4\*x\*y + y^3


    
                                3            6
                               y  + 4 x y + x
    

diff(f,x): Bagian ini untuk menghitung turunan numerik.


f: Merupakan representasi dari fungsi yang ingin kita turunkan. Fungsi
ini bisa berupa fungsi anonim, fungsi yang telah didefinisikan
sebelumnya, atau bahkan persamaan matematika yang kompleks.


x: Menunjukkan variabel terhadap mana kita akan menurunan fungsi f.
Artinya, kita akan mencari laju perubahan fungsi f terhadap perubahan
nilai x.


&amp;=: mendefinikan fungsi, seperti yang sudah dijelaskan kemarin


\>fx &= diff(f(x,y),x)


    
                                           5
                                  4 y + 6 x
    

ini merupakan fungsi simbolik jadi harus didefinisikan dengan &amp;=


\>fy &= diff(f(x,y),y)


    
                                     2
                                  3 y  + 4 x
    

\>plot3d("f", -3,3, -3,3) :


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-163.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-163.png)

menggunakan fungsi f yang telah didefinisikan di atas.


# Turunan fungsi multivariabel

Diberikan fungsi:


$$\sqrt{x}+y^4+7xz$$\>function f(x,y,z)&= sqrt(x)+y^4+7\*x\*z


    
                                      4
                             7 x z + y  + sqrt(x)
    

\>fx &= diff(f(x,y,z),x)


    
                                         1
                               7 z + ---------
                                     2 sqrt(x)
    

\>fy &= diff(f(x,y,z),y)


    
                                        3
                                     4 y
    

\>fz &= diff(f(x,y,z),z)


    
                                     7 x
    

Diberikan fungsi


$$x^5+8y^2-9x+2$$\>function g(x,y) &= x^5+8\*y^2-9\*x+2


    
                                2    5
                             8 y  + x  - 9 x + 2
    

menentukan dg/dx


\>gx &= diff(g(x,y),x)


    
                                      4
                                   5 x  - 9
    

menentukan dg/dy


\>gy &= diff(g(x,y),y)


    
                                     16 y
    

\>grad &= [diff(g(x,y),x), diff(g(x,y),y)]


    
                                   4
                               [5 x  - 9, 16 y]
    

Contoh Trigonometri


Diberikan fungsi:


$$\frac{3sin(x)^5}{sin(x)+cos(x)}+tan (y)^4$$tentukan df/dx, df/dy, dan df/dz!


\>function f(x,y,z)&= 3\*sin(x)^5/(sin(x)+cos(z))+tan(y)^4;

\>$fx := diff(f(x,y,z),x)


$$\frac{15\,\cos x\,\sin ^4x}{\cos z+\sin x}-\frac{3\,\cos x\,\sin ^5  x}{\left(\cos z+\sin x\right)^2}$$\>$fy := diff(f(x,y,z),y)


$$4\,\sec ^2y\,\tan ^3y$$\>$fz := diff(f(x,y,z),z)


$$\frac{3\,\sin ^5x\,\sin z}{\left(\cos z+\sin x\right)^2}$$# Grafik 

Grafik fungsi multivariabel adalah representasi visual dari fungsi
yang memiliki dua atau lebih variabel input. Untuk fungsi dua variabel
$f(x,y)$, grafiknya berupa permukaan dalam ruang tiga dimensi.


Bidang z = 2x + 3y


\>plot3d("2\*x + 3\*y", -2,2, -2,2):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-170.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-170.png)

\>title("Kontur z = 2x + 3y"):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-171.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-171.png)

Paraboloid z = x^4 + y^4


\>plot3d("x^4 + y^4", -4,2, -4,2):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-172.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-172.png)

Hyperbolic Paraboloid


$$z = x^3 - y^3$$\>plot3d("x^3 - y^3", -3,3, -3,3):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-174.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-174.png)

z = sin(sqrt(x^2 + y^2))


\>plot3d("sin(sqrt(x^2 + y^2))", -4\*pi,4\*pi, -4\*pi,4\*pi):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-175.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-175.png)

Distribusi normal bivariat


\>plot3d("(8/(3\*pi))\*exp(-(x^5+y^3)/4)", -4,3, -4,3):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-176.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-176.png)

# Turunan 

Turunan fungsi multivariabel merupakan perluasan konsep turunan dari
fungsi satu variabel ke fungsi dengan dua atau lebih variabel.


menghitung turunan parsial


\>f &= x^2 + 4\*x\*y + y^3


    
                                3            2
                               y  + 4 x y + x
    

\>plot3d("x^2 + 4\*x\*y + y^3", -2.2, -2.2):


![images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-177.png](images/Achmad%20Nuril%20Dimas%20Effendy_23030630059_EMT4Kalkulus-177.png)

\>f &= x^2 + y^3


    
                                    3    2
                                   y  + x
    

\>grad &= [diff(f,x), diff(f,y)]


    
                                          2
                                 [2 x, 3 y ]
    

Menghitung turunan parsial kedua


\>f &= x^5 + 6\*x\*y + y^4


    
                                4            5
                               y  + 6 x y + x
    

\>fxy &= diff(diff(f,x),y)


    
                                      6
    

# Integral 

Integral fungsi multivariabel adalah perluasan konsep integral dari
fungsi satu variabel ke fungsi dengan dua atau lebih variabel.


Contoh sederhana integral lipat dua


\>$showev ('integrate(integrate(x^7 + y^5, x, 3, 1), y, 5, 2))


$$-\int_{2}^{5}{\frac{8\,y^5+1}{8}-\frac{24\,y^5+6561}{8}\;dy}=7647$$Hasil dari integral ganda ini akan memberikan nilai total area di
bawah permukaan fungsi


f(x,y)=x^7+y^5 di daerah persegi yang ditentukan.


\>$showev('integrate(integrate(9\*x^6\*y - 7\*x\*y^2, x, 0, 1), y, 1, 2))


$$-\frac{\int_{1}^{2}{49\,y^2-18\,y\;dy}}{14}=-\frac{131}{21}$$Contoh ini menunjukkan bagaimana integral ganda bekerja pada fungsi
multivariabel.


Integral Ganda: Fungsi Eksponensial


\>$showev('integrate(integrate(exp(x) \* exp(y), x, 0, 1), y, 0, 2))


$$\int_{0}^{2}{e^{y+1}-e^{y}\;dy}=e^3-e^2-e+1$$Integral Ganda: Fungsi Trigonometri


\>$showev('integrate(integrate(sin(x) \* cos(y), x, 0, pi), y, 0, pi/2))


$$2\,\int_{0}^{\frac{\pi}{2}}{\cos y\;dy}=2$$ Integral Ganda: Fungsi Kuadrat  

\>$showev('integrate(integrate(x^8 + y^7, x, 3, 2), y, 2, 3))


$$\int_{2}^{3}{\frac{18\,y^7+512}{9}-3\,y^7-2187\;dy}=-\frac{210113}{  72}$$# Aplikasinya

1. Misalkan medan listrik di suatu daerah diberikan oleh


$$E(x,y)=x^5 - y^3$$

Hitung fluks medan listrik melalui permukaan persegi panjang
[4,3]�[2,1]!


\>$showev('integrate(integrate(x^5 - y^3, x, 4, 3), y, 2, 1))


$$-\int_{1}^{2}{\frac{12\,y^3-2048}{3}-\frac{6\,y^3-243}{2}\;dy}=  \frac{6689}{12}$$kita diberikan medan listrik dalam bentuk vektor


$$E(x,y)=x^5-y^3$$

dan diminta untuk menghitung fluks dari medan listrik melalui
permukaan tersebut.


$$x=4-3$$$$y=2-1$$