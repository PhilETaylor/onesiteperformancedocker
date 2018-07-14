FROM mysql:5.7
RUN echo "lower_case_table_names=1 >> /etc/mysql/conf.d/docker.cnf"
RUN echo "query_cache_size=268435456 >> /etc/mysql/conf.d/cache.cnf"
RUN echo "query_cache_type=1 >> /etc/mysql/conf.d/cache.cnf"
RUN echo "query_cache_limit=1048576 >> /etc/mysql/conf.d/cache.cnf"
