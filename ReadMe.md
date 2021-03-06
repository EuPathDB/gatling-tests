
### Experimental Gatling tests

Download, untar Gatling - [http://gatling.io/download](http://gatling.io/download/)

Add to `$PATH`

    export PATH=$PATH:~/gatling-charts-highcharts-bundle-2.1.4/bin

Acquire tests

    git clone git@github.com:EuPathDB/gatling-tests

    cd gatling-tests
    
Run, with interactive menu choice,

    bin/grun --host w1.toxodb.org

or, for single test class,

    bin/grun -s wdk.StrategyMix --host w1.toxodb.org

----

### Authentication

Development sites require authentication. Use the `auth_tkt` cookie value from 
a web browser that has authenticated to the site under test and supply the value
with the `--authtoken` option.

    bin/grun -s wdk.StrategyMix --host mheiges.trichdb.org --authtoken jjBhMDzUNAZjMQzyNzRhNWEY4WU0ODgOjTk5NGVxZG1MNGI3MzlhZGWwaARiIFFawWRiITE0MjEyOTM5OTg6
    
----

### Logging

The conf/logback.xml is customized to allow changes to log levels by setting
Java system properties on the commandline.

#### Log ALL HTTP request and responses to console.

        JAVA_OPTS="-DhttpLogging=TRACE" bin/grun

#### Log  ONLY FAILED HTTP request and responses to console.

        JAVA_OPTS="-DhttpLogging=DEBUG" bin/grun

#### Set log level for Gatling root appender.

        JAVA_OPTS="-DrootLogging=DEBUG" bin/grun

#### Combining log levels

        JAVA_OPTS="-DrootLogging=TRACE -DhttpLogging=TRACE" bin/grun -s wdk.StrategyMix 

See
[LOGBack FAQ](http://logback.qos.ch/faq.html#overrideFromCL) for more 
information.

----

### wdk.StrategyMix

Runs a mix of strategies.

To select which product to use, set the `product` variable in `StrategyMix.scala` and each scenario files, 
e.g. `GeneTextSearchScenario`. (hackish, I don't yet know how to pass parameters
into a Scala object.)


