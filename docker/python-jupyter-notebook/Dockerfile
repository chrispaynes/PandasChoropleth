FROM python:3.7-alpine3.8

ENV PATH /root/.local/bin:"$PATH"

EXPOSE 8888

RUN set -ex \
	&& apk add --no-cache --virtual .build-deps  \
        g++ \
		gcc \
	&& apk add --no-cache --virtual .postgis-rundeps-testing \
        --repository http://dl-cdn.alpinelinux.org/alpine/edge/testing \
		geos \
    && pip3 install --user cython \
		geopandas \
		jupyter \
        nbconvert \
		# libgdal-dev \
        bash \
		fiona

WORKDIR /notebook
COPY ./notebook .

CMD [ "sh", "-c", "jupyter notebook --allow-root" ]
