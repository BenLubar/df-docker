FROM benlubar/dwarffortress:df-0.44.12

ENV DFHACK_VERSION=0.44.12-alpha1 \
    DFHACK_ARCHIVE_NAME=dfhack-0.44.12-alpha1-Linux-64-gcc-4.8.tar.bz2 \
    DFHACK_ARCHIVE_SHA1=a22184e08c1278cc502f6580d420f1a3501660c8

RUN curl -LSo dfhack.tar.bz2 https://github.com/DFHack/dfhack/releases/download/${DFHACK_VERSION}/${DFHACK_ARCHIVE_NAME} \
 && echo "${DFHACK_ARCHIVE_SHA1} *dfhack.tar.bz2" | sha1sum -c \
 && tar -xjvf dfhack.tar.bz2 \
 && rm -rf dfhack.tar.bz2 stonesense hack/plugins/stonesense.plug.so \
 && echo "if ! setarch x86_64 -R grep -q 00040000 /proc/self/personality; then echo 'Access to the ADDR_NO_RANDOMIZE personality is required for DFHack to run.'; echo 'See https://github.com/BenLubar/df-docker#readme for details.'; exit 2; fi" > distro_fixes.sh

CMD ["./dfhack"]
