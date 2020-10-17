# Neural-Qubits

KTHack2020 - Kuantum Teknolojileri Hackathonu Akademi Kategorisi Birincisi

Grup Üyeleri:

〈 ALARA | ZINDANCIOĞLU 〉

〈 BAŞAK | EKINCI 〉

〈 ENES | BAŞPINAR 〉

〈 TOGAN | TLIMAKHOV | YUSUF 〉

------------------------------------------------------------------------------------------------------------------------------------

**Özet**

Makine öğrenmesi, bilgisayar bilimi ve mühendislikteki en büyük araştırma alanlarından birisidir. Askeri, endüstri, güvenlik, robotik ve astronomi gibi bir çok alanda çok önem arz eden bir teknolojidir. Öte yandan kuantum programlama ise insanların hayatına çok kısa bir süre önce giriş yapan yeni bir alandır. Yapılan öngörülere göre klasik bilgisayarlardaki transistörlerin boyutu daha fazla küçültülemeyeceği için gelişim kısa bir zaman içinde mümkün olmayan bir hale gelecek ve bu yüzden de kuantum bilgisayarlar ön plana çıktı. 
Bunun sonucunda insanlar, klasik bilgisayarların kullanıldığı uygulamaların hangilerinde kuantum bilgisayarların daha verimli olabileceğini araştırmaya başladı. Bir çok alanda yapılan bu araştırmalar, elbette makine öğrenmesi alanına da sıçradı. Dünyanın dört bir yanında insanlar farklı modellerin, yöntemlerin ve algoritmaların kuantum programlamaya aktarmaya çalıştı ve performanslarını değerlendirdi. Bazı noktalarda ise klasik bilgisayarlarda yapılan hesaplama tekniklerine göre performans ve hız açısından daha verimli olduğu keşfedildi.
Biz de hackathon konumuzu bu sebeplerden dolayı, kuantum programlama içerisindeki önemi üst sıralarda yer alan makine öğrenmesi alanında seçtik. Projemize küçük adımlarla başladık. Öncelikle Neural Network’ü kuantum programlamaya uyarladık (QNN). Sonrasında modelimizi, verilerimizin kuantum devrelerine çevrilmesi aşamasına katkı sağlayacak ve klasik sinyal ve görüntü işlemede kullanılan en önemli algoritmalardan biri olan Fourier algoritmasıyla zenginleştirdik. Bunları yaparken edindiğimiz bilgiler ile projemizdeki en önemli noktası olan Convolutional Neural Network modelini, kuantum programlama için sıfırdan inşa ettik (QCNN) ve hackathonu tamamladık.

------------------------------------------------------------------------------------------------------------------------------------

**Proje Detayları**

Projenin başında ekipçe kuantum programlama ile ilgili bilgilerimiz çok yüzeyseldi. Bu yüzden, öncelikle kuantum programlamaya dair eksiklerimizi kapatarak başladık.  

Öncelikle basit bir Quantum Neural Network (QNN) oluşturmaya karar verdik. Bu kısımda karşımıza çıkan ilk aşama verilerin kübitler şekline dönüştürülmesi oldu. Bildiğimiz üzere kübitlerin başlangıç değerleri sıfırdır. Kübitler ile pikselleri ifade edebilmemiz için resimlerdeki piksellerin değerlerini eşik değerlere göre ikili (0 ve 1) hale dönüştürdük. MNIST verisetindeki resimler 28x28 olduğu için 784 kübite ihtiyacımız olacaktı. Ancak kuantum bilgisayarı simülatörlerinde mümkün olduğunca az kübit kullanmamız gerektiği için resimlerin, diğer değerleri de denedikten sonra, 3x3 piksele düşürmemizin en iyisi olacağına karar verdik. Tensorflow’daki resim küçültme işlemi piksellerin ortalamalarını alarak sıkıştırma işlemi yaptığı için sınıflandırma yaparken modelimizin performansını klasiğe göre düşürse de çok fazla problem yaşatmadı. Ve bu sayede her resmi 9 kübit ile saklayabilecektik. Bit değerlerini kübitlere aktarmak için resim başına bir tane devre oluşturduk. Artık her bir devremizin sonucu bizim için bir resmi ifade edecek hale geldi. Ardından modelimizi oluşturduk ve Keras içerisinde bulunan PQC katmanını ekledik. Bu katman, modele verdiğimiz resmi işleyen ve sonucu readout isimli kübite aktarma işlemini gerçekleştirir. Modelde kullandığımız Hinge kayıp fonksiyonu sayesinde tahminimiz -1 veya 1 değerini alır. Başlangıçta ise -1 değerini 6 rakamının sınıfını, 1 değerini 3 rakamının sınıfını ifade edecek şekilde belirlediğimizden dolayı, tahmin yaparken bunu göz önünde bulundurduk. Son olarak tahminlerimizi gerçekleştirdik. Modelimizin eğitimi 29 saniye sürdü. Temel parametrelerden epoch=3, batch-size=32 ayarlandığında en yüksek doğruluk olan ~0.83 değeri elde edildi.    

Çalışmamızın bir sonraki aşamasında QNN algoritmasında fourier dönüşümü kullanarak, bu algoritmayı geliştirmeye çalıştık. Fourier dönüşümü, sinyal ve görüntü işlemede kullanılan en önemli algoritmalardan biri iken, aynı zamanda modern kuantum algoritmalarının çoğunda da önemli bir bileşen olarak kabul edilmektedir. Literatürde yapılan çalışmaları incelediğimizde, kuantum hesaplamalarda görüntüleri kübit olarak sunmanın bir kaç yolu bulunduğunun gördük. Bunlardan Flexible Representation of quantum images olarak adlandırılan, fourier dönüşümünü temel alarak görüntüleri kübit olarak sunmamıza yarayan yöntemi kullandık. 3x3 ve 4x4 boyutlu resimlere ayrı ayrı bu yöntemi uygulayarak sonuçlarımızın sadece qnn algoritmasın kullnılmasıyla elde edilen sonuçlarla hemen hemen aynı oranda doğrulukla elde ettiğimizde gördük, ileride bu yöntemi nasıl iyileştireceğimiz yönünde çalışmalar yapmaya devam etmek istiyoruz.  

QNN modelinde olgunlaştıktan sonra resim sınıflandırmada çokça kullanılan Convolutional Neural Network (CNN) modelini kuantum programlama ile inşa etmeyi planladık. Araştırdığımız makalelerden gördüğümüz kadarıyla inşa edilen Quantum Convolutional Network (QCNN) modellerinde, kuantum algoritmaları ile yazılan convolutional filtrelerin resmin ön işlemesini yapmak için ve yahut klasik CNN modelleri ile birleştirilerek eğitildiğini gördük. Resimleri QCNN algoritmasına girdi olarak verebilmemiz için, her piksel değerini kuantum durumuna dönüştürmemiz gerekiyordu. QNN modelinde olduğu gibi, resimlerin piksel sayısının çok fazla olması kuantum modelinin eğitilmesine izin vermeyeceği için verisetimizdeki tüm resimleri 6x6’lık piksele indirip resimlerin ortasındaki 4x4’lük kısmı kullandık. Ve her resim için 16 kübitlik devre kurduk. İlk modelimizde bu resimleri, 1x2 boyutundaki Quantum Convolutional filtreden geçirdik. Bu model de MNIST verisetindeki 3 ve 6 sayılarında sınıflandırma yapılarak test edildi. Eğitim için her birinden 100 resim, test için ise 20 resim kullanıldı. Eğitimi sonucunda ise ~0.81 doğruluk oranına ulaştık. Geliştirdiğimiz diğer bir QCNN modelinde ise yine 4x4’lük resimler kullanıp bu sefer 2x2 boyutunda Convolutional filtreler uyguladık ve iki katmanlık bir model oluşturduk. Yine MNIST verisetindeki 3 ve 6 sayılarında eğitip test ettiğimiz modelimiz ~0.85 doğruluk oranına ulaştı. QCNN modelini tamamen kuantum programlama ile ifade etmemiz, projede elde ettiğimiz en önemli kazanım oldu. 

------------------------------------------------------------------------------------------------------------------------------------

**Sonuç**

Hackathona, kuantum programlama ile ilgili çok az, kuantum makine öğrenmesi ile ilgili ise hiçbir deneyimi olmayan ve öncesinde birbirini tanımayan 4 kişi olarak başladık. 48 saatlik bu maratonda ekip olarak çok iyi bir iletişim kurduk. Bunun sonucunda, Hackathon Discord’dundaki en aktif gruplardan olduk ve haftasonumuzu oldukça eğlenceli geçirdik. Hackathonlarda araştırmalar oldukça yoğun geçtiğinden dolayı kuantum programlamanın birçok alanıyla ilgili güzel bir deneyim edindik. Ve bu deneyimi, bilmediğimiz bir alanda geçirdiğimiz 48 saat içindeki isteğimiz ve gayretimiz ile akademi kategorisinde aldığımız birincilik ile süsledik. Heyecanımızın hiç eksilmediği bu Hackathonu organize eden QTurkey'e teşekkürlerimizi sunarız, rekabet ettiğimiz takımları da tebrik ederiz.

------------------------------------------------------------------------------------------------------------------------------------

**Referanslar**

[1] https://pennylane.ai/qml/demos/tutorial_quanvolution.html
[2] https://www.tensorflow.org/quantum/tutorials/
[3] Implementation and Analysis of Quantum Fourier Transform in ImageProcessing
[4] P. Le, F. Dong, and K. Hirota, "A flexible representation of quantum images for polynomialpreparation, image compression, and processing operations," Quantum InformationProcessing, vol. 10, no. 1, pp. 63-84, 2011
[5] Y. Zhang, K. Lu, Y. Gao, and M. Wang, "NEQR: a novel enhanced quantum representation ofdigital images," Quantum Information Processing, vol. 12, no. 8, pp. 2833-2860, 2013.
[6] Performing Quantum Computer Vision Tasks onIBM Quantum Computers and Simulators
[7] Implementation and Analysis of Quantum Fourier Transform in Image Processing, Ola Al-Ta’ani, Ali Mohammad Alqudah, Manal Al-Bzoor
[8] Quantum neural network, M.V.Altaisky
[9] Learning the quantum algorithm for state overlap, Lukasz Cincio, Yiğit Subaşı, Andrew T. Sornborger, Patrick J. Coles
[10] Quantum Natural Gradient, James Stokes, Josh Izaac, Nathan Killoran, Giuseppe Carleo
[11] Classification with Quantum Neural Networks on Near Term Processors, Edward Farhi, Hartmut Neven
[12] Image Processing in Quantum Computers, Aditya Dendukuri, Khoa Luu
[13] Quantum Image Processing and Its Application to Edge Detection: Theory and Experiment, Xi-Wei Yao, Hengyan Wang, Zeyang Liao, Ming-Cheng Chen, Jian Pan, Jun Li, Kechao Zhang, Xingcheng Lin, Zhehui Wang, Zhihuang Luo, Wenqiang Zheng, Jianzhong Li, Meisheng Zhao, Xinhua Peng, Dieter Suter

