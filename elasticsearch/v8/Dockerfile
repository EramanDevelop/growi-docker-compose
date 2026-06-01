# Elasticsearch 8.x image for GROWI with Japanese full-text search built in.
# See elasticsearch/v9/Dockerfile for why the plugins are baked in at build time.
FROM docker.elastic.co/elasticsearch/elasticsearch:8.19.14

# analysis-kuromoji : Japanese morphological analyzer (required for 日本語全文検索)
# analysis-icu      : Unicode normalization / segmentation
RUN bin/elasticsearch-plugin install --batch analysis-kuromoji analysis-icu

COPY config/elasticsearch.yml /usr/share/elasticsearch/config/elasticsearch.yml
