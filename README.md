# Neural-Qubits
KTHack2020 - KUANTUM PROGRAMLAMA HACKATHONU 

Grup Üyeleri:

〈 ALARA | ZINDANCIOĞLU 〉

〈 BAŞAK | EKINCI 〉

〈 ENES | BAŞPINAR 〉

〈 TOGAN | TLIMAKHOV | YUSUF 〉




**Özet**

Görüntü işleme, bilgisayar bilimi ve mühendislikte en büyük araştırma alanlardan biridir. Askeri Endüstri, Güvenlik, Robotik, astronomi, gibi bir çok insan hayatını doğrudan etkileyen uygulamalarla yakından ilgilendiren bir teknoloji haline geldi.

Bu bağlamda kuantum görüntü işlemeye (QImP) artan bir ilgi var. Bunun nedeni, kuantum hesaplamanın, klasik hesaplama tekniklerine göre performans ve hız açısından daha verimli olmasıdır.

Fourier dönüşümü, klasik sinyal ve görüntü işlemede kullanılan en önemli algoritmalardan biridir, aynı zamanda son geliştirilen kuantum algoritmalarında önemli bir bileşen olarak kullanıma girmiştir. klasikten farklı olarak, Kuantum Fourier dönüşümü, verilerin olasılık genliklerine kodlandığı bir kuantum durumunu kulanmasıdır.

Kuantum bilgisayarlar, Kuantum süperpozisyonu ve kuantum dolaşıklığı özelliklerinden yararlandiğindan, Logic işlemlerinde aynı anda 0 ve 1〈 0 | 1 〉değerlerini alabiliyor. Bu nedenle kuantum bilgisayarlar temel bilgi birimi olan bit yerine Qubit ile çalışıp, belirli hesaplamalarda klasik bilgisayarlardan katlanarak daha hızlı olduğu kanıtlanmıştır.




------------------------------------------------------------------------------------------------------------------------------------
**Açıklama**

Fourier analizi makine öğrenmesinde karmaşık olan bir verinin, boyutlarının azaltılarak daha basit bir problem olarak incelenmesi için oolanak sağlamaktadır. Çalışmamızda verilen bir resmin pixel gösterimini elde edebilmek için fourier temelli Flexible Representation of Quantum Images (FRQI) yöntemi kullanarak sağlanmıştır.

Bu yöntem nxn piksel ile verilen bir resmin log2(m) qubit olarak gösterilmesini sağlamaktadır.

Projemizde yapay zeka ile resim işlemede çokça kullanılan Convolutional Neural Network(CNN) modellerini quantum algoritmaları ile yazmayı planladık. Şimdiye kadar yapılan Quantum Convolutional Network (Q-CNN) modellerinde, kuantum algoritmaları ile yazılan convolutional filtrelerin ya resmin ön işlemesini yapmak için ya da klasik CNN modelleri ile birleştirilip eğitildiğini gördük. Bu yüzden amacımız, bu projede baştan sonra kuantum algoritmaları ile çalışan bir Q-CNN modeli yazmak oldu. 

Resimleri Q-CNN algorithmasına girdi olarak vermek için, resimin her pixel değerini kuantum state değerine dönüştürmemiz gerekiyor. Çok sayıda pixel kullanamayacağımız için resimlerimizi 4x4 boyutuna indirdik ve sonuç olarak 16 qubit içeren bir devre kurduk. Bu devrede 2x1 boyutunda Quantum Convolutional filtreleri resimin üzerinde gezdirdik. Böylece resmi yarı boyutuna indirgeyerek 2x2 boyutunda özellik haritalarını çıkardık. Bu noktada modele ölçüm yaparak tahmin yaptık. 

Modelimiz MNIST datasetinde 3 ve 6 sayılarını sınıflandırmak için kullanıldı. 100 resmi eğitim için, 20 resmi ise modeli test etmek için kullandık. Modelin eğitimi sonucunda 76% doğruluk oranına ulaştık. 



------------------------------------------------------------------------------------------------------------------------------------
**Referanslar**

Implementation and Analysis of Quantum Fourier Transform in Image Processing. Ola Al-Ta’ani, Ali Mohammad Alqudah2, Manal Al-Bzoor
Quantum neural network, M.V.Altaisky 

Learning the quantum algorithm for state overlap, Lukasz Cincio, Yiğit Subaşı, Andrew T. Sornborger, Patrick J. Coles 

Quantum Natural Gradient. James Stokes, Josh Izaac, Nathan Killoran, Giuseppe Carleo

Classification with Quantum Neural Networks on Near Term Processors. Edward Farhi, Hartmut Neven

https://pennylane.ai/qml/demos/tutorial_quanvolution.html

https://www.tensorflow.org/quantum/tutorials/mnist

https://www.tensorflow.org/quantum/tutorials/qcnn

https://arxiv.org/pdf/1801.01465.pdf

https://arxiv.org/pdf/1812.11042.pdf

