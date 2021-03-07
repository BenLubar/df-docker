FROM benlubar/dwarffortress:dfhack-0.47.05-r1

ENV DF_AI_VERSION=0.47.05-r1 \
    DF_AI_ARCHIVE_NAME=df-ai-0.47.05-r1-linux-64-4.8.tar.gz \
    DF_AI_ARCHIVE_SHA1=28073db2b7deb60cef2748ecddd0fe11cda90fed \
    DF_AI_ASSETS_SHA1=56cabb1cc8ec467568b03a53d991d8b1d25cd621 \
    WEBLEGENDS_VERSION=0.47.05-r1 \
    WEBLEGENDS_ARCHIVE_NAME=weblegends-0.47.05-r1-linux-64-4.8.tar.gz \
    WEBLEGENDS_ARCHIVE_SHA1=11bfc3bf57b84bbf0543e115c73f128774884b52

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
