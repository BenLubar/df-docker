FROM benlubar/dwarffortress:dfhack-0.44.07-alpha1

ENV DF_AI_VERSION=0.44.07-alpha1 \
    DF_AI_ARCHIVE_NAME=df-ai-0.44.07-alpha1-linux-64-4.8.tar.gz \
    DF_AI_ARCHIVE_SHA1=3019241f87df29d3a1e1892d964bccb2eb89b8c8 \
    DF_AI_ASSETS_SHA1=ad2dbe7358dd64200cba74d1a846ec9ebf96ec3a \
    WEBLEGENDS_VERSION=0.44.07-alpha1 \
    WEBLEGENDS_ARCHIVE_NAME=weblegends-0.44.07-alpha1-linux-64-4.8.tar.gz \
    WEBLEGENDS_ARCHIVE_SHA1=b4b85cf9972f31c3f7a3a3383dad02a168daba17

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
