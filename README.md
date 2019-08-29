# java_csv
Java 操作CSV 文件 <br>
https://www.jianshu.com/p/c29280c1719a<br>
<br>
Maven pom dependency
    <dependency>
      <groupId>org.apache.commons</groupId>
      <artifactId>commons-csv</artifactId>
      <version>1.3</version>
    </dependency>

读取CSV 文件
public void printCsvFile(String fileName) {
  Reader fileReader = new FileReader(fileName);
  Iterable<CSVRecord> records = CSVFormat.RFC4180.withFirstRecordAsHeader().parse(fileReader);
  for (CSVRecord record : records) {
    System.out.println(record.get("instanceId") + record.get("regionId") + record.get("zoneId"))
  }
}

写入CSV文件
public void writeCsvFile(String fileName) {
  Appendable fileWriter = new FileWriter(fileName);
  CSVPrinter printer = CSVFormat.RFC4180.withHeader("instanceId", "regionId", "zoneId").print(fileWriter)
  printer.printRecord("testInstanceId", "testRegionId", "testZoneId");
  printer.close();
}

作者：DongGuangqing
链接：https://www.jianshu.com/p/c29280c1719a
来源：简书
简书著作权归作者所有，任何形式的转载都请联系作者获得授权并注明出处。
