
== Setup environment
```
cd c:
mkdir liferay; cd liferay
mkdir bundles trunk workspace

cd trunk
git clone https://github.com/panser/liferay-portal --depth 1 -b 6.2.x 62x-portal
cd 62x-portal
git remote add upstream git@github.com:liferay/liferay-portal.git
cd ..

git clone https://github.com/liferay/liferay-plugins --depth 1 -b 6.2.x 62x-plugins
cd 62x-plugins
git remote add upstream git@github.com:liferay/liferay-plugins.git
cd ..

cd 62x-portal
vim app.server.spanov.properties
 app.server.parent.dir=${project.dir}/../../bundles
ant -f build-dist.xml unzip-tomcat
ant -f build.xml all
cd ..

cd 62x-plugins
vim build.spanov.properties
 app.server.parent.dir=c:/liferay/bundles
 app.server.tomcat.dir=${app.server.parent.dir}/tomcat-7.0.42
ant
cd ..

cd C:\liferay\bundles\tomcat-7.0.25\bin
.\catalina.bat run
```

== Links
  [ https://www.liferay.com/community/wiki/-/wiki/Main/Liferay+Contributor+Development+Environment+Setup ]
  [ http://www.liferay.com/community/wiki/-/wiki/Main/Contribute+using+Git+and+GitHub ]
  [ https://www.liferay.com/community/wiki/-/wiki/Main/Integrated+Development+Environments ]
  