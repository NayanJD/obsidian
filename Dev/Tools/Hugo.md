
I am currently using [hugo](https://gohugo.io/) for hosting my portfolio. In future, I am going to add blog to it too. Currently my focus is on using Markdown for my blog as well. I might try [ghost](https://ghost.org/) in future if newsletter is needed (a big if 🙄).

#### Installation

I am currently using [adritian-free-hugo-theme](https://themes.gohugo.io/themes/adritian-free-hugo-theme/). Hugo `extended` installation is required. It can be done by downloading the .deb file from hugo's release page in github and run `dpkg -i <deb> package`. `dart-sass` needs to be installed by fetching using wget from github release page and adding the binary to path.

#### Running

`hugo server -D` can be used to run a development server locally. It will bind to localhost at port `1313`. If hugo is run in a remote server, the port `1313` can be forwarded to local using command `ssh -L 1313:localhost:1313 <username>@<IP or host>`  ([[SSH]]). 

To host the blog in a remote server, first change the `baseURL` to the IP or the hostname in hugo.toml and run `hugo`. This would build the html/js/css into the public folder. This public folder can be used to host the portfolio using reverse proxies like `nginx`:

```bash
cd <hugo directory>
nerdctl run --name nginx -v ./public:/usr/share/nginx/html:ro -d -p 80:80 nginx
```


#### Hosting

Currently it is being hosted by Github Pages using Github Actions. The blog is stored in `nayanjd.github.io` repo and Github Actions publishes the site by building using `hugo` command.