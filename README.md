# Neural-Qubits
KTHack2020 - KUANTUM PROGRAMLAMA HACKATHONU 

Grup Üyeleri:

〈 ALARA | ZINDANCIOĞLU 〉

〈 BAŞAK | EKINCI 〉

〈 ENES | BAŞPINAR 〉

〈 TOGAN | TLIMAKHOV | YUSUF 〉



------------------------------------------------------------------------------------------------------------------------------------
**Özet**

Görüntü işleme, bilgisayar bilimi ve mühendislikte en büyük araştırma alanlardan biridir. Askeri Endüstri, Güvenlik, Robotik, astronomi, gibi bir çok insan hayatını doğrudan etkileyen uygulamalarla yakından ilgilendiren bir teknoloji haline geldi.

Bu bağlamda kuantum görüntü işlemeye (QImP) artan bir ilgi var. Bunun nedeni, kuantum hesaplamanın, klasik hesaplama tekniklerine göre performans ve hız açısından daha verimli olmasıdır.

Fourier dönüşümü, klasik sinyal ve görüntü işlemede kullanılan en önemli algoritmalardan biridir, aynı zamanda son geliştirilen kuantum algoritmalarında önemli bir bileşen olarak kullanıma girmiştir. klasikten farklı olarak, Kuantum Fourier dönüşümü, verilerin olasılık genliklerine kodlandığı bir kuantum durumunu kulanmasıdır.

Kuantum bilgisayarlar, Kuantum süperpozisyonu ve kuantum dolaşıklığı özelliklerinden yararlandiğindan, Logic işlemlerinde aynı anda 0 ve 1〈 0 | 1 〉değerlerini alabiliyor. Bu nedenle kuantum bilgisayarlar temel bilgi birimi olan bit yerine Qubit ile çalışıp, belirli hesaplamalarda klasik bilgisayarlardan katlanarak daha hızlı olduğu kanıtlanmıştır.




------------------------------------------------------------------------------------------------------------------------------------
**Açıklama**

Fourier analizi makine öğrenmesinde karmaşık olan bir verinin, boyutlarının azaltılarak daha basit bir problem olarak incelenmesi için oolanak sağlamaktadır. Çalışmamızda verilen bir resmin pixel gösterimini elde edebilmek için fourier temelli Flexible Representation of Quantum Images (FRQI) yöntemi kullanarak sağlanmıştır.

Bu yöntem nxn piksel ile verilen bir resmin log2(m) qubit olarak gösterilmesini sağlamaktadır.

Çalışmamızda Neural network kullanarak resim sınıflandırması 3X3 piksel ve 4X4 piksel boyutunda resimlere uygulanarak sonuçlar elde edilmiştir ve bu sonuçlar Neural networkta yer alan   girdi olarak verilen resmin pixel dönüşümünü sağlayan algoritmanın FRQI yöntemiyle değiştirilerek, elde edilen sonuçlar ile karşılaştırılmıştır.
Sonuçta 3X^ 3 piksel boyutunda resimlere FRQI uygulanması halinde programın  biraz daha hızlı çalıştığı görülürken,
accuracy'nin düştüğü, 4x4  boyutlu resimlerde ise tam tersi bir durum ile karşılaşılmıştır.

Projemizde yapay zeka ile resim işlemede çokça kullanılan Convolutional Neural Network(CNN) modellerini quantum algoritmaları ile yazmayı planladık. Şimdiye kadar yapılan Quantum Convolutional Network (Q-CNN) modellerinde, kuantum algoritmaları ile yazılan convolutional filtrelerin ya resmin ön işlemesini yapmak için ya da klasik CNN modelleri ile birleştirilip eğitildiğini gördük. Bu yüzden amacımız, bu projede baştan sonra kuantum algoritmaları ile çalışan bir Q-CNN modeli yazmak oldu. 

Resimleri Q-CNN algorithmasına girdi olarak vermek için, resimin her pixel değerini kuantum state değerine dönüştürmemiz gerekiyor. Çok sayıda pixel kullanamayacağımız için resimlerimizi 4x4 boyutuna indirdik ve sonuç olarak 16 qubit içeren bir devre kurduk. Bu devrede 2x1 boyutunda Quantum Convolutional filtreleri resimin üzerinde gezdirdik. Böylece resmi yarı boyutuna indirgeyerek 2x2 boyutunda özellik haritalarını çıkardık. Bu noktada modele ölçüm yaparak tahmin yaptık. 

Modelimiz MNIST datasetinde 3 ve 6 sayılarını sınıflandırmak için kullanıldı. 100 resmi eğitim için, 20 resmi ise modeli test etmek için kullandık. Modelin eğitimi sonucunda 76% doğruluk oranına ulaştık. 



------------------------------------------------------------------------------------------------------------------------------------
**Referanslar**

[0]: Implementation and Analysis of Quantum Fourier Transform in Image Processing. Ola Al-Ta’ani, Ali Mohammad [1]: Alqudah2, Manal Al-Bzoor  
[2]: Quantum neural network, M.V.Altaisky   
[3]: Learning the quantum algorithm for state overlap, Lukasz Cincio, Yiğit Subaşı, Andrew T. Sornborger, Patrick J. Coles  
[5]: Quantum Natural Gradient. James Stokes, Josh Izaac, Nathan Killoran, Giuseppe Carleo   
[6]: Classification with Quantum Neural Networks on Near Term Processors. Edward Farhi, Hartmut Neven  
[7]: [https://pennylane.ai/qml/demos/tutorial_quanvolution.html]()  
[8]: [https://www.tensorflow.org/quantum/tutorials/mnist]()  
[9]: [https://www.tensorflow.org/quantum/tutorials/qcnn]()  
[10]: [https://arxiv.org/pdf/1801.01465.pdf]()  
[11]: [https://arxiv.org/pdf/1812.11042.pdf]()  


