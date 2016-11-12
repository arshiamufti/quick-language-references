### Json

* A [useful list](http://manuel.bernhardt.io/2015/11/06/a-quick-tour-of-json-libraries-in-scala/) of the libraries out there.
* I like [play-json](https://www.playframework.com/documentation/2.4.x/ScalaJson)

### Http

* [scalaj-http](https://github.com/scalaj/scalaj-http) for making HTTP requests and handling responses.

### Working With Databases

* A [list](http://manuel.bernhardt.io/2014/02/04/a-quick-tour-of-relational-database-access-with-scala/) of libraries to use for relational database access with Scala
* [Slick](https://github.com/slick/slick)
  - I like it because it uses functional-relational mapping, as opposed to ORMs, but its documentation needs work, and there's random things that you'd expect support for, but don't have. I rememeber not being able to upsert on a table with with a compound primary key [throws a syntax error](https://github.com/slick/slick/issues/966)
  - [Official doc](http://slick.lightbend.com/docs/) and a [decent example](https://github.com/slick/slick-codegen-example) (but it uses fancy scala, booo)
  - http://arnaudt.github.io/2015/03/31/slick-codegen.html
  - [How to configure PostgreSQL](http://queirozf.com/entries/scala-slick-simple-example-on-connecting-to-a-postgresql-database) for Slick (`simple` is deprecated, use `api` instead)
  - Slick-pg: https://github.com/tminglei/slick-pg (enum support)
  - Transactions with slick and psql: http://blog.scalac.io/2015/07/09/slick-3-overview.html
  
### Scala Akka (for Actor-based concurrency)

* Best practices: http://arnaudt.github.io/2015/03/25/scala-sites.html
* Typesafe Activator: http://www.typesafe.com/activator/template/hello-akka
* This article on a gentler introduction (more high level): http://danielwestheide.com/blog/2013/02/27/the-neophytes-guide-to-scala-part-14-the-actor-approach-to-concurrency.html

