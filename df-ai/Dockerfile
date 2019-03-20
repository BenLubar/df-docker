FROM benlubar/dwarffortress:dfhack-0.44.12-r2

ENV DF_AI_VERSION=0.44.12-r2 \
    DF_AI_ARCHIVE_NAME=df-ai-0.44.12-r2-linux-64-4.8.tar.gz \
    DF_AI_ARCHIVE_SHA1=9996812c1212cebf7c1874dd581725b4b66822fa \
    DF_AI_ASSETS_SHA1=5dd80e19160e81eae7576c013851af449162ebb2 \
    WEBLEGENDS_VERSION=0.44.12-r2 \
    WEBLEGENDS_ARCHIVE_NAME=weblegends-0.44.12-r2-linux-64-4.8.tar.gz \
    WEBLEGENDS_ARCHIVE_SHA1=9067b862a629758a13eaa6f6b50f92b716cef38c

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
