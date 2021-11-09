ARG ELK_VERSION

FROM amd64/ubuntu:20.04

RUN apt-get update && \
    apt-get -y install sudo && \
    apt-get -y install python3-pip python3

RUN pip3 install requests
RUN pip3 install PyYaml
RUN pip3 install elastic-agent-setup==0.0.11
#RUN first=7.14.0 && second=$ELK_VERSION && [  "$first" = "`echo -e "$first\n$second" | sort -V | head -n1`" ] && sed -i 's/--kibana-url/--url/g' $(python3 -c "import os;import elastic_agent_setup;print(os.path.dirname(elastic_agent_setup.__file__))")/settings.py
ADD version_workaround /version_workaround
RUN chmod +x /version_workaround
#RUN echo ${ELK_VERSION}
#RUN /version_workaround "$ELK_VERSION"
ADD install.py /install.py
RUN chmod +x /install.py

#CMD ["/install.py"]
#ENTRYPOINT ["python3"]
CMD ["/version_workaround"]