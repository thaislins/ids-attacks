# From the Kali linux base image
FROM kalilinux/kali-linux-docker

# Update and apt install programs
RUN apt update && apt -y upgrade && apt -y install kali-linux-top10 && apt -y install net-tools

# Create known_hosts for git cloning
RUN touch /root/.ssh/known_hosts
# Add host keys
RUN ssh-keyscan bitbucket.org >> /root/.ssh/known_hosts
RUN ssh-keyscan github.com >> /root/.ssh/known_hosts

# Clone git repos
RUN git clone https://github.com/danielmiessler/SecLists.git /opt/seclists
RUN git clone https://github.com/PowerShellMafia/PowerSploit.git /opt/powersploit

# Other installs
RUN pip install pwntools

# Update ENVd
ENV PATH=$PATH:/opt/powersploit

# Set entrypoint and working directory
WORKDIR /root/
