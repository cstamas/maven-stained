# Maven fix version

Ref:
https://www.reddit.com/r/java/comments/1lwh5b5/mavens_transitive_dependency_hell_and_how_we/

## Steps
* checkout this repo (do not cd as settings.xml uses rel paths for simplicity)
* `mvn -s settings.xml -f library install` to build library
* `mvn -s settings -f app install` to build app
* inspect contents of `app/target/app-1.0-SNAPSHOT-jar-with-dependencies.zip`
* buy me a beer

