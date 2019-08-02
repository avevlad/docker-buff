FROM mongo:2.6

COPY buff-mongo-dump/gbuff /gbuff
RUN ls -la
RUN ls -ls gbuff
CMD mongorestore --host mongodb gbuff
