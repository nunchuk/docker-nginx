############################################################ 
# Dockerfile to build nginx image 
# Based on Alpine:3.5
############################################################

FROM library/nginx:1.12.0-alpine
MAINTAINER XinYe <nunchuk@live.com>

# add AliCloud repository
# > If you are using Aliyun ECS, the package mirror server can be replaced by 
# > 'mirrors.cloud.aliyuncs.com', via Aliyun private network.
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/' /etc/apk/repositories

ENV TIMEZONE=Asia/Shanghai \
	TIMEZONE_DEPS=tzdata

# set timezone
RUN set -xe; \
	apk --update add --no-cache --virtual .build-deps \
                      $TIMEZONE_DEPS ; \
	cp /usr/share/zoneinfo/${TIMEZONE} /etc/localtime ; \
	echo ${TIMEZONE} > /etc/timezone

# clean up
RUN apk del .build-deps && \
	rm -rf /var/cache/apk/*