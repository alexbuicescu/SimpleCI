
1. Run the app:
    ```bash
    flask run --host=0.0.0.0 --port=8000

    ```

1. Set the necessary environment variables:
    ```bash
    # needed to run the shell script
    chmod +x run_tests.sh

    # github access token
    export gitToken=123

    # can be something like: https://ci.myapp.com
    export CI_URL=myurl

    # set it up on github.com for your webhook
    export GITHUB_SECRET=mygitsecret

    ```

1. Update or create your own ```run_tests.sh``` and give it run permissions:
    ```bash
    # needed to run the shell script
    chmod +x run_tests.sh

    ```

1. Start nginx:
```bash
docker run \
-p 8080:80 \
--name ci-nginx \
-v $HOME/buildMessages:/buildMessages \
-v $(pwd)/nginx.conf:/etc/nginx/nginx.conf:ro \
-d nginx

```
