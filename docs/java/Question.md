## Question

压缩字符串存数据库

压缩成Bytes，然后Base64编码

https://stackoverflow.com/questions/48837883/compress-and-store-a-string-in-a-varchar-field-in-mysql

https://stackoverflow.com/questions/3649485/how-to-compress-a-string-in-java

```java
String str = "10000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000001111111000011111111111111111111111110000000000000000000000000000000000000000000000000000000000000";
ByteBuffer bufferStringInput = StringUtils.getByteBufferUtf8(str);

ByteArrayOutputStream out = new ByteArrayOutputStream(1024);
BufferedOutputStream bufferedOutputStream = new BufferedOutputStream(out);
CompressorOutputStream compressorOutputStream = new CompressorStreamFactory().createCompressorOutputStream(CompressorStreamFactory.GZIP, bufferedOutputStream);

compressorOutputStream.write(bufferStringInput.array());

compressorOutputStream.close();
bufferedOutputStream.close();

System.out.println(StringUtils.newStringUtf8(Base64.getEncoder().encode(out.toByteArray())));
out.close();
```

