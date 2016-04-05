# Json Parse [![Build Status](https://travis-ci.org/mitchhentges/json-parse.svg?branch=master)](https://travis-ci.org/mitchhentges/json-parse)

A tool to quickly parse JSON into Java maps and lists. Usually faster than FasterXML's Jackson with an extremely
small memory footprint.

_Lower is better:_
![](resources/comparison-nocache.png)
![](resources/comparison-cache.png)

## Usage

```
String mapString = "{\"fast\":true, \"super-neat\":true}";
String listString = "[1, 2, false]";

JsonParse parse = new JsonParse();
Map<String, Object> map = parse.map(mapString);
List<Object> list = parse.list(listString);
```

## Getting the dependency

**Maven**
```
<dependency>
    <groupId>ca.fuzzlesoft</groupId>
    <artifactId>json-parse</artifactId>
    <version>1.0.3</version>
</dependency>
```

**Gradle**
```
compile 'ca.fuzzlesoft:json-parse:1.0.3'
```

## Features

* Convert a JSON string to a Java `List<Object>`
* Convert a JSON string to a Java `Map<String, Object>`
* Thread safe
* Throw exceptions with helpful messages with trace to error, e.g. 'a.b.c: "fasle" is an invalid value'

## FAQ

* Can this convert from JSON directly to `SomeObject`?

Unfortunately not. JSON doesn't have any type information, so explicit knowledge is required before JSON can be
converted. This is the job of a "binding framework"

* Why do my JSON traces show "[]" for array elements, rather than their index?

Since efficiency is a primary goal of this project, array indices could not be added to JSON traces. It would
cost some performance, and that's not worth it ;)

* Why is the code squashed so much?

I wanted to minimize the number of function calls. Though the cost is minimal, it will still affect performance
on the large scale. Besides, my goal is for this to be a "finish and forget" project, where the speed benefits
add up over time, while the maintenance cost is nonexistent because the code "just works". We'll see how naive this
is over time ;)

To confirm that I'm not just a terrible developer, see my infrastructure contributions to the
[Binder app](https://github.com/binder-app/android)

## License
[MIT License (Expat)](http://www.opensource.org/licenses/mit-license.php)
