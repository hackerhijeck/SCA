## OWASP Dependency Check Tool Usage
 
### Installation:
```
$ apt update -y && mkdir OWASP && cd OWASP
$ wget https://github.com/jeremylong/DependencyCheck/releases/download/v9.0.7/dependency-check-9.0.7-release.zip
$ unzip <file-name>.zip
$ cd <dependency-check>/bin

## For NVD updates:
$ ./dependency-check.sh --scan dependency-check-9.0.7-release.zip

## It will take more time to update, Use NVD ApiKey to fast update:
$ ./dependency-check.sh --nvdApiKey <apiKey> --scan dependency-check-9.0.7-release.zip
```
### Usage Commands:
```
$ ./dependency-check.sh --help

--project     <Project-name>       Choose any project name (eg. Dep-Check)
-s/--scan     <Path>	             The path to scan - this option can be specified multiple times. (e.g. 'path/**/*.jar')
-f        	  <Format>             Report format (HTML, XML, CSV, JSON, JUNIT, SARIF, JENKINS, GITLAB)
-o/--out      <Output>             Output file name (For HTML=output.html, For XML=output.xml etc)
-v 	          <Version>            OWASP Dependency Version details.

$ ./dependency-check.sh --project <project-name> --scan /path/file.jar --out output.html
$ ./dependency-check.sh --project <project-name> --scan /path/file.zip --out output.html

N.B: Multiple .jar files can be scanned with a zip file.
```
