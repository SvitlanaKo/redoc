# redoc
Generate markdown doc from Gherkin *.feature files

## Why

The problem with test documentation is that it is either **non-existing** or **outdated**.

We can solve the problem by:

1. Adopting [BDD](https://en.wikipedia.org/wiki/Behavior-driven_development) approach and [Gherkin](https://docs.cucumber.io/gherkin/) syntax for test scenario description.
2. Using [Markdown](https://en.wikipedia.org/wiki/Markdown) for documentation. 
3. Generating Markdown documents from Gherkin description.

## Advantages

1. Gherkin syntax is simple and human readable
2. Markdown format is easy to publish
3. *.feature files become single source of truth for both documentation and test automation.
4. Can be easily integrated into any CI/CD process.

## Prerequisites
Kotlin compiler installed (e.g via [sdkman](https://sdkman.io/))

## How to use

* Put your Gherkin `*.feature` files under `./features` folder

* Generate `testplan-ui.md`from `*.feature`files by running:

  ```
  $ kotlinc redoc.kt -include-runtime -d redoc.jar && java -jar redoc.jar ./features ./doc/testplan-ui.md 
  ```

* Make sure Features section of `./doc/testplan-ui.md`is updated

* Commit and push changes to your git repository

* Check updated [Features](https://github.com/ludenus/redoc/blob/master/doc/testplan-ui.md#features) section on testplan-ui.md Github page.

* You should be able to navigate exact lines of `*.feature` files by clicking **Scenarios** on [testplan-ui.md](https://github.com/ludenus/redoc/blob/master/doc/testplan-ui.md#features) page.



## Known issues

Markdown format does not support comments, so in order to hide autogen markers [this workaround](https://stackoverflow.com/a/20885980/1073584) is used: 

```
[//]: # (AUTOGENERATED BLOCK BEGIN)
[//]: # (AUTOGENERATED BLOCK END)
```

However different tools treat such block in a different way. In particular https://typora.io/ adds undesired quotes to this block. There is no reliable way to prevent such behaviour, so beware.
