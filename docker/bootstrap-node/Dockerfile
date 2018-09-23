FROM ubuntu:xenial

WORKDIR /data
USER root

RUN apt update && apt -y install openjdk-8-jre-headless libsodium18 wget
RUN wget https://github.com/rchain/rchain/releases/download/v0.6.4/rnode_0.6.4_all.deb
RUN dpkg -i rnode_0.6.4_all.deb

ENV private_key cb82faa58dea8d1295b41efe66e4dc5bb057c69ca718295c2ab6359937178710
ENV public_key 8bb03c4ece1cec9062c00686b45845fcb3f10e8a48148df1073e626fe1d424cb
ENV bootstrap_address rnode://7fa70d245268ed19253f18c802fccd22668a0211@52.119.8.68:40400
ENV standalone false
ENV port 40400
ENV http_port 40402
ENV metrics_port 40403
ENV grpc_port 40401
ENV grpc_host localhost

EXPOSE 40400

ADD rnode_init /data/
RUN chmod +x /data/rnode_init
CMD ["/data/./rnode_init"]