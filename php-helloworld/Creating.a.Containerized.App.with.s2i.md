
Create a new branch
```
cd ~/DO180-apps
git checkout master
git checkout -b s2i
git push -u orgin s2i
```
Is the pod running
```
oc get pods
```
Examine the logs for this build
```
oc logs --all-containers -f php-helloworld-1-build
```
Review the deployment for this application
```
oc describe deployment/php-helloworld
```
Make a small modification to `D0180-apps/php-helloworld/index.php`
Push change back to origin
```
git add .
git commit -m 'Changed index page contents'
git push origin s2i
```
Start a new Source-to-Image build process and wait for it to build and deploy
```
oc start-build php-helloworld
oc logs php-helloworld-2-build -f
```
After completion, use the `oc get pods` command to verify that the new version of the application is running
Done.
