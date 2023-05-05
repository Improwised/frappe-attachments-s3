FROM frappe/bench:latest

WORKDIR /workspace/development
ENV NODE_VERSION=14.19.3
ENV PATH="/home/frappe/.local/bin:/home/frappe/.pyenv/shims:/home/frappe/.nvm/versions/node/v14.19.3/bin:/home/frappe/.local/bin:/home/frappe/.pyenv/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
RUN sudo chown frappe:frappe .
RUN node -v
RUN PYENV_VERSION=3.9.9 bench init --skip-redis-config-generation --frappe-branch version-13 frappe-bench
WORKDIR /workspace/development/frappe-bench
RUN bench set-config -g db_host mariadb
RUN bench set-config -g redis_cache redis://redis-cache:6379
RUN bench set-config -g redis_queue redis://redis-queue:6379
RUN bench set-config -g redis_socketio redis://redis-socketio:6379
RUN bench set-config -g developer_mode 1
RUN bench get-app --branch version-13 erpnext
