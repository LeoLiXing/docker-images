FROM centos:centos7

#用户
USER root

#更新yum
RUN yum update -y

#安装vim wget openssh-server openssh-clients
RUN yum install -y vim wget openssh-server openssh-clients

#生成ssh-key与配置ssh-key
RUN mkdir -p /root/.ssh && touch /root/.ssh/known_hosts
RUN ssh-keygen -t rsa -b 2048 -f /root/.ssh/id_rsa
#RUN echo 'ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDNYXyDd8RLahbcgW7uLzoJgg9LHxNbl9EO82jdCh2VTOKl4ky/oK94wNeifdX8dpty9yjvV/47JU84CQWxUPm5d4xuV9zraq0G0COOMFZ0bNPQHYKaJGyDIVKbi0eWXBRxy+Doq7GCYAP1zKJSpsmHKkInJ0JOvzzcxbAFmzfgTV+2AKTv8W6o8fKFr8uA81XHbHSnUCHiiZbbQxpMaBlOPufZI1RB0E9TflGsBmjuLmVUhoDHKessZ65Mk47SSLL6B23hRWNgLdfkS6N2zAKpBUBubO4MUYwhmWLRzrvMjI7PtuhypoyKCGvd53gOzeRbtsq+q7PaGVpoRa4I0xlF freedoms@Freedoms.local'>/root/.ssh/authorized_keys
RUN cat /root/.ssh/id_rsa.pub > /root/.ssh/authorized_keys

#修改ssh配置
RUN sed -i 's/UsePAM yes/UsePAM no/g' /etc/ssh/sshd_config
RUN sed -i '/^#Host_Key/'d /etc/ssh/sshd_config
RUN sed -i '/^Host_Key/'d /etc/ssh/sshd_config
RUN echo 'HostKey /root/.ssh/id_rsa'>/etc/ssh/sshd_config

#修改root用户登录密码
RUN echo 'root:passwd'|chpasswd

#开放22端口
EXPOSE 22

#镜像运行时，启动sshd
CMD ["/usr/sbin/sshd", "-D"]