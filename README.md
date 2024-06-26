# Kotlin + Gradle (Kotlin DSL) + AWS CDK + AWS Lambda (Kotlin) Template

Check the Medium [article](https://medium.com/@goradux/how-to-serverless-kotlin-gradle-aws-cdk-aws-lambda-024b2f1f7f06) describing the step-by-step setup.

## TL;DR

This is a Kotlin-based template repository that constists of two subprojects:

1. Infrastructure. CDK infrastructure code is written in Kotlin and uses AWS Java CDK library.
2. Lambda. Lambda source code written in Kotlin and compiled into Java-compatible uber-jars using shadow Gradle plugin.

## Requirements

You should have this software preinstalled:

* Kotlin (`brew install kotlin`);
* Gradle (`brew install gradle`);
* Java (`brew install openjdk`);
* Node (`brew install nvm` & `nvm install 20`);
* AWS CDK CLI Toolkit (`npm install -g aws-cdk`);
* AWS SAM CLI (`brew install aws-sam-cli`);

## How to run

Build everything:

```bash
./gradlew build
```

Deploy stack:

```bash
./gradlew lambda:shadow # build the lambda
cd infrastructure
cdk deploy --context stage=dev # deploy the code
```

Run Lambda locally (using AWS SAM CLI):

```bash
./gradlew lambda:shadow # build the lambda
cd infrastructure
cdk synth --context stage=dev
sam local invoke Function --no-event -t cdk.out/my-sample-stack.template.json
```
