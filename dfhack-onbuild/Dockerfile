FROM benlubar/dwarffortress:latest

ONBUILD COPY . /dfhack-plugin-onbuild

ONBUILD RUN apt-get update && apt-get install -y --no-install-recommends \
	ca-certificates \
	cmake \
	g++-multilib \
	gcc-multilib \
	git \
	libxml-libxml-perl \
	libxml-libxslt-perl \
	make \
	zlib1g-dev:i386 \
&& git clone --recursive --depth=1 -b develop https://github.com/DFHack/dfhack.git /dfhack \
&& cd /dfhack \
&& git tag dfhack-onbuild \
&& mv /dfhack-plugin-onbuild /dfhack/plugins/onbuild \
&& echo 'add_subdirectory(onbuild)' >> /dfhack/plugins/CMakeLists.custom.txt \
&& mkdir -p /dfhack/build-docker \
&& cd /dfhack/build-docker \
&& cmake -DCMAKE_INSTALL_PREFIX:STRING=/df_linux .. \
&& make -j3 install \
&& rm -rf /dfhack \
&& apt-get purge -y \
	ca-certificates \
	cmake \
	g++-multilib \
	gcc-multilib \
	git \
	libxml-libxml-perl \
	libxml-libxslt-perl \
	make \
	zlib1g-dev:i386 \
&& apt-get autoremove -y \
&& apt-get clean \
&& rm -rf /var/lib/apt/lists/*

CMD ["./dfhack"]
