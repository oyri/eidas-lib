# eidas-lib

[security advice](./security/advisories/new)


## upload external jars
Prerequisite:
- folder of your choice (do not need a pom.xml here)
- maven installed
- your jar-fil is in the current folder
- settings.xml as described below in same folder

RUN:
```
mvn -s settings.xml deploy:deploy-file -Dfile=eidas-saml-engine-2.7.1.jar -DrepositoryId=github -Durl=https://maven.pkg.github.com/oyri/eidas-lib
```

Where settings.xml has this content:
```
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
	  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	  xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
						  https://maven.apache.org/xsd/settings-1.0.0.xsd">
  <servers>
	<server>
	  <id>github</id>
	 <username><USERNAME></username> 
	 <configuration>
		<httpHeaders>
		  <property>
			<name>Authorization</name>
			<value>Bearer <GH-classic-token-with-package_write-and-repo-rights></value>
		  </property>
		</httpHeaders>
	  </configuration>
	</server>
  </servers>
</settings>
```
