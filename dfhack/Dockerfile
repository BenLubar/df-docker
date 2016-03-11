FROM benlubar/dwarffortress:df-0.42.06

RUN curl -ksSL https://github.com/DFHack/dfhack/releases/download/0.42.06-alpha2/dfhack-0.42.06-alpha2-Linux-gcc-4.8.1.tar.bz2 | tar -xjv \
&& rm -rf stonesense hack/plugins/stonesense.plug.so

CMD ["./dfhack"]
