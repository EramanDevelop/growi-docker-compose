# Elasticsearch 9.x image for GROWI with Japanese full-text search built in.
#
# The plugins are installed at *build* time and baked into the image instead of
# being downloaded on every container start via `elasticsearch-plugins.yml`.
# Downloading plugins at start-up requires outbound network access to
# artifacts.elastic.co on each boot; on hosts with restricted / proxied egress
# (e.g. Coolify) that download fails and the Elasticsearch container crashes,
# which in turn blocks the `app` container (it waits for ES to become healthy).
# Baking the plugins in makes start-up deterministic and offline-friendly.
FROM docker.elastic.co/elasticsearch/elasticsearch:9.3.3

# analysis-kuromoji : Japanese morphological analyzer (required for 日本語全文検索)
# analysis-icu      : Unicode normalization / segmentation
RUN bin/elasticsearch-plugin install --batch analysis-kuromoji analysis-icu

# Bake the HTTP / CORS / security settings into the image so the container does
# not depend on a bind-mounted config file at runtime.
COPY config/elasticsearch.yml /usr/share/elasticsearch/config/elasticsearch.yml
