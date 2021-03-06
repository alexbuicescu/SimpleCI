
1. Run the app:
    ```bash
    flask run --host=0.0.0.0 --port=8000

    ```

1. Set the necessary environment variables:
    ```bash
    mkdir ~/buildMessages/
    sudo chmod -R 777 ~/buildMessages/

    # github access token
    export gitToken=123

    # can be something like: https://ci.myapp.com
    export CI_URL=myurl

    # set it up on github.com for your webhook
    export GITHUB_SECRET=mygitsecret

    # must be the following format: "<repo_owner>/<repo_name>"
    export REPO_PATH=alexbuicescu/simpleCI

    # variable for sync/async
    export SYNC=true

    ```

1. Update or create your own ```run_tests.sh``` and give it run permissions:
    ```bash
    # needed to run the shell script
    chmod +x run_tests.sh

    ```

1. Add a new user and password for **nginx** (replace <username> with the actual username, see more [here](http://www.genecasanova.com/labs/security-online/nginx-password-authentication.html#.W1g7RNgzZN0)):
    ```bash
    printf "<username>:`openssl passwd -apr1`\n" >> ~/.htpasswd

    ```

1. Set permissions for passwords:
    ```bash
    chmod 644 ~/.htpasswd

    ```

1. Start nginx:
    ```bash
    cd simpleCI

    docker run \
    --rm \
    -p 80:80 \
    --name ci-nginx \
    -v $HOME/buildMessages:/buildMessages:ro \
    -v $HOME/.htpasswd:/.htpasswd:ro \
    -v $(pwd)/nginx.conf:/etc/nginx/nginx.conf:ro \
    -d nginx

    ```

1. Screenshots folder architecture:
    1. screenshots/android/image.png
    1. screenshots/ios/image.png
    1. screenshots/webMobile/image.png
    1. screenshots/webDesktop/image.png