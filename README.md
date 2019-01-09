# githook
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
