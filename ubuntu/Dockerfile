# Use the official Ubuntu base image
FROM ubuntu:latest

# Install vim and bash
RUN apt-get update && \
    apt-get install -y vim bash && \
    rm -rf /var/lib/apt/lists/*

# Set the default command to bash
CMD ["bash"]

