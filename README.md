
## Deploy Hadron on OpenShift PaaS

With this seed project you will be able to get your [Hadron](https://github.com/hadronjs/hadron) blog up and running
on the OpenShift PaaS (...and for free BTW).

* Create a free account at [https://www.openshift.com](https://www.openshift.com/) if you don't have one yet.
* Install the `rhc` utility for your platform([instructions](https://www.openshift.com/developers/rhc-client-tools-install)).
* Create a namespace, if you haven't already done so
```
$ rhc domain create <yournamespace>
```

* Create a `nodejs-0.10` application (you can name it anything via `-a`)
```
$ rhc app create -a hadron -t nodejs-0.10
```

* Cleanup your new project
```
$ cd hadron
$ rm -rf ./node_modules server.js index.html deplist.txt
```

* Checkout the `hadron-seed` repository
```
$ git remote add hadron-seed -m master https://github.com/hadronjs/hadron-seed.git
$ git pull -s recursive -X theirs hadron-seed master
```

* Checkout the `hadron-openshift` repository
```
$ git remote add hadron-openshift -m master https://github.com/hadronjs/hadron-openshift-seed.git
$ git pull -s recursive -X theirs hadron-openshift master
```

* Install npm dependencies
```
$ npm install --production
```

* Then push the repo to OpenShift
```
$ git add -A
$ git commit -m "Deploying initial version"
$ git push
```

* That's it, you can now access Hadron at `http://hadron-$yournamespace.rhcloud.com`
* Access the admin interface at `http://hadron-$yournamespace.rhcloud.com/admin`. Use admin/admin to login 
  (**change the admin password first thing after login!**)

