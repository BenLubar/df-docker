FROM benlubar/dwarffortress:latest

RUN apt-get update && apt-get install -y --no-install-recommends \
	ca-certificates \
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

RUN git clone -b develop --recursive --depth=1 https://github.com/DFHack/dfhack.git /dfhack \
&& cd /dfhack \
&& git tag git-develop

RUN mkdir -p /dfhack/build-docker \
&& cd /dfhack/build-docker \
&& cmake -DCMAKE_INSTALL_PREFIX:STRING=/df_linux -DCMAKE_BUILD_TYPE:STRING=RelWithDebInfo .. \
&& make -j3 \
&& make install \
&& rm -rf /dfhack/build-docker \
&& echo -n > /df_linux/hack/scripts/gui/prerelease-warning.lua

CMD ["./dfhack"]
