# Release Nodes #

## 2.2.0 (2017-05-08) ##

* Switch to the updated MSBuild .NET Core build system. Pull request by Adeel
  Mujahid. GitHub #35.
* Move tests from  NUnit to xUnit.net. GitHub #35.

## 2.1.3 (2016-11-22) ##

* Update for .NET Core 1.1.

## 2.1.2 (2016-08-08) ##

* Re-build of 2.1.1 to fix signing issue. No code changes.

## 2.1.1 (2016-08-01) ##

* First non-beta release with .NET Core support.
* The tests now use the .NET Core NUnit runner.

## 2.1.1-beta1 (2016-06-01) ##

* Re-release of `2.1.0-beta4` to skip bad `2.1.0` release on NuGet.

## 2.1.0-beta4 (2016-06-01) ##

* Update for .NET Core RC2. Pull request by Adeel Mujahid. GitHub #28.

## 2.1.0-beta3 (2016-05-12) ##

* The assemblies are now signed again.

## 2.1.0-beta2 (2016-05-10) ##

* Remove unnecessary Newtonsoft.Json dependency.

## 2.1.0-beta1 (2016-05-10) ##

* .NET Core support. Switched to `dotnet/cli` for building. Pull request by
  Adeel Mujahid. GitHub #26 & #27.

## 2.0.0 (2016-04-15) ##

* No changes since 2.0.0-beta3.

## 2.0.0-beta3 (2016-03-24) ##

* The Reader class now has an overloaded method that takes an integer out
  parameter. This parameter is set the the network prefix length for the
  record containing the IP address in the database. Pull request by Ed Dorsey.
  GitHub #22 & #23.

## 2.0.0-beta2 (2016-01-29) ##

* Minor refactoring. No substantial changes since beta1.

## 2.0.0-beta1 (2016-01-18) ##

* Significant API changes. The `Find` method now takes a type parameter
  specifying the type to deserialize to. Note that `JToken` is _not_ supported
  for this. You can either deserialize to an arbitrary collection or to
  model classes that use the `MaxMind.Db.Constructor` and
  `MaxMind.Db.Parameter` attributes to identify the constructors and
  parameters to deserialize to.
* The API now significantly faster.

## 1.2.0 (2015-09-23) ##

* Production release. No changes.

## 1.2.0-beta1 (2015-09-08) ##

* The assembly now has a strong name.
* An internal use of `JTokenReader` is now disposed of after use.
* A null stream passed to the `Reader(Stream)` constructor will now throw an
  `ArgumentNullException`.

## 1.1.0 (2015-07-21) ##

* Minor code cleanup.

## 1.1.0-beta1 (2015-06-30) ##

* A `IOException: Not enough storage is available to process this command`
  when using the memory-mapped mode with 32-bit builds or many threads was
  fixed. Closes GH #5.
* Use of streams was replaced with direct access for both the memory-mapped
  file mode and the memory mode. This should increase performance in most
  cases.
* When using memory-mapped mode, the file is now opened with
  `FileShare.Delete`, allowing other processes to delete or replace the
  database when it is in use. The reader object will continue using the old
  database.
* The Json.NET dependency was updated to 7.0.1.

## 1.0.1 (2015-05-19) ##

* Improved the exception thrown when the constructor for `Reader` is called
  with an empty stream.
* Updated Newtonsoft.Json dependency to 6.0.8.
* Minor code cleanup.

## 1.0.0 (2014-09-29) ##

* First production release.

## 0.3.0 (2014-09-24) ##

* Added public `Metadata` property on `Reader`.

## 0.2.3 (2014-04-09) ##

* The database is now loadable from a `Stream`.

## 0.2.2 (2013-12-24) ##

* Fixed a bug that occurred when using the memory-mode in a multi-threaded
  application. When using a single `Reader` from multiple threads in memory-
  mode, the internal state of the object could become corrupt if you replaced
  the MaxMind database file on disk with another database file.

## 0.2.1 (2013-11-15) ##

* Fixed bug that caused an exception to be thrown when two threads created a
  `MaxMind.Db.Reader` object at the same time. This was fixed using a
  synchronization lock around the code that opens/creates the memory map. We
  recommend that you share a `Reader` object across threads rather than
  create one for each thread or lookup.

## 0.2.0 (2013-10-25) ##

* Changed namespace from `MaxMind.DB` to `MaxMind.Db` to conform with
  Microsoft's recommendations.
* Replaced custom `BigInteger` implementation with
  `System.Numerics.BigInteger`.
* Made `Metadata` an internal property on `Reader`.

## 0.1.0 (2013-10-22) ##

* Initial release
