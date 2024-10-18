# Base image
FROM node:lts-alpine as base

FROM base AS deps

# Set the working directory
WORKDIR /app

# Install dependencies
COPY package*.json ./
RUN npm install

# Expose the necessary port
EXPOSE 3000


FROM base AS dev

WORKDIR /app
COPY --from=deps /app/node_modules ./node_modules
COPY . .

ENV NEXT_TELEMETRY_DISABLED 1


FROM base AS runner
# Copy application files
COPY --from=deps /app/node_modules ./node_modules
COPY . .

# Build the Next.js application
# RUN npm run build

ENV NEXT_TELEMETRY_DISABLED 1

# Expose the necessary port
EXPOSE 3000

# Run the Next.js application
CMD ["npm", "run", "start"]