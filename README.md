# Minecraft-JVM-Arguments-Optimization

Minecraft JVM Arguments Optimization for in-game FPS for a medium-large size modpack.

Note: I am NOT a Java professional. All the work written here is based on reading official documentations.


<hr>

## Changing JVM Arguments

Here's how to change your java arguments in the official Minecraft Launcher. 
1. Open the Minecraft Launcher, click on 'Installations', click on your profile and click on 'More Options'.
2. Under 'More Options', you will find 'JVM arguments'.
3. You can change or add your JVM arguments here.


<hr>

## HotSpot JVM Arguments

- ## G1 Garbage Collection

  The G1 Garbage Collection (G1GC) is the default garbage collection policy for newer versions of Minecraft. It's an adaptive garbage collector that uses concurrent and parallel phases to achieve its target pause time and to maintain good throughput.

   - #### JVM Arguments for HotSpot with G1 Garbage Collection for computers with 12GB+ of RAM memory:
      ``
      -Xmx8G -Xms8G -XX:+UnlockExperimentalVMOptions -XX:+AlwaysPreTouch -XX:+UseG1GC -XX:G1NewSizePercent=25 -XX:G1ReservePercent=50 -XX:G1HeapWastePercent=25 -XX:MaxGCPauseMillis=50 -XX:G1HeapRegionSize=32M
      ``

  - #### JVM Arguments for HotSpot with G1 Garbage Collection for computers with 8GB of RAM memory:
      ``
      -Xmx5G -Xms5G -XX:+UnlockExperimentalVMOptions -XX:+AlwaysPreTouch -XX:+UseG1GC -XX:G1NewSizePercent=25 -XX:G1ReservePercent=20 -XX:G1HeapWastePercent=25 -XX:MaxGCPauseMillis=50 -XX:G1HeapRegionSize=32M
      ``

  - #### JVM Arguments for HotSpot with G1 Garbage Collection for computers with 6GB of RAM memory:
      ``
      -Xmx4G -Xms4G -XX:+UnlockExperimentalVMOptions -XX:+AlwaysPreTouch -XX:+UseG1GC -XX:G1NewSizePercent=15 -XX:G1ReservePercent=15 -XX:G1HeapWastePercent=10 -XX:MaxGCPauseMillis=55 -XX:G1HeapRegionSize=32M
      ``

- ## Shenandoah Garbage Collection

  Lags the client. Not recommended at the moment. Need tests.

   - #### JVM Arguments for HotSpot with Shenandoah Garbage Collection for computers with 12GB+ of RAM memory:
      ``
      -Xmx8G -Xms8G -XX:+UnlockExperimentalVMOptions -XX:+AlwaysPreTouch -XX:+UseShenandoahGC -XX:ShenandoahAllocSpikeFactor=25 -XX:ShenandoahGarbageThreshold=25 -XX:ShenandoahPacingMaxDelay=50
      ``


<hr>

## OpenJ9 JVM Arguments:

  Lags the client. Not recommended at the moment. Need tests.
  
  - #### JVM Arguments for OpenJ9 with gencon Garbage Collection for computers with 12GB+ of RAM memory:
    ``
    -Xmx8G -Xms8G -Xgcpolicy:gencon -Xmnx4G - Xmns4G
    ``


<hr>

## Sources

Sources and documentations of interest.

<br> [Oracle Docs](https://docs.oracle.com/en/)
<br> [OpenJDK Wiki](https://wiki.openjdk.java.net/)
<br> [Memory Management in the Java HotSpot Virtual Machine](https://www.oracle.com/technetwork/java/javase/memorymanagement-whitepaper-150215.pdf)
<br> [Java arguments optimization](https://github.com/NordicGamerFE/usefulmods/blob/main/JavaArgumentsOptimization.md)
<br> [HotSpot G1GC](https://wiki.openjdk.java.net/display/HotSpot/G1GC+Feedback)
<br> [G1GC Parameters Tuning](https://www.oracle.com/technical-resources/articles/java/g1gc.html)
<br> [Shenandoah Garbage Collector](https://wiki.openjdk.java.net/display/shenandoah/Main)
<br> [Eclipse OpenJ9 docs](https://www.eclipse.org/openj9/docs/)
