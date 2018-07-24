snowball-stemmers-weka-package
==============================

Weka package for the snowball stemmers (http://snowball.tartarus.org/).

**OBSOLETE**

This package is now maintained by the Weka maintainer. The code is available
directly from the Weka subversion repository. Here is a direct link to the
package's location in that repo:

https://svn.cms.waikato.ac.nz/svn/weka/trunk/packages/external/snowball-stemmers/


Releases
--------

* [1.0.1](https://github.com/fracpete/snowball-stemmers-weka-package/releases/download/v1.0.1/snowball-stemmers-1.0.1.zip)
* [1.0.0](https://github.com/fracpete/snowball-stemmers-weka-package/releases/download/v1.0.0/snowball-stemmers-1.0.0.zip)



How to use packages
-------------------

For more information on how to install the package, see:

https://waikato.github.io/weka-wiki/packages/manager/


Maven
-----

Add the following dependency in your `pom.xml` to include the package.

The following dependency automatically pulls in Weka:

```xml
    <dependency>
      <groupId>com.github.fracpete</groupId>
      <artifactId>snowball-stemmers-weka-package</artifactId>
      <version>1.0.1</version>
    </dependency>
```

Use the following dependency to exclude the Weka dependencies:

```xml
    <dependency>
      <groupId>com.github.fracpete</groupId>
      <artifactId>snowball-stemmers-weka-package</artifactId>
      <version>1.0.1</version>
      <exclusions>
        <exclusion>
          <groupId>nz.ac.waikato.cms.weka</groupId>
          <artifactId>weka-dev</artifactId>
        </exclusion>
        <exclusion>
          <groupId>org.pentaho.pentaho-commons</groupId>
          <artifactId>pentaho-package-manager</artifactId>
        </exclusion>
      </exclusions>
    </dependency>
```

Usage
-----

* When using the stemmers independent of Weka:

  ```java
  import org.tartarus.snowball.SnowballStemmer;
  import org.tartarus.snowball.ext.porterStemmer;

  SnowballStemmer stemmer = new porterStemmer();
  stemmer.setCurrent("referred");
  stemmer.stem();
  System.out.println(stemmer.getCurrent());
  ```

* Using the stemmers as a Weka stemmer:

  ```java
  import weka.core.stemmers.SnowballStemmer;

  SnowballStemmer stemmer = new SnowballStemmer();
  stemmer.setStemmer("porter");
  System.out.println(stemmer.stem("referred"));
  ```

* Using the stemmers as part of the `StringToWordVector` filter:

  ```java
  import weka.filters.unsupervised.attribute.StringToWordVector;
  import weka.core.stemmers.SnowballStemmer;

  SnowballStemmer stemmer = new SnowballStemmer();
  stemmer.setStemmer("porter");
  StringToWordVector filter = new StringToWordVector();
  filter.setStemmer(stemmer);
  ```

