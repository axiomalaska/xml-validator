# xml-validator

Simple Java utility to validate that XML files are well formed and valid against their internally declared xsds and dtds.

Uses javax.xml.validation. The main method accepts a path to an XML file or an XML string as the single argument.

Example:

```
java -jar xml-validator.jar my-xml-file.xml
```

You can create a bash alias for easy access, like so:

```
mvn clean install
cp target/xml-validator-shaded.jar /usr/local/bin/xml-validator.jar
echo alias validate-xml=\'java -jar /usr/local/bin/xml-validator.jar\' >> ~/.bashrc
. ~/.bashrc
```

A vim command is also helpful:

```
echo command VXML !java -jar /usr/local/bin/xml-validator.jar % >> ~/.bashrc
```

This will allow you to quickly validate XML files in vim as you edit them (make sure you save the file first):

```
:w
:VXML
```

## Docker

Build the image:

```
DOCKER_BUILDKIT=1 docker build -t xml-validator .
```

Then run the validator against a document:

```
docker run --rm -v $(pwd)/some_doc.xml:/doc.xml xml-validator
```
