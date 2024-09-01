# Use an official Ubuntu as a parent image
FROM ubuntu:20.04

# Set environment variables to non-interactive (prevents prompts)
ENV DEBIAN_FRONTEND=noninteractive

# Update and install basic tools
RUN apt-get update && \
    apt-get install -y apt-transport-https ca-certificates curl

# Add Kubernetes apt repository
RUN curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add - && \
    echo "deb http://apt.kubernetes.io/ kubernetes-xenial main" | tee /etc/apt/sources.list.d/kubernetes.list

# Install Kubernetes components
RUN apt-get update && \
    apt-get install -y kubelet kubeadm kubectl

# Mark packages to prevent automatic updates
RUN apt-mark hold kubelet kubeadm kubectl

# Expose ports needed for Kubernetes API server
EXPOSE 6443

# Initialize Kubernetes (this will need to be configured or run later manually)
CMD ["kubeadm", "init"]
