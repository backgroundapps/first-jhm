## Steps used for creating this project:

1. run » mvn archetype:generate -DinteractiveMode=false -DarchetypeGroupId=org.openjdk.jmh -DarchetypeArtifactId=jmh-java-benchmark-archetype -DgroupId=org.sample -DartifactId=first-jhm -Dversion=1.0
2. update the benchmark class with the content bellow
package org.sample;
import org.openjdk.jmh.annotations.*;
import java.util.concurrent.TimeUnit;

public class MyBenchmark {
    @Benchmark@BenchmarkMode(Mode.AverageTime) @OutputTimeUnit(TimeUnit.MICROSECONDS)
    public void testMethod() {
        doMagic();
    }
    public static void doMagic() {
        try {
            Thread.sleep(2000);
        } catch (InterruptedException ignored) {
        }
    }
}

3. run » java -jar target/benchmark.jar -f 1 -wi 2 -i 5

Legend:
number of forks = 1
warm up iterations = 2
benchmark iterations = 5

