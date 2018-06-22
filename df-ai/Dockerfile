FROM benlubar/dwarffortress:dfhack-0.44.10-r2

ENV DF_AI_VERSION=0.44.10-r2 \
    DF_AI_ARCHIVE_NAME=df-ai-0.44.10-r2-linux-64-4.8.tar.gz \
    DF_AI_ARCHIVE_SHA1=f1490557ec8e635a84ed0cc4e507eeb1a3cdad2d \
    DF_AI_ASSETS_SHA1=15fe1ea5f250611b7c02250e2ed77f80726d6a05 \
    WEBLEGENDS_VERSION=0.44.10-r2 \
    WEBLEGENDS_ARCHIVE_NAME=weblegends-0.44.10-r2-linux-64-4.8.tar.gz \
    WEBLEGENDS_ARCHIVE_SHA1=b4bcc519964c1979a47a0211d68dcf271b47dc4a

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
