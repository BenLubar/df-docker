FROM benlubar/dwarffortress:dfhack-0.44.09-r1

ENV DF_AI_VERSION=0.44.09-r1 \
    DF_AI_ARCHIVE_NAME=df-ai-0.44.09-r1-linux-64-4.8.tar.gz \
    DF_AI_ARCHIVE_SHA1=e982f35e0c26bdc078e7a026e8be1c5fd1c491b9 \
    DF_AI_ASSETS_SHA1=bc7a9f027711f1ee5a7daa99b72d52d255d2216a \
    WEBLEGENDS_VERSION=0.44.09-r1 \
    WEBLEGENDS_ARCHIVE_NAME=weblegends-0.44.09-r1-linux-64-4.8.tar.gz \
    WEBLEGENDS_ARCHIVE_SHA1=076e7137555843eac1251082d40c0c6ed05a63ff

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
