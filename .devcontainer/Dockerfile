FROM mcr.microsoft.com/devcontainers/ruby:1-3.2-bullseye

# Install Rails
RUN su vscode -c "gem install rails -v \"~> 7.1.0\""
RUN su vscode -c "gem install webdrivers"

# # Fix issue with Rails 7.0 and concurrent-ruby gem
# # https://github.com/rails/rails/issues/54263
# RUN su vscode -c "gem uninstall concurrent-ruby -aIx --force"
# RUN su vscode -c "gem install concurrent-ruby -v 1.3.4"

RUN su vscode -c "/usr/local/rvm/bin/rvm fix-permissions"

# Default value to allow debug server to serve content over GitHub Codespace's port forwarding service
# The value is a comma-separated list of allowed domains
ENV RAILS_DEVELOPMENT_HOSTS=".githubpreview.dev,.preview.app.github.dev,.app.github.dev"

# [Optional] Uncomment this section to install additional OS packages.
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends npm yarn postgresql-client

# [Optional] Uncomment this line to install additional gems.
# RUN su vscode -c "gem install <your-gem-names-here>"

# [Optional] Uncomment this line to install global node packages.
# RUN su vscode -c "source /usr/local/share/nvm/nvm.sh && npm install -g <your-package-here>" 2>&1

WORKDIR /workspaces/rails-7-ruby-3-postgres-template
