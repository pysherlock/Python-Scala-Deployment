# Scala Object, Class, and Trait in Spark

## 1. Object

An object is a class that has exactly one instance. It is created lazily when it is referenced, like a lazy val.

### Companion objects
An object with the same name as a class is called a companion object. Conversely, the class is the object’s companion class. 
A companion class or object can access the private members of its companion. Use a companion object for methods and values which are not specific to instances of the companion class.

```Example:
import scala.math._

case class Circle(radius: Double) {
  import Circle._
  def area: Double = calculateArea(radius)
}

object Circle {
  private def calculateArea(radius: Double): Double = Pi * pow(radius, 2.0)
}

val circle1 = new Circle(5.0)

circle1.area
```

As a top-level value, an object is a singleton.

In Spark, Objects, as singletons, **are never shipped to executors**. They are initialized locally, whenever objects is accessed for the first time.

So it means, if you are trying to use a singleton Object in executors (like RDD.map), the executors will try to initialize the object locally. In this case, if this object has some dependecies (like a file to be read) which are only available in driver, the initialization will be falied.

For examples:

When you want to ship something to executors, it should be Class rather than Objcet.

Ref: 1. https://docs.scala-lang.org/tour/singleton-objects.html 
     
     2. https://stackoverflow.com/questions/47241882/spark-object-singleton-serialization-on-executors

## 2. Trait

A trait is a kind of class that enables ***multiple inheritance***


## 3. Class

The Class which can be shipped to executors has to be Serializable. 
