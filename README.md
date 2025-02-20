scala-cli-seed
===

A [Giter8](http://www.foundweekends.org/giter8/) template for creating scala-cli project with scripts facilitating Sonatype deployment.

How to create a new project based on the template?
---

* Go to directory where you want to create the template
* Decide your project name (the hardest part :))
* Run the command

    `sbt new encalmo/y --branch master --name="example" --organization="org.encalmo" --repository="encalmo/example" --package="org.encalmo.example" -o example`

or    

* Install g8 commandline tool (http://www.foundweekends.org/giter8/setup.html)
* Run the command

    `g8 encalmo/y --branch master --name="example" --organization="org.encalmo" --repository="encalmo/example" --package="org.encalmo.example" -o example`
    
and then
    
    cd example
    git init
	git add .
	git commit -m start
  
* Test generated project using command 

    `scala-cli --power test project.scala --suppress-experimental-warning`
    

How to test the template and generate an example project?
---

* Run `./test.sh` 

An example project will be then created and tested in `target/sandbox/example`

How to modify the template?
---

 * review template sources in `/src/main/g8`
 * modify files as you need, but be careful about placeholders, paths and so on
 * run `./test.sh` in template root to validate your changes
 
or (safer) ...

* run `./test.sh` first
* open `target/sandbox/example` in your preferred IDE, 
* modify the generated example project as you wish, 
* build and test it as usual, you can run `scala-cli test project.scala`,
* when you are done switch back to the template root
* run `./update-g8.sh` in order to port your changes back to the template.
* run `./test.sh` again to validate your changes

What is in the template?
--

Assuming the command above 
the template will supply the following values for the placeholders:

    $packaged$ -> org/encalmo/example
	$package$ -> org.encalmo.example
	$repository$ -> encalmo/example
	$organization$ -> org.encalmo
	$name$ -> example
	$nameCamel$ -> Example

and produce the folders and files as shown below:

    ├── .github
	│   └── workflows
	│       ├── buildAndPublishPackage.yaml
	│       └── release.yaml
	│
	├── .gitignore
	├── .scalafmt.conf
	├── Example.scalax
	├── ExampleSpec.test.scala
	├── LICENSE
	├── project.scala
	├── README.md
	└── scripts
	    ├── computeNewVersion.sc
	    └── createReleaseBundle.sc