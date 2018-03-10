FROM benlubar/dwarffortress:df-0.44.05

ENV DFHACK_VERSION 0.44.05-r2
ENV DFHACK_ARCHIVE_NAME dfhack-0.44.05-r2-Linux-64-gcc-4.8.tar.bz2

ENV DFHACK_ARCHIVE_SHA1 

RUN curl -LSo dfhack.tar.bz2 https://github.com/DFHack/dfhack/releases/download/${DFHACK_VERSION}/${DFHACK_ARCHIVE_NAME} \
 && echo "${DFHACK_ARCHIVE_SHA1} *dfhack.tar.bz2" | sha1sum -c \
 && tar -xjvf dfhack.tar.bz2 \
 && rm -rf dfhack.tar.bz2 stonesense hack/plugins/stonesense.plug.so \
 && echo "setarch x86_64 -R true || (echo 'Access to the ADDR_NO_RANDOMIZE personality is required for DFHack to run.'; echo 'See https://github.com/BenLubar/df-docker#readme for details.' exit 2)" > distro_fixes.sh

CMD ["./dfhack"]
