# Helm charts for opensource projects

#### Step 0: Get helm working

~~~sh
> helm init
> kubectl create serviceaccount --namespace kube-system tiller
> kubectl create clusterrolebinding tiller-cluster-rule --clusterrole=cluster-admin
    --serviceaccount=kube-system:tiller
> kubectl patch deploy --namespace kube-system tiller-deploy
    -p '{"spec":{"template":{"spec":{"serviceAccount":"tiller"}}}}'
~~~

This helm + tiller installation is to get you started asap. If you need
more control over security, please open a github issue with your
requirements, we would be more than happy to help out.

#### Install Travis

Now add travis chart repository to your helm config

~~~
helm repo add bored-im https://bored-im.github.io/travis-helm
~~~

After adding a new helm repository, install travis as helm package

~~~sh
> helm install --name=travis bored-im/travis-helm
~~~
