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

Download our test dataset and copy the gmm-marker-tracking&drawmatch into the directory. Run the following instruction:

./gmm-marker-tracking -i V4B_G1_Tilt2.mrc -a V4B_G1_Tilt2.rawtlt -d -1 -o V4B_G1_Tilt2.xf -n V4B_G1_Tilt2.tlt
 ./drawmatch -i V4B_G1_Tilt2.mrc -a V4B_G1_Tilt2.rawtlt -d -1 -o V4B_G1_Tilt2.xf -n V4B_G1_Tilt2.tlt

There will be a directory named matches_ill generated, in which the tracking result is illustrated.

Gaussian mixture model based fiducial marker tracking serves as the key code in markerauto1.6+, which is a popular software for tilt series alignment in ET[1][2]. markerauto1.6.2 can be download in ear.ict.ac.cn.

If the reader run as "markerauto -i V4B_G1_Tilt2.mrc -a V4B_G1_Tilt2.rawtlt -d -1 -o V4B_G1_Tilt2.xf -n V4B_G1_Tilt2.tlt", markerauto1.6+ will use the old fasion to process the data. If the reader run as "markerauto -i V4B_G1_Tilt2.mrc -a V4B_G1_Tilt2.rawtlt -d -1 -o V4B_G1_Tilt2.xf -n V4B_G1_Tilt2.tlt -t", markerauto1.6+ will use the Gaussian mixture model based fiducial marker tracking to process the data, which is much fater than the old fashion. 

[1] Han, R., Wang, L., Liu, Z., Sun, F., Zhang, F., 2015. A novel fully automatic scheme for fiducial marker-based alignment in electron tomography. J. Struct. Biol. 192 (3), 403 – 417.
[2] Han, R. et al. AuTom: a novel automatic platform for electron tomography reconstruction. J. Struct. Biol. in press
