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
# Optionally, create a normal user
RUN adduser -D appuser

# Switch to non-root user
USER appuser
