# Maven fix version

Ref:
https://www.reddit.com/r/java/comments/1lwh5b5/mavens_transitive_dependency_hell_and_how_we/

## Steps
* checkout this repo (do not cd as settings.xml uses rel paths for simplicity)
* `mvn -s settings.xml -f library install` to build library
* `mvn -s settings -f app install` to build app
* inspect contents of `app/target/app-1.0-SNAPSHOT-jar-with-dependencies.zip`
* buy me a beer


```
[cstamas@urnebes maven-fix-versions (main)]$ mvn -s settings.xml eu.maveniverse.maven.plugins:toolbox:tree -f app/ -DverboseTree
[INFO] Scanning for projects...
[INFO] 
[INFO] ------------------------< org.cstamas.fud:app >-------------------------
[INFO] Building app 1.0-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- toolbox:0.11.5:tree (default-cli) @ app ---
[INFO] org.cstamas.fud:app:jar:1.0-SNAPSHOT
[INFO] ├─org.cstamas.fud:library:jar:1.0 [compile]
[INFO] │ ╰─org.slf4j:slf4j-api:jar:1.7.36 [compile] (range '[1.7.36,1.7.36]')
[INFO] ╰─org.slf4j:slf4j-api:jar:2.0.17 [compile] (conflicts with 1.7.36)
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  0.470 s
[INFO] Finished at: 2025-07-11T15:29:55+02:00
[INFO] ------------------------------------------------------------------------
[cstamas@urnebes maven-fix-versions (main)]$ 
```
