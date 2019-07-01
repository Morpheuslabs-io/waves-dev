# waves-dev (localhost version single node)
This version is for use in the local PC/laptop. This is a version of waves network with single node and explorer.
   # endpoints:
   - explorer can be opened at http://localhost:45555
   - node API can be opened at http://localhost:27558 (Note: Waves IDE settings doesn't accept http connection. Production and Test of BPaaS go via HTTPS. A modified version of Waves IDE may be able to use locally).
   
For your convenience you can change the explorer port currently set as 45555 and apiPort currently set as 27558 (change also the env url accordingly)

```
   ports:
      - "27558:6869"
    volumes:
      - ./node:/waves

  data-service-explorer:
    image: mlabsg/ml-waves-explorer
    entrypoint:
      - yarn
      - start:toolkit
      - --env.TOOLKIT_API_NODE_URL=http://localhost:27558
      - --env.TOOLKIT_NODE_LIST=http://localhost:27558
      - --env.NET_NAME=onyx
    depends_on:
      - node0
    restart: always
    ports:
      - "45555:8080"
```
