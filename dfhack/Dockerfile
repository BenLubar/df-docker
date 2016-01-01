FROM benlubar/dwarffortress:df-0.42.04

RUN apt-get update && apt-get install -y --no-install-recommends \
	cmake \
	g++-multilib \
	gcc-multilib \
	git \
	libxml-libxml-perl \
	libxml-libxslt-perl \
	make \
	zlib1g-dev:i386 \
&& apt-get clean \
&& rm -rf /var/lib/apt/lists/*

RUN git clone -b 0.42.04-alpha1 --recursive --depth=1 https://github.com/DFHack/dfhack.git /dfhack \
&& mkdir -p /dfhack/build-docker \
&& cd /dfhack/build-docker \
&& cmake -DCMAKE_INSTALL_PREFIX:STRING=/df_linux -DZLIB_LIBRARY:STRING=/usr/lib/i386-linux-gnu/libz.so /dfhack \
&& make install

CMD ["./dfhack"]
