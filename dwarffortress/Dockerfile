FROM ubuntu

RUN apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends \
    bzip2 \
    ca-certificates \
    curl \
    libglu1-mesa \
    libgtk2.0-0 \
    libncursesw5 \
    libopenal1 \
    libsdl-image1.2 \
    libsdl-ttf2.0-0 \
    locales \
    unzip \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/*

ENV LANG=en_US.UTF-8 LANGUAGE=en_US:en LC_ALL=en_US.UTF-8 \
    DF_VERSION=47_05 \
    DF_ARCHIVE_SHA256=ac74a6dbb7d7d9621f430405080322ab50c35f6632352ff2ea923f6dc5affca3

RUN LC_ALL=C locale-gen en_US.UTF-8 \
 && mkdir -p /df_linux \
 && cd / \
 && curl -LSo /df_linux.tar.bz2 http://www.bay12games.com/dwarves/df_${DF_VERSION}_linux.tar.bz2 \
 && echo "${DF_ARCHIVE_SHA256} *df_linux.tar.bz2" | sha256sum -c \
 && tar -xjf /df_linux.tar.bz2 df_linux \
 && rm df_linux.tar.bz2 \
 && chmod -x+X -R /df_linux \
 && chmod +x /df_linux/df /df_linux/libs/Dwarf_Fortress \
 && rm /df_linux/libs/libgcc_s.so.1 /df_linux/libs/libstdc++.so.6 \
 && rm -r /df_linux/data/sound \
 && mkdir -p /df_linux/data/save /df_linux/data/movies \
 && sed -e 's/\[PRINT_MODE:2D\]/[PRINT_MODE:TEXT]/' \
        -e 's/\[TRUETYPE:[0-9]*\]/[TRUETYPE:NO]/' \
        -e 's/\[SOUND:YES\]/[SOUND:NO]/' \
        -e 's/\[INTRO:YES\]/[INTRO:NO]/' \
        -i /df_linux/data/init/init.txt \
 && sed -e 's/^\.\/libs\/Dwarf_Fortress/exec \0/' \
        -i /df_linux/df

WORKDIR /df_linux
VOLUME /df_linux/data/save
VOLUME /df_linux/data/movies

CMD ["./df"]
