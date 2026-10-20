FROM debian:bookworm-slim AS builder

RUN apt-get update \
    && apt-get install -y --no-install-recommends curl ca-certificates bash findutils \
    && rm -rf /var/lib/apt/lists/*

RUN curl -fsSL https://x.ai/cli/install.sh | bash

FROM debian:bookworm-slim AS runner

RUN apt-get update \
    && apt-get install -y --no-install-recommends ca-certificates git \
    && rm -rf /var/lib/apt/lists/*

COPY --from=builder /usr/local/bin/grok /usr/local/bin/grok

RUN useradd --create-home --shell /bin/bash grok
USER grok
WORKDIR /workspace

ENTRYPOINT ["grok"]
