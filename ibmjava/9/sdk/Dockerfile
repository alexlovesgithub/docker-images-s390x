# (C) Copyright IBM Corporation 2016, 2017
#
# ------------------------------------------------------------------------------
#               NOTE: THIS DOCKERFILE IS GENERATED VIA "update.sh"
#
#                       PLEASE DO NOT EDIT IT DIRECTLY.
# ------------------------------------------------------------------------------
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#      http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

FROM clefos:clefos7

MAINTAINER The ClefOS Project <neale@sinenomine.net>

RUN yum -y update \
    && yum install -y wget tar ca-certificates \
    && yum clean all \
    && rm -rf /var/cache/yum/* /tmp/* /var/log/yum.log

ENV JAVA_VERSION 1.9.0_ea2

RUN ESUM="6e823afa1df83e364381f827f4244bfe29b0ddd58ef0203eb60df9b8c0d123af" \
    && BASE_URL="https://public.dhe.ibm.com/ibmdl/export/pub/systems/cloud/runtimes/java/meta/" \
    && YML_FILE="sdk/linux/s390x/index.yml" \
    && wget -q -U UA_IBM_JAVA_Docker -O /tmp/index.yml $BASE_URL/$YML_FILE \
    && JAVA_URL=$(cat /tmp/index.yml | sed -n '/'$JAVA_VERSION'/{n;p}' | sed -n 's/\s*uri:\s//p' | tr -d '\r') \
    && wget -q -U UA_IBM_JAVA_Docker -O /tmp/ibm-java.bin $JAVA_URL \
    && echo "$ESUM  /tmp/ibm-java.bin" | sha256sum -c - \
    && echo "INSTALLER_UI=silent" > /tmp/response.properties \
    && echo "USER_INSTALL_DIR=/opt/ibm/java" >> /tmp/response.properties \
    && echo "LICENSE_ACCEPTED=TRUE" >> /tmp/response.properties \
    && mkdir -p /opt/ibm \
    && chmod +x /tmp/ibm-java.bin \
    && /tmp/ibm-java.bin -i silent -f /tmp/response.properties \
    && rm -f /tmp/response.properties \
    && rm -f /tmp/index.yml \
    && rm -f /tmp/ibm-java.bin

ENV JAVA_HOME=/opt/ibm/java \
    PATH=/opt/ibm/java/bin:$PATH
RUN yum erase -y wget tar     && yum clean all     && rm -rf /var/cache/yum/* /tmp/* /var/log/yum.log
