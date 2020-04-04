FROM benlubar/dwarffortress:dfhack-0.47.04-beta1

ENV DF_AI_VERSION=0.47.04-beta1 \
    DF_AI_ARCHIVE_NAME=df-ai-0.47.04-beta1-linux-64-4.8.tar.gz \
    DF_AI_ARCHIVE_SHA1=ef45887c9f0537a60f950d217159a0431f9662c3 \
    DF_AI_ASSETS_SHA1=2e97913cb531a8668895f181745276c6a749d58d \
    WEBLEGENDS_VERSION=0.47.04-beta1 \
    WEBLEGENDS_ARCHIVE_NAME=weblegends-0.47.04-beta1-linux-64-4.8.tar.gz \
    WEBLEGENDS_ARCHIVE_SHA1=832b64d7ec2ae57483602552f2ac62ad6c0f6f42

RUN curl -LSo df-ai.tar.gz https://github.com/BenLubar/df-ai/releases/download/${DF_AI_VERSION}/${DF_AI_ARCHIVE_NAME} \
 && curl -LSo df-ai-assets.zip https://github.com/BenLubar/df-ai/releases/download/${DF_AI_VERSION}/df-ai-assets.zip \
 && curl -LSo weblegends.tar.gz https://github.com/BenLubar/weblegends/releases/download/${WEBLEGENDS_VERSION}/${WEBLEGENDS_ARCHIVE_NAME} \
 && (echo "${DF_AI_ARCHIVE_SHA1} *df-ai.tar.gz"; \
     echo "${DF_AI_ASSETS_SHA1} *df-ai-assets.zip"; \
     echo "${WEBLEGENDS_ARCHIVE_SHA1} *weblegends.tar.gz") | sha1sum -c \
 && tar -xzvf df-ai.tar.gz -C hack/plugins \
 && unzip df-ai-assets.zip \
 && tar -xzvf weblegends.tar.gz -C hack/plugins \
 && rm -f df-ai.tar.gz df-ai-assets.zip weblegends.tar.gz \
 && echo "enable df-ai" >> dfhack.init

EXPOSE 5080
