#JCFLAGS = -target 1.1 #(is default)

# Set this to include any other files you want in your jar
EXTRAJARFILES ?=

all: zplet zjapp

../classes:
	mkdir -p ../classes

zplet: ../classes/org/zplet/Zplet.class

../classes/org/zplet/Zplet.class: main/java/org/zplet/Zplet.java ../classes
	javac $(JCFLAGS) -sourcepath $(PWD)/main/java -d ../classes main/java/org/zplet/Zplet.java

zjapp: ../classes/org/zplet/ZJApp.class

../classes/org/zplet/ZJApp.class: main/java/org/zplet/ZJApp.java ../classes
	javac $(JCFLAGS) -sourcepath $(PWD)/main/java -d ../classes main/java/org/zplet/ZJApp.java

zplet.jar: zplet zjapp
	cd ../classes && jar cvfm ../$@ ../manifest.txt org/zplet/*.class org/zplet/*/*.class org/zplet/*/*/*.class $(EXTRAJARFILES)

clean:
	find ../classes -type f -exec rm "{}" \;	
	find . -name "*~" -exec rm "{}" \;
