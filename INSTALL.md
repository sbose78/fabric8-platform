## Installing on MiniShift

The following are the instructions for installing fabric8 on minishift:

* [download the minishift distribution for your platform](https://github.com/minishift/minishift/releases) extract it and place the `minishift` binary on your `$PATH` somewhere
* start up minishift via something like this (on OS X):

```
minishift start --vm-driver=xhyve --memory=7000 --cpus=4 --disk-size=50g
```

### Setup GitHub client ID and secret

We now have GitHub integration which for now requires a manual OAuth setup to obtain a clientid and secret that we will give to keycloak. 

![Register OAuth App](./images/register-oauth.png)

Once you have found your client ID and secret for the new fabric8 app on your github settings then type the following:

```
export GITHUB_OAUTH_CLIENT_ID=TODO
export GITHUB_OAUTH_CLIENT_SECRET=TODO
```

where the above `TODO` text is replaced by the actual client id and secret from your github settings page!

### Run the install script

* now run the [install.sh](https://github.com/fabric8io/fabric8-platform/blob/master/install.sh) script on the command line:

```
bash <(curl -s https://raw.githubusercontent.com/fabric8io/fabric8-platform/master/install.sh)
```

* if you want to install a specific version of the [fabric8 system template](http://central.maven.org/maven2/io/fabric8/platform/packages/fabric8-system/) then you can pass it on the command line as an argument. Or add the argument `local` to use a local build.


### Cleanup and re-try

If for some reason, your installation isn't working and you wish to restart the installation process, here's hhow you could do a cleanup using [gofabric8](https://github.com/fabric8io/gofabric8#install--update--run)  :
* gofabric cleanup
* minishift stop

