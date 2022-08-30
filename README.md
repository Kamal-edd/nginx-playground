Welcome to this repo where I document my the things that I learn to do with **Nginx**. I will be using the [official documentation page](https://nginx.org/en/docs/), so I suggest you check it out too.\
Feel free to use and/or modify the code you find in here, and if you have any suggestions please make a pull request, I'd love to see what you got.

## 1. Download and install **Nginx** 
I'm on *Ubuntu 18.04*  
### Install the prerequisites:
```
sudo apt install curl gnupg2 ca-certificates lsb-release ubuntu-keyring
```
Import an official nginx signing key so apt could verify the packages authenticity. Fetch the key:
```
curl https://nginx.org/keys/nginx_signing.key | gpg --dearmor \
    | sudo tee /usr/share/keyrings/nginx-archive-keyring.gpg >/dev/null
```
Verify that the downloaded file contains the proper key:
```
gpg --dry-run --quiet --import --import-options import-show /usr/share/keyrings/nginx-archive-keyring.gpg
```
The output should contain the full fingerprint 573BFD6B3D8FBC641079A6ABABF5BD827BD9BF62 as follows:
```
    pub   rsa2048 2011-08-19 [SC] [expires: 2024-06-14]
          573BFD6B3D8FBC641079A6ABABF5BD827BD9BF62
    uid                      nginx signing key <signing-key@nginx.com>
```
If the fingerprint is different, remove the file.

To set up the apt repository for stable nginx packages, run the following command:
```
echo "deb [signed-by=/usr/share/keyrings/nginx-archive-keyring.gpg] \
    http://nginx.org/packages/ubuntu `lsb_release -cs` nginx" \
    | sudo tee /etc/apt/sources.list.d/nginx.list
```

If you would like to use mainline nginx packages, run the following command instead:
```
echo "deb [signed-by=/usr/share/keyrings/nginx-archive-keyring.gpg] \
    http://nginx.org/packages/mainline/ubuntu `lsb_release -cs` nginx" \
    | sudo tee /etc/apt/sources.list.d/nginx.list
```
Set up repository pinning to prefer our packages over distribution-provided ones:
```
echo -e "Package: *\nPin: origin nginx.org\nPin: release o=nginx\nPin-Priority: 900\n" \
    | sudo tee /etc/apt/preferences.d/99nginx
```

To install nginx, run the following commands:
```
sudo apt update
sudo apt install nginx
```
for a complete guide on how to install in on your OS, you can check out the docs : [Installing nginx](https://nginx.org/en/docs/install.html)