FROM luber/postgres-plv8:13-build AS build

ENV PLV8_VERSION=v3.0.0

RUN wget https://github.com/plv8/plv8/archive/v3.0.0.tar.gz
RUN tar -xvzf v3.0.0.tar.gz
RUN cd plv8-3.0.0 && make && make install


FROM postgres:13 AS final

RUN apt-get update && apt-get upgrade \
    && apt-get install -y libc++-dev

COPY --from=build /usr/share/postgresql/13/extension/plcoffee* /usr/share/postgresql/13/extension/
COPY --from=build /usr/share/postgresql/13/extension/plls* /usr/share/postgresql/13/extension/
COPY --from=build /usr/share/postgresql/13/extension/plv8* /usr/share/postgresql/13/extension/

COPY --from=build /usr/lib/postgresql/13/lib/plv8-3.0.0.so /usr/lib/postgresql/13/lib/plv8-3.0.0.so
COPY --from=build /usr/lib/postgresql/13/lib/pgxs /usr/lib/postgresql/13/lib/pgxs

COPY --from=build /usr/lib/postgresql/13/bin/pg_config /usr/lib/postgresql/13/bin/pg_config

RUN chmod -R 644 /usr/share/postgresql/13/extension/plcoffee* /usr/share/postgresql/13/extension/plls* /usr/share/postgresql/13/extension/plv8* \
    && chmod 755 /usr/lib/postgresql/13/lib/plv8-3.0.0.so \
    && chmod 755 /usr/lib/postgresql/13/bin/pg_config