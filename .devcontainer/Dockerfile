FROM ruby:3.3

# Create the user
ARG USERNAME=vscode
ARG USER_UID=1000
ARG USER_GID=$USER_UID

# Create the user
RUN groupadd --gid $USER_GID $USERNAME \
    && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
    && apt-get update \
    && apt-get install -y sudo \
    && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
    && chmod 0440 /etc/sudoers.d/$USERNAME

# Install Python and required packages
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
        python3-full \
        python3-pip \
        python3-venv \
    && apt-get clean -y && rm -rf /var/lib/apt/lists/*

# Create and activate virtual environment
RUN python3 -m venv /opt/venv
ENV PATH="/opt/venv/bin:$PATH"

# Install Jupyter in the virtual environment
RUN pip3 install jupyter

# Install required system dependencies for IRuby
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
        libtool \
        libffi-dev \
        ruby-dev \
        libzmq3-dev \
        autoconf \
        pkg-config \
    && apt-get clean -y && rm -rf /var/lib/apt/lists/*

# Install IRuby
RUN gem install iruby
RUN iruby register --force

# Set the default user
USER $USERNAME

# Create workspace directory
WORKDIR /workspace