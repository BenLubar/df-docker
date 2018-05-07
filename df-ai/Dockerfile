FROM benlubar/dwarffortress:dfhack-0.44.10-alpha1

ENV DF_AI_VERSION=0.44.10-alpha1 \
    DF_AI_ARCHIVE_NAME=df-ai-0.44.10-alpha1-linux-64-4.8.tar.gz \
    DF_AI_ARCHIVE_SHA1=a3fb3b4994c0e1b0f1e357a14d653e5503d77b25 \
    DF_AI_ASSETS_SHA1=60b10974d21ce305a8a2ebf1680517dc4b9d68e5 \
    WEBLEGENDS_VERSION=0.44.10-alpha1 \
    WEBLEGENDS_ARCHIVE_NAME=weblegends-0.44.10-alpha1-linux-64-4.8.tar.gz \
    WEBLEGENDS_ARCHIVE_SHA1=7cfeb90794752b8a10bcd8a3360ec0898a9f4e4a

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
