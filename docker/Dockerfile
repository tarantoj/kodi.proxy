FROM linuxserver/tvheadend

RUN apk add --no-cache py-virtualenv wget git

WORKDIR /user/share/kodi.proxy
COPY . .

RUN echo "userdata=/config/kodi.proxy" >> config.ini \
    && virtualenv --python=python2.7 .env \
    && .env/bin/pip install -r requirements.txt \
    && chmod 555 proxy tv_grab_iptv_merge iptv_merge.m3u8.sh tvh.sh \
    && ln -s /usr/share/kodi.proxy/tv_grab_iptv_merge /usr/bin/tv_grab_iptv_merge

COPY ./docker/40-config /etc/cont-init.d/40-config
