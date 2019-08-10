## Introduction

This project should help migrating from Java 8 and earlier to Java 9/10/11/12/13/… and their modular structure. It duplicates other open source projects but provides a `module-info.java`/`module-info.class`. With this modularisation they can be used by `jlink` and other new tools.

This project heavily uses the [ModiTect Maven Plugin](https://github.com/moditect/moditect), thanks to its developers!

I hope this project gets redundant soon and most projects supply a module-info by themselves.

## Supplied artifacts
Currently the following artifacts are wrapped and published as their own Maven module.

| original `groupId` | original `artifactId` | original `version` | new `groupId` | new `artifactId` | new `version` | Notes |
|--------------------|-----------------------|--------------------|---------------|------------------|---------------|-------|
| org.apache.commons | commons-compress | ¹ | io.github.1tchy.java9modular.org.apache.commons | commons-compress | ![Maven Central](https://img.shields.io/maven-central/v/io.github.1tchy.java9modular.org.apache.commons/commons-compress?label=Latest%20version) | Also comes with the `org.tukaani` artifact to support xz-compression. |

¹ The version of the original artifact is equal to the version of the new artifact without the last part (e.g. new: `1.18.1` was originally `1.18`).

### Example
```
<dependency>
    <groupId>org.apache.commons</groupId>
    <artifactId>commons-compress</artifactId>
    <version>a.b.c</version>
</dependency>
```
The above is basically equal to the following, but it is modularized - so it contains a module info:
```
<dependency>
    <groupId>io.github.1tchy.java9modular.org.apache.commons</groupId>
    <artifactId>commons-compress</artifactId>
    <version>a.b.c.d</version>
</dependency>
```
It contains (almost) all the same classes plus a (generated) module-info exporting all packages.

## Getting more artifacts
I would like to supply more artifacts, but I guess I will not have time for it. However I would be happy to accept some pull requests! Please feel free to send me one:

1. Checkout project
1. Duplicate an existing Maven sub-module
1. Adapt it to generate your artifact with a module-info
1. Test it (`mvn install` should install your new Jar to your local repository which you then can use in your other projects)
1. Update this Readme.md
1. Send a pull request containing the following statement to dedicate your contributions to the public domain: `I dedicate any and all copyright interest in this software to the public domain. I make this dedication for the benefit of the public at large and to the detriment of my heirs and successors. I intend this dedication to be an overt act of relinquishment in perpetuity of all present and future rights to this software under copyright law.`

## Getting updates for artifacts
If I find time I might update the artifacts. If you want faster updates, feel free to send me a pull request:

1. Checkout project
1. Update the version of the original artifact
1. Reset the version of the new artifact (`<new-version-of-the-original-artifact>`+`.0-SNAPSHOT`)
1. Test it (`mvn install` should install your new Jar to your local repository which you then can use in your other projects)
1. Send a pull request

## License
### For the generated artifacts
The generated artifacts are published under the same license as the corresponding original artifact.

### For this project
> This is free and unencumbered software released into the public domain.
>
> Anyone is free to copy, modify, publish, use, compile, sell, or distribute this software, either in source code form or as a compiled binary, for any purpose, commercial or non-commercial, and by any means.
>
> In jurisdictions that recognize copyright laws, the author or authors of this software dedicate any and all copyright interest in the software to the public domain. We make this dedication for the benefit of the public at large and to the detriment of our heirs and successors. We intend this dedication to be an overt act of relinquishment in perpetuity of all present and future rights to this software under copyright law.
>
> THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
>
> For more information, please refer to <http://unlicense.org/>
