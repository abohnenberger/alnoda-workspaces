ARG docker_registry=docker.io/alnoda
ARG image_tag=18.04-1.0

FROM ${docker_registry}/workspace-in-docker:${image_tag}
USER roots

USER root

COPY supervisord-sqlite.conf /etc/supervisord/

COPY mkdocs /home/docs
COPY README.md /home/docs/docs/docs.md

RUN echo "------------------------------------------------------ sqlite3" \
    && apt-get install -y sqlite3 \
    && echo "------------------------------------------------------ cli" \
    && pip install litecli==1.7.0 \
    && echo "------------------------------------------------------ rclone" \
    && curl https://rclone.org/install.sh | bash \
    && echo "------------------------------------------------------ pspg" \
    && apt-get install -y pspg \
    && echo "------------------------------------------------------ sqlite-browser" \
    && pip install sqlite-web==0.4.0 \
    && echo "------------------------------------------------------ sqlean main extension set" \
    && mkdir /home/sqlite-extensions && cd /home/sqlite-extensions \
    && wget https://github.com/nalgeon/sqlean/releases/download/0.15.1/crypto.so \
    && wget https://github.com/nalgeon/sqlean/releases/download/0.15.1/fileio.so \
    && wget https://github.com/nalgeon/sqlean/releases/download/0.15.1/fuzzy.so \
    && wget https://github.com/nalgeon/sqlean/releases/download/0.15.1/ipaddr.so \
    && wget https://github.com/nalgeon/sqlean/releases/download/0.15.1/re.so \
    && wget https://github.com/nalgeon/sqlean/releases/download/0.15.1/spellfix.so \
    && wget https://github.com/nalgeon/sqlean/releases/download/0.15.1/stats.so \
    && wget https://github.com/nalgeon/sqlean/releases/download/0.15.1/text.so \
    && wget https://github.com/nalgeon/sqlean/releases/download/0.15.1/unicode.so \
    && wget https://github.com/nalgeon/sqlean/releases/download/0.15.1/uuid.so \
    && echo "------------------------------------------------------ tbls" \
    && cd /tmp && wget https://github.com/k1LoW/tbls/releases/download/v1.54.2/tbls_v1.54.2_linux_amd64.tar.gz \
    && mkdir /tmp/tbls  && tar -xzf /tmp/tbls_v1.54.2_linux_amd64.tar.gz --directory /tmp/tbls \
    && chmod +x /tmp/tbls/tbls \
    && mv /tmp/tbls/tbls /usr/bin/ \
    && rm -rf /tmp/tbls && rm tbls_v1.54.2_linux_amd64.tar.gz \
    && echo "------------------------------------------------------ dbdesigner" \
    && git clone https://github.com/akreienbring/dbdesigner /opt/dbdesigner \
    && cd /opt/dbdesigner && nodeenv --node=12.18.3 env && . env/bin/activate && npm install --save express \
    && rm /opt/dbdesigner/dist/startUp.js \
    && echo "------------------------------------------------------ sqlite viewers" \
    && git clone https://github.com/inloop/sqlite-viewer.git /home/static-server/sqlite-viewer \
    && git clone https://github.com/cyrilbois/Web-GUI-for-SQLite.git /home/static-server/web-gui-sqlite \
    && mv /home/static-server/web-gui-sqlite/Web-GUI-for-SQLite.html /home/static-server/web-gui-sqlite/index.html \
    && echo "------------------------------------------------------ user" \
    && chown -R abc /opt/theia \
    && mkdir -p /var/log/theia && chown -R abc /var/log/theia \
    && chown -R abc /opt/dbdesigner \
    && mkdir /var/log/dbdesigner && chown -R abc /var/log/dbdesigner \
    && mkdir /var/log/sqlite-web && chown -R abc /var/log/sqlite-web \
    && echo "export PAGER='pspg -s 4 --no-mouse'" >> /home/abc/.zshrc  \
    && find /home -type d | xargs -I{} chown -R abc {} \
    && find /home -type f | xargs -I{} chown abc {} 

COPY dbdesigner/startUp.js /opt/dbdesigner/dist/startUp.js 


ENV SQLITE_VIEWER_URL=http://localhost:8022/sqlite-viewer/ \
    SQLITE_WEB_GUI_URL=http://localhost:8022/web-gui-sqlite/ \
    SQLITE_WEB_CUSTOM_URL=http://localhost:8033/

USER abc


