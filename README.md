# gmm-marker-tracking
This is the code and test data for Gaussian mixture model based fiducial marker tracking in ET

1.gmm-marker-tracking-bound-test
Readers can download gmm-marker-tracking-bound-test.tar.gz and build it to test the Gaussian mixture model based fiducial marker tracking in ET. This code has the implementation of an entire tilt series matching. We provide a dataset as illustration. 

The code can be compiled by cmake 2.8+; the code depends on opencv2.4 and gcc5.4. here is an example to build it:

cd gmm-marker-tracking-bound-test
mkdir build
cd build
cmake ..
make

There will be execution named gmm-marker-tracking and drawmatch in gmm-marker-tracking-bound-test/build/bin

Download our test dataset (V4B_G1_Tilt2.tar.gz from ear.ict.ac.cn) and copy the gmm-marker-tracking&drawmatch into the directory. Run the following instruction:

./gmm-marker-tracking -i V4B_G1_Tilt2.mrc -a V4B_G1_Tilt2.rawtlt -d -1 -o V4B_G1_Tilt2.xf -n V4B_G1_Tilt2.tlt
 ./drawmatch -i V4B_G1_Tilt2.mrc -a V4B_G1_Tilt2.rawtlt -d -1 -o V4B_G1_Tilt2.xf -n V4B_G1_Tilt2.tlt

There will be a directory named matches_ill generated, in which the tracking result is illustrated.

Gaussian mixture model based fiducial marker tracking serves as the key code in markerauto1.6+, which is a popular software for tilt series alignment in ET[1][2]. markerauto1.6.2 can be download in ear.ict.ac.cn.

If the reader run as "markerauto -i V4B_G1_Tilt2.mrc -a V4B_G1_Tilt2.rawtlt -d -1 -o V4B_G1_Tilt2.xf -n V4B_G1_Tilt2.tlt", markerauto1.6+ will use the old fasion to process the data. If the reader run as "markerauto -i V4B_G1_Tilt2.mrc -a V4B_G1_Tilt2.rawtlt -d -1 -o V4B_G1_Tilt2.xf -n V4B_G1_Tilt2.tlt -t", markerauto1.6+ will use the Gaussian mixture model based fiducial marker tracking to process the data, which is much fater than the old fashion. The generated xxx.xf file can be used to general full stack: AuTom "mrcstack -i xxx.mrc -x xxx.xf -o xxx_fin.mrc" or IMOD "newstack -input xxx.mrc -xf xxx.xf -output xxx_fin.mrc".

[1] Renmin Han, Fa Zhang, Xiaohua Wan, Jose-Jesus Fernández, Fei Sun, Zhiyong Liu. (2014) A marker-free automatic alignment method based on scale-invariant features. Journal of Structural Biology, 186 (1), 167-180.

[2] Renmin Han#, Xiaohua Wan#, Zihao Wang, Yu Hao, Jingrong Zhang, Yu Chen, Xin Gao, Zhiyong Liu, Fei Ren, Fei Sun, Fa Zhang. (2017) AuTom: A novel automatic platform for electron tomography reconstruction. Journal of Structural Biology, 199(3), 196-208.

[3] Renmin Han, Fa Zhang, Xin Gao. (2018) A fast fiducial marker tracking model for fully automatic alignment in electron tomography. Bioinformatics, 34(5), 853-863.
