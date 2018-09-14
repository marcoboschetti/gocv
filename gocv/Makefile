.ONESHELL:
.PHONY: test deps download build clean

test:
	go test .

deps:
	 apt-get update
	 apt-get install -y build-essential
	 apt-get install -y cmake git pkg-config
	 apt-get install -y libtbb2 libtbb-dev libjpeg-dev libpng-dev libtiff-dev libjasper-dev

download:
	mkdir /tmp/opencv
	cd /tmp/opencv
	wget -O opencv.zip https://github.com/opencv/opencv/archive/3.4.0.zip
	unzip opencv.zip
	wget -O opencv_contrib.zip https://github.com/opencv/opencv_contrib/archive/3.4.0.zip
	unzip opencv_contrib.zip

build:
	cd /tmp/opencv/opencv-3.4.0
	mkdir build
	cd build
	cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D OPENCV_EXTRA_MODULES_PATH=/tmp/opencv/opencv_contrib-3.4.0/modules -D BUILD_DOCS=OFF BUILD_EXAMPLES=OFF -D BUILD_TESTS=OFF -D BUILD_PERF_TESTS=OFF -D BUILD_opencv_java=OFF -D BUILD_opencv_python=OFF -D BUILD_opencv_python2=OFF -D BUILD_opencv_python3=OFF ..
	make -j4
	 make install
	 ldconfig

clean:
	cd ~
	rm -rf /tmp/opencv

install: download build clean