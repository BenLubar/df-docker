FROM benlubar/dwarffortress:df-0.43.03

ENV DFHACK_VERSION 0.43.03-alpha1

RUN curl -ksSL https://github.com/DFHack/dfhack/releases/download/${DFHACK_VERSION}/dfhack-${DFHACK_VERSION}-Linux-gcc-4.8.1.tar.bz2 | tar -xjv \
&& rm -rf stonesense hack/plugins/stonesense.plug.so

CMD ["./dfhack"]
