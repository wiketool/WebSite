Lombok（Jdk9+）需要使用

```xml
<annotationProcessorPaths>
   <path>
      <groupId>org.projectlombok</groupId>
      <artifactId>lombok</artifactId>
      <version>${lombok.version}</version>
   </path>
</annotationProcessorPaths>
```



Lombok 1.18.16+后和MapStruct搭配使用需要配置如下

```xml
<annotationProcessorPaths>
   <path>
      <groupId>org.projectlombok</groupId>
      <artifactId>lombok</artifactId>
      <version>${lombok.version}</version>
   </path>
   <path>
      <groupId>org.mapstruct</groupId>
      <artifactId>mapstruct-processor</artifactId>
      <version>${org.mapstruct.version}</version>
   </path>
   <!-- additional annotation processor required as of Lombok 1.18.16 -->
   <path>
      <groupId>org.projectlombok</groupId>
      <artifactId>lombok-mapstruct-binding</artifactId>
      <version>0.1.0</version>
   </path>
</annotationProcessorPaths>
```
