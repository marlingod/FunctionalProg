
* A functor is a data type that defines how a transformation known as a map applies to it. Scala implements functors as type classes with a map method.
* A monad is a wrapper around an existing data type. It applies a transformation to a data of wrapper type and returns a value of the same wrapper type. Scala implements monads as type classes with unit and flatMap methods. Monads extends functors in Scala.
Monads provide the ability for those collections to do the following:
+ Create the collection
** Transform the elements of the collection
** Flatten nested collections
```scala
trait Monad[M[_]] {  
  def unit[T](a: T): M[T]     
  def map[U,V](m: M[U])(f U =>V): M[V]                
  def flatMap[U,V](m: M[U])(f: U =>M[V]): M[V]
}
```
A monad abstraction consists of the following three elements:                                                   A type constructor, M[A], expressed in Scala as trait M[A] or case class M[A] or class M[A].                                                   A unit method that lifts a computation into the monad. In Scala, you use the invocation of the class constructor for this purpose.                                                   A bind method, which sequences computations. In Scala, flatMap is the bind.
Try is a monad as defined in the Scala standard library.[4] Try implements flatMap, which allows the sequencing of effects that we just discussed. Using the compositional power of Try, you can define operations composed from primitive ones, as you’ll see shortly when you implement a transfer operation from debit and credit.


https://bartoszmilewski.com/2015/01/20/functors/
Functional and Reactive Domain Modeling

Scala for Machine Learning - Second Edition

