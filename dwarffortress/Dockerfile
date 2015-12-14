FROM ubuntu

RUN dpkg --add-architecture i386 \
&& apt-get update && apt-get install -y \
	curl \
	libglu1-mesa:i386 \
	libgtk2.0-0:i386 \
	libopenal1:i386 \
	libsdl-image1.2:i386 \
	libsdl-ttf2.0-0:i386 \
&& apt-get clean \
&& rm -rf /var/lib/apt/lists/*

ENV DF_VERSION 40_12

RUN mkdir -p /df_linux \
	&& curl -SL http://www.bay12games.com/dwarves/df_${DF_VERSION}_linux.tar.bz2 \
	| tar -xjC / df_linux \
	&& chmod -x+X -R /df_linux \
	&& chmod +x /df_linux/df /df_linux/libs/Dwarf_Fortress \
	&& rm /df_linux/libs/libgcc_s.so.1 /df_linux/libs/libstdc++.so.6 \
	&& rm -r /df_linux/data/sound \
	&& mkdir -p /df_linux/data/save /df_linux/data/movies \
	&& sed -i \
		-e 's/\[PRINT_MODE:2D\]/[PRINT_MODE:TEXT]/' \
		-e 's/\[TRUETYPE:[0-9]*\]/[TRUETYPE:NO]/' \
		-e 's/\[SOUND:YES\]/[SOUND:NO]/' \
		-e 's/\[INTRO:YES\]/[INTRO:NO]/' \
		/df_linux/data/init/init.txt

WORKDIR /df_linux
VOLUME /df_linux/data/save
VOLUME /df_linux/data/movies

CMD ["./df"]
