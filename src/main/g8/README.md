# $name$

Scala library providing $nameCamel$[R,V] typeclass derivation.

## Usage

Use with SBT

    libraryDependencies += "$organization$" % "$name$_3" % "0.9.0"

or with SCALA-CLI

    //> using dep $organization$::$name$:0.9.0

## Examples

```scala

    case class Person(firstName: String, lastName: String, address: Address)
    case class Address(street1: String, street2: Option[String] = None, postcode: String, town: String, country: String)

    val town$nameCamel$ = $nameCamel$[Person].address.town
    
    val mike = Person("Mike","Hart", Address("1 Abbey Road", None, "BN15 KJ", "Exeter", "United Kingdom"))

    val town =  town$nameCamel$.get(mike)
    town$nameCamel$.set(mike)("Derby")
    town$nameCamel$.update(mike, town => town.toUpperCase())

```
