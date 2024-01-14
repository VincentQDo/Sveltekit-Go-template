FROM alpine:3.19.0

# Install Go
RUN apk add --no-cache go

# Install Node.js (SvelteKit will need it)
RUN apk add --no-cache nodejs npm

# Install additional dependencies, tools, etc.
RUN apk add --no-cache git
# Optionally: Install SvelteKit globally
RUN npm install -g @sveltejs/kit

# Set a working directory (can be changed if you wish)
WORKDIR /app
# Create a non-root user and switch to it
RUN adduser -D appuser
USER appuser

# Set up the environment for Go
ENV GO111MODULE=on \
    GOPATH="/home/appuser/go" \
    PATH="$PATH:/home/appuser/go/bin"

# Install Go tools
RUN go install github.com/cweill/gotests/gotests@v1.6.0 \
    && go install github.com/fatih/gomodifytags@v1.16.0 \
    && go install github.com/josharian/impl@v1.1.0 \
    && go install github.com/haya14busa/goplay/cmd/goplay@v1.0.0 \
    && go install github.com/go-delve/delve/cmd/dlv@latest \
    && go install honnef.co/go/tools/cmd/staticcheck@latest \
    && go install golang.org/x/tools/gopls@latest
