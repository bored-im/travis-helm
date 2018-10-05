### Hosting helm charts via github

Helm charts repository is nothing but bunch of zip files served by a server.
Its mostly static data. Follow below steps at root directory, and get your
PR merged.

Following: https://docs.helm.sh/developing_charts/#hosting-chart-repositories

~~~sh
# First create zip files for charts
cd /path/to/cloned/repo/of/travis-helm
helm package .

# Now move generated packages to docs folder
mv travis-helm-*.tgz docs

# Update index file in docs folder
cd docs
helm repo index --url=https://bored-im.github.io/travis-helm .
~~~


Now commit changes, open a PR and get it merged. Ensure that you change
version of charts before publishing.
