FROM benlubar/dwarffortress:dfhack-0.44.12-r3

ENV DF_AI_VERSION=0.44.12-r3 \
    DF_AI_ARCHIVE_NAME=df-ai-0.44.12-r3-linux-64-4.8.tar.gz \
    DF_AI_ARCHIVE_SHA1=32e7b06cc2decced16c53523e3d9e058f6ee7e9c \
    DF_AI_ASSETS_SHA1=38bc78a569e483a086de4f6aeebd69c4c75addb1 \
    WEBLEGENDS_VERSION=0.44.12-r3 \
    WEBLEGENDS_ARCHIVE_NAME=weblegends-0.44.12-r3-linux-64-4.8.tar.gz \
    WEBLEGENDS_ARCHIVE_SHA1=a1941c938481dab81fe4d88f2e9d8e3490a74c73

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
