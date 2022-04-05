FROM debian:11-slim AS builder
RUN apt-get update && \
    apt-get install --no-install-suggests --no-install-recommends --yes python3-venv && \
    python3 -m venv /venv &&\
    /venv/bin/pip install --upgrade pip setuptools wheel
    
FROM builder
COPY . /usr/src
WORKDIR /usr/src
RUN /venv/bin/pip install -r requirements.txt

COPY --from=build-venv /venv /venv

#FROM gcr.io/distroless/python3-debian11
# COPY --from=build-venv /venv /venv

# dangourous below
# COPY --from=builder /bin /bin
