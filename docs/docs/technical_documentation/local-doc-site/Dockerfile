# Copyright (c) 2016-2023 Martin Donath <martin.donath@squidfunk.com>

# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to
# deal in the Software without restriction, including without limitation the
# rights to use, copy, modify, merge, publish, distribute, sublicense, and/or
# sell copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:

# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.

# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NON-INFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
# FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS
# IN THE SOFTWARE.

FROM mcr.microsoft.com/devcontainers/python:3.11 

# Build-time flags
ARG WITH_PLUGINS=true

SHELL ["/bin/bash", "-c"]

# Environment variables
ENV PACKAGES=/usr/local/lib/python3.11/site-packages
ENV PYTHONDONTWRITEBYTECODE=1

# Set build directory
WORKDIR /tmp

# Copy files necessary for build
COPY package.json package.json
COPY README.md README.md
COPY requirements.txt ./
COPY pyproject.toml pyproject.toml

# Perform build and cleanup artifacts and caches

RUN apt update && \
    apt -y dist-upgrade && \
    type -p curl >/dev/null || (apt install curl -y) && \
    curl -fsSL https://cli.github.com/packages/githubcli-archive-keyring.gpg | sudo dd of=/usr/share/keyrings/githubcli-archive-keyring.gpg && \
    chmod go+r /usr/share/keyrings/githubcli-archive-keyring.gpg && \
    echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" > /etc/apt/sources.list.d/github-cli.list > /dev/null && \
    apt update && \
    apt install gh -y

# This user should be the same as "remoteUser" in the devcontainer.json file
ARG USERNAME="vscode"

USER ${USERNAME}
WORKDIR /home/${USERNAME}/
ARG HOME="/home/${USERNAME}"

# Set up alias for devcontainer commands using the alternate Makefile
RUN echo 'alias make="make -f Makefile.container"' >> ~/.profile && \
    echo 'alias make="make -f Makefile.container"' >> ~/.bash_aliases && \
    curl -s https://raw.githubusercontent.com/git/git/master/contrib/completion/git-completion.bash -o ~/.git-completion.bash && \
    echo '. ~/.git-completion.bash' >> ~/.bashrc && \
    echo 'eval "$(gh completion -s bash)"' >> ~/.bashrc

ENV PATH="${HOME}/.local/bin:$PATH"

COPY --chown=${USERNAME} requirements.txt /tmp/pip-tmp/
COPY --chown=${USERNAME} .pre-commit-config.yaml .
COPY --chown=${USERNAME} ./* docs/
RUN pip3 --disable-pip-version-check --no-cache-dir install --user -r /tmp/pip-tmp/requirements.txt

# Set working directory
WORKDIR "${HOME}/docs"

# Expose MkDocs development server port
EXPOSE 8000

ENTRYPOINT ["mkdocs"]
CMD ["serve", "-a0.0.0.0:8005"]
