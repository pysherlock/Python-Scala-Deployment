# Initialization of Object, Class, and Traid in Spark

## 1. Object

An object is a class that has exactly one instance. It is created lazily when it is referenced, like a lazy val.

As a top-level value, an object is a singleton.

In Spark, Objects, as singletons, **are never shipped to executors**. They are initialized locally, whenever objects is accessed for the first time.

For examples:

When you want to ship something to executors, it should be Class rather than Objcet.

Ref: https://docs.scala-lang.org/tour/singleton-objects.html
     https://stackoverflow.com/questions/47241882/spark-object-singleton-serialization-on-executors

## 2. Trait

## 3. Class
