FROM benlubar/dwarffortress:dfhack-0.47.04-r3

ENV DF_AI_VERSION=0.47.04-r3 \
    DF_AI_ARCHIVE_NAME=df-ai-0.47.04-r3-linux-64-4.8.tar.gz \
    DF_AI_ARCHIVE_SHA1=042a4b4803c9c9d70754ebb551d5deb562d076a0 \
    DF_AI_ASSETS_SHA1=17bcb093b273411c33c6b77906d410b7fa233b00 \
    WEBLEGENDS_VERSION=0.47.04-r3 \
    WEBLEGENDS_ARCHIVE_NAME=weblegends-0.47.04-r3-linux-64-4.8.tar.gz \
    WEBLEGENDS_ARCHIVE_SHA1=f6f36b627d7e15ec4a178d066ad920dbf5f630bc

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
