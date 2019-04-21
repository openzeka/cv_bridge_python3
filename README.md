Jetpack 4.2 sürümünde ROS paketlerini Python3 ile kullanmak için cv_bridge kütüphanesi python3'e göre tekrar derlenmelidir.

Öncelikle yeni bir klasör oluşturalım. cv_bridge paketinin python3'e göre derlenme işlemleri bu klasörde gerçekleşecektir. Daha sonra python3 ile geliştirilen bir ROS uygulamasında cv_bridge kullanmak için bu klasör **extend** edilecektir.



# Gereksinimler
- ROS melodic
- Jetpack 4.2

# Kurulum

```bash
mkdir ~/catkin_cv_bridge && cd catkin_cv_bridge
git clone https://github.com/openzeka/cv_bridge_python3.git ./src/vision_opencv
source /opt/ros/melodic/setup.bash
catkin config  -DPYTHON_EXECUTABLE=/usr/bin/python3 -DPYTHON_INCLUDE_DIR=/usr/include/python3.6m -DPYTHON_LIBRARY=/usr/lib/aarch64-linux-gnu/libpython3.6m.so
catkin config --install
catkin build cv_bridge
```

Örnek olarak python3 ile yazılmış olan MARC 2.0 yazılımı içerisinde bulunan _predict.py_ dosyasını çalıştırmak için:

```bash
cd marc
source devel/setup.bash
source ../cv_bridge_python3/install/setup.bash --extend 
rosrun deep_learning predict.py
```

_source ../cv_bridge_python3/install/setup.bash --extend_ kodu her seferinde _source devel/setup.bash_ komutundan sonra uygulanmalıdır. 

# Kaynaklar
[https://medium.com/@beta_b0t/how-to-setup-ros-with-python-3-44a69ca36674](https://medium.com/@beta_b0t/how-to-setup-ros-with-python-3-44a69ca36674)
[https://stackoverflow.com/questions/49221565/unable-to-use-cv-bridge-with-ros-kinetic-and-python3](https://stackoverflow.com/questions/49221565/unable-to-use-cv-bridge-with-ros-kinetic-and-python3)

