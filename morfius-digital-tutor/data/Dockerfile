ARG MARKETPLACE_TOOLS_TAG
FROM gcr.io/cloud-marketplace-tools/k8s/deployer_envsubst/onbuild

ENV WAIT_FOR_READY_TIMEOUT 7200
ENV TESTER_TIMEOUT 7200

COPY data-test/ /data-test/