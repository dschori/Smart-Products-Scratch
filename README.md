# Smart-Products-Scratch


## TLT-Classification Example:
1. Get access to the Nvidia DGX-2 Machine, one person per group
2. Read the DGX-2 Manual which you received with the access!
3. Login to the Machine
4. Check which GPU's are in use: http://sx-el-121920.hsr.ch:8080/ 
5. Start a TLT-Docker container by:
```
docker run --rm -ti -e NVIDIA_VISIBLE_DEVICES=<NUMBER OF A GPU WHICH IS NOT IN USE> -p 8881:8888 -v /mnt/data/smart-products:/workspace/tlt-experiments nvcr.io/nvidia/tlt-streamanalytics:v2.0_py3 /bin/bash
```
6. If you get an error for the port mapping: That means this port is probably already in use, take another port 8880 - 8899
7. Start a Jupyter Server inside the Docker Container:
```
jupyter notebook --ip 0.0.0.0 --port 8888 --allow-root
```
8. You should see a token in the console
9. Copy that token and go to: 
  ```
http://sx-el-121920.hsr.ch:<the port you mapped>/?<your token>
```
10. Inside Jupyter, go to (in a web-browser): /tlt-experiments/DO_NOT_DELETE
11. Make a copy of the Notebook or Download it from: https://github.com/dschori/Smart-Products-Scratch/tree/main/TLT  
(The SmartProducts.zip File has to be at: **/mnt/data/smartproducts/SmartProducts.zip** and the Notebook has to be at: **/mnt/data/DO_NOT_DELETE/your_notebook.ipynb**)
12. Open the Notebook
13. Click: Kernel>Restart&Clear Output
14. Click through the Notebook

## Camera Calibration:
**Don't do this on the DGX-2 Machine!**  
**Use your Jetson Nano**  
1. Run: python3 aqcuire_images.py to aquire images from a chessboard
2. Run: python3 calibrate_camera.py  with the taken images to generate the calibration files


