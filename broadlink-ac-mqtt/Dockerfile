ARG BUILD_FROM
FROM $BUILD_FROM

# Build the proxy from the resilient fork that isolates per-device failures.
COPY rootfs /

RUN apk add --no-cache gcc g++ make libffi-dev openssl-dev \
    && pip3 install --no-cache-dir -U \
    paho-mqtt \
    pyyaml \
    cryptography~=42.0 \
    && cd /usr/share \
    && wget -c https://github.com/uzairfarooq/broadlink_ac_mqtt/archive/refs/tags/1.2.4.tar.gz -O - | tar -xz \
    && chmod a+x /etc/services.d/broadlink-ac-mqtt/* \
    && python3 -m py_compile /usr/share/broadlink_ac_mqtt-1.2.4/broadlink_ac_mqtt/AcToMqtt.py
