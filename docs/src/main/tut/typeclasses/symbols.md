---
layout: docs
title:  "Symbols"
section: "typeclasses"
---

# Symbols

Below is a list of symbols used in cats.

The `~>`, `⊥` and `⊤` symbols can be imported with `import cats._`.

All other symbols can be imported with `import cats.implicits._`

A scaladoc generated list is also available on the [Scaladoc symbols page](http://typelevel.org/cats/api/#index.index-_).

| Symbol     | Name                   | Type Class                                                                                  | Definition                             |
| ---------- | ---------------------- | ----------------------------------------------------------------------------------------    |--------------------------------------- |
| `fa |@| fb`| Cartesian builder      | [`Cartesian[F[_]]`]({{ site.sources }}/core/src/main/scala/cats/Cartesian.scala)            | `|@|(fa: F[A])(fb: F[B]): F[(A, B)]`   |
| `fa *> fb` | right apply            | [`Cartesian[F[_]]`]({{ site.sources }}/core/src/main/scala/cats/Cartesian.scala)            | `*>(fa: F[A])(fb: F[B]): F[A]`         |
| `fa <* fb` | left apply             | [`Cartesian[F[_]]`]({{ site.sources }}/core/src/main/scala/cats/Cartesian.scala)            | `<*(fa: F[A])(fb: F[B]): F[B]`         |
| `x === y`  | equals                 | [`Eq[A]`]({{ site.sources }}/kernel/src/main/scala/cats/kernel/Eq.scala)                    | `eqv(x: A, y: A): Boolean`             |
| `x =!= y`  | not equals             | [`Eq[A]`]({{ site.sources }}/kernel/src/main/scala/cats/kernel/Eq.scala)                    | `neqv(x: A, y: A): Boolean`            |
| `fa >>= f` | flatMap                | [`FlatMap[F[_]]`]({{ site.sources }}/core/src/main/scala/cats/FlatMap.scala)                | `flatMap(fa: F[A])(f: A => F[B]): F[B]`|
| `fa >> fb` | followed by            | [`FlatMap[F[_]]`]({{ site.sources }}/core/src/main/scala/cats/FlatMap.scala)                | `followedBy(fa: F[A])(fb: F[B]): F[B]` |
| `x |-| y`  | remove                 | [`Group[A]`]({{ site.sources }}/kernel/src/main/scala/cats/kernel/Group.scala)              | `remove(x: A, y: A): A`                |
| `x > y`    | greater than           | [`PartialOrder[A]`]({{ site.sources }}/kernel/src/main/scala/cats/kernel/PartialOrder.scala)| `gt(x: A, y: A): Boolean`              |
| `x >= y`   | greater than or equal  | [`PartialOrder[A]`]({{ site.sources }}/kernel/src/main/scala/cats/kernel/PartialOrder.scala)| `gteq(x: A, y: A): Boolean`            |
| `x < y`    | less than              | [`PartialOrder[A]`]({{ site.sources }}/kernel/src/main/scala/cats/kernel/PartialOrder.scala)| `lt(x: A, y: A): Boolean`              |
| `x <= y`   | less than or equal     | [`PartialOrder[A]`]({{ site.sources }}/kernel/src/main/scala/cats/kernel/PartialOrder.scala)| `lteq(x: A, y: A): Boolean`            |
| `x |+| y`  | Semigroup combine      | [`Semigroup[A]`]({{ site.sources }}/kernel/src/main/scala/cats/kernel/Semigroup.scala)      | `combine(x: A, y: A): A`               |
| `x <+> y`  | SemigroupK combine     | [`SemigroupK[F[_]]`]({{ site.sources }}/core/src/main/scala/cats/SemigroupK.scala)          | `combineK(x: F[A], y: F[A]): F[A]`     |
| `F ~> G`   | natural transformation | [`FunctionK[F[_], G[_]]`]({{ site.sources }}/core/src/main/scala/cats/arrow/FunctionK.scala)| `FunctionK` alias                      |
| `F :<: G`  | inject                 | [`Inject[F[_], G[_]]`]({{ site.sources }}/free/src/main/scala/cats/free/package.scala)      | `Inject` alias                         |
| `F :≺: G`  | inject                 | [`Inject[F[_], G[_]]`]({{ site.sources }}/free/src/main/scala/cats/free/package.scala)      | `Inject` alias                         |
| `⊥`        | bottom                 | [N/A]({{ site.sources }}/core/src/main/scala/cats/package.scala)                            | `Nothing`                              |
| `⊤`        | top                    | [N/A]({{ site.sources }}/core/src/main/scala/cats/package.scala)                            | `Any`                                  |

<br><br>

| Type Class                                                                | Signature                                                  | Function / Symbol    | Bounds             | Defining |
| ------------------------------------------------------------------------- | ---------------------------------------------------------- | -------------------- | ------------------ | :------: |
| [`Eq[A]`]({{ site.baseurl }}/api/cats/kernel/Eq.html)                     | `A => A => Boolean`                                        | `eqv`  / `===`       |                    |     ✓    |
|                                                                           | `A => A => Boolean`                                        | `neqv` / `=!=`       |                    |          |
|-------------------------------------------------------------------------- +----------------------------------------------------------- +--------------------- | ------------------ | -------- |
| [`PartialOrder[A]`]({{ site.baseurl }}/api/cats/kernel/PartialOrder.html) | `A => A => Double`                                         | `partialCompare`     |                    |     ✓    |
|                                                                           | `A => A => Option[Int]`                                    | `tryCompare`         |                    |          |
|                                                                           | `A => A => Boolean`                                        | `gt`    / `>`        |                    |          |
|                                                                           | `A => A => Boolean`                                        | `gteqv` / `>=`       |                    |          |
|                                                                           | `A => A => Boolean`                                        | `lt`    / `<`        |                    |          |
|                                                                           | `A => A => Boolean`                                        | `lteqv` / `<=`       |                    |          |
|---------------------------------------------------------------------------+----------------------------------------------------------- +--------------------- | ------------------ | -------- |
| [`Semigroup[A]`]({{ site.baseurl }}/api/cats/kernel/Semigroup.scala)      | `A =>  A  => A`                                            | `combine` / `|+|`    |                    |     ✓    |
|                                                                           | `A => Int => A`                                            | `combineN`           |                    |          |
|---------------------------------------------------------------------------+----------------------------------------------------------- +--------------------- | ------------------ | -------- |
| [`Monoid[A]`]({{ site.baseurl }}/api/cats/kernel/Monoid.scala)            | `A`                                                        | `empty`              |                    |     ✓    |
|---------------------------------------------------------------------------+----------------------------------------------------------- +--------------------- | ------------------ | -------- |
| [`Group[A]`]({{ site.baseurl }}/api/cats/kernel/Group.scala)              | `A => A`                                                   | `inverse`            |                    |     ✓    |
|                                                                           | `A => A => A`                                              | `remove` / `|-|`     |                    |          |
|---------------------------------------------------------------------------+----------------------------------------------------------- +--------------------- | ------------------ | -------- |
| [`Cartesian[F[_]]`]({{ site.baseurl }}/api/cats/Cartesian.html)           | `F[A] => F[B] => F[(A, B)]`                                | `product`            |                    |     ✓    |
|                                                                           | `F[A] => F[B] => ((A, B) => C) => F[C]`                    | `|@|`                |                    |          |
|                                                                           | `F[A] => F[B] => F[A]`                                     | `<*`                 |                    |          |
|                                                                           | `F[A] => F[B] => F[B]`                                     | `*>`                 |                    |          |
|---------------------------------------------------------------------------+----------------------------------------------------------- +--------------------- | ------------------ | -------- |
| [`Functor[F[_]]`]({{ site.baseurl }}/api/cats/Functor.html)               | `F[A] => (A => B) => F[B]`                                 | `map`                |                    |     ✓    |
|                                                                           | `F[A] => (A => B) => (B => A) => F[B]`                     | `imap`               |                    |          |
|---------------------------------------------------------------------------+----------------------------------------------------------- +--------------------- | ------------------ | -------- |
| [`Apply[F[_]]`]({{ site.baseurl }}/api/cats/Apply.html)                   | `F[A => B]      => F[A] => F[B]`                           | `ap`                 |                    |     ✓    |
|                                                                           | `F[(A, B) => Z] => F[A] => F[B]          => F[Z]`          | `ap2`                |                    |          |
|                                                                           | `F[A]           => F[B] => ((A, B) => Z) => F[Z]`          | `map2`               |                    |          |
|---------------------------------------------------------------------------+----------------------------------------------------------- +--------------------- | ------------------ | -------- |
| [`Applicative[F[_]]`]({{ site.baseurl }}/api/cats/Applicative.html)       | `A       => F[A]`                                          | `pure`               |                    |     ✓    |
|                                                                           | `Int     => F[A]        => F[List[A]]`                     | `relicateA`          |                    |          |
|                                                                           | `G[A]    => (A => F[B]) => F[G[B]]`                        | `traverse`           | `[G: Traverse]`    |     ✓    |
|                                                                           | `G[F[A]] => F[G[B]]                  `                     | `sequence`           | `[G: Traverse]`    |          |
|---------------------------------------------------------------------------+----------------------------------------------------------- +--------------------- | ------------------ | -------- |
| [`FlatMap[F[_]]`]({{ site.baseurl }}/api/cats/FlatMap.html)               | `F[A]       => (A => F[B])  => F[B]`                       | `flatMap`    / `>>=` |                    |     ✓    |
|                                                                           | `F[F[A]]    => F[A]`                                       | `flatten`            |                    |          |
|                                                                           | `F[A]       => F[B]         => F[B]`                       | `followedBy` / `>>`  |                    |          |
|                                                                           | `F[A]       => (A => F[B])  => F[(A, B)]`                  | `mproduct`           |                    |          |
|                                                                           | `F[Boolean] => (F[B], F[B]) => F[B]`                       | `ifM`                |                    |          |
|---------------------------------------------------------------------------+----------------------------------------------------------- +--------------------- | ------------------ | -------- |
| [`Monad[F[_]]`]({{ site.baseurl }}/api/cats/Monad.html)                   | `F[A] => (A => F[B]) => F[B]`                              | `flatMap`            |                    |     ✓    |
|---------------------------------------------------------------------------+----------------------------------------------------------- +--------------------- | ------------------ | -------- |
| [`MonadFilter[F[_]]`]({{ site.baseurl }}/api/cats/MonadFilter.html)       | `F[A] => (A => Option[B]) => F[B]`                         | `mapFilter`          |                    |     ✓    |
|---------------------------------------------------------------------------+----------------------------------------------------------- +--------------------- | ------------------ | -------- |
| [`MonadCombine[F[_]]`]({{ site.baseurl }}/api/cats/MonadCombine.html)     | `F[G[A]] => F[A]`                                          | `unite`              | `[G: Foldable]`    |     ✓    |
|                                                                           | `F[G[A]] => (F[A], F[B])`                                  | `separate`           | `[G: Bifoldable]`  |     ✓    |
|---------------------------------------------------------------------------+----------------------------------------------------------- +--------------------- | ------------------ | -------- |
| [`Traverse[F[_]]`]({{ site.baseurl }}/api/cats/Traverse.html)             | `F[A]    => (A => G[B])    => G[F[B]]`                     | `traverse`           | `[G: Applicative]` |     ✓    |
|                                                                           | `F[G[A]] => G[F[B]]                  `                     | `sequence`           | `[G: Applicative]` |          |
|                                                                           | `F[A]    => (A => G[F[B]]) => G[F[B]]`                     | `traverseM`          | `[G: Applicative, F: FlatMap]` |          |
|---------------------------------------------------------------------------+------------------------------------------------------------+--------------------- | ------------------ | -------- |
| [`Foldable[F[_]]`]({{ site.baseurl }}/api/cats/Foldable.html)             | `F[A] => B        => ((B, A) => B)       => B`             | `foldLeft`           |                    |     ✓    |
|                                                                           | `F[A] => Eval[B]  => ((A, Eval[B]) => B) => Eval[B]`       | `foldRight`          |                    |     ✓    |
|                                                                           | `F[A] => (A => B) => B`                                    | `foldMap`            | `[B: Monoid]`      |          |
|                                                                           | `F[A] => B        => ((B, A) => G[B])    => G[B]`          | `foldM`              | `[G: Monad]`       |          |
|---------------------------------------------------------------------------+------------------------------------------------------------+--------------------- | ------------------ | -------- |
| [`Reducible[F[_]]`]({{ site.baseurl }}/api/cats/Reducible.html)           | `F[A] => (A => B)    => ((B, A) => B)          => B`       | `reduceLeftTo`       |                    |     ✓    |
|                                                                           | `F[A] => (A => B) => ((A, Eval[B]) => Eval[B]) => Eval[B]` | `reduceRightTo`      |                    |     ✓    |
|                                                                           | `F[A] => (A => B)    => B`                                 | `reduceMap`          | `[B: Monoid]`      |     ✓    |
|                                                                           | `F[A] => (A => G[B]) => ((B, A) => G[B])       => G[B]`    | `reduceLeftM`        | `[G: FlatMap]`     |     ✓    |
|---------------------------------------------------------------------------+------------------------------------------------------------+--------------------- | ------------------ | -------- |
| [`CoflatMap[F[_]]`]({{ site.baseurl }}/api/cats/CoflatMap.html)           | `F[A] => (F[A] => B) => F[B]`                              | `coflatMap`          |                    |     ✓    |
|                                                                           | `F[A] => F[F[A]]`                                          | `coflatten`          |                    |     ✓    |
|---------------------------------------------------------------------------+------------------------------------------------------------+--------------------- | ------------------ | -------- |
| [`Comonad[F[_]]`]({{ site.baseurl }}/api/cats/Comonad.html)               | `F[A] => A`                                                | `extract`            |                    |     ✓    |
{: #type-class-table}
