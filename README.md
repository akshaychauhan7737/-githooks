# githook
```
# Add your server as a Git remote called 'deploy'
git remote add deploy ssh://<your-name>@<your-ip>/srv/git/<your-project>.git/
# Push your code and deploy
git push deploy master
```

/srv/git/<your-app>.git/hooks/post-receive

```
#!/bin/sh
# The production directory
TARGET="/srv/www/<your-app>"
# A temporary directory for deployment
TEMP="/srv/tmp/<your-app>"
# The Git repo
REPO="/srv/git/<your-app>.git"
# Deploy the content to the temporary directory
mkdir -p $TEMP
git --work-tree=$TEMP --git-dir=$REPO checkout -f
cd $TEMP
# Do stuffs, like npm install…
# Replace the production directory
# with the temporary directory
cd /
rm -rf $TARGET
mv $TEMP $TARGET
```


push to the server
```
git add . 
git commit -m "<commit message>"
git push deploy master
```
