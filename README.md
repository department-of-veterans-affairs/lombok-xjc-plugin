# lombok-xjc-plugin

XJC plugin to add Lombok POJO annotations to generated classes.

The following annotations are added:

```
@Builder
@ToString
@EqualsAndHashCode
@NoArgsConstructor
@AllArgsConstructor(access = AccessLevel.PRIVATE)
```

Example usage:

```
<build>
  <plugins>
    <plugin>
      <groupId>org.codehaus.mojo</groupId>
      <artifactId>jaxws-maven-plugin</artifactId>
      <version>${jaxws-maven-plugin.version}</version>
      <executions>
        <execution>
          <goals>
            <goal>wsimport</goal>
          </goals>
          <configuration>
            <wsdlDirectory>src/main/wsdl</wsdlDirectory>
            <wsdlFiles>
              <wsdlFile>foo.wsdl</wsdlFile>
            </wsdlFiles>
            <keep>true</keep>
            <sourceDestDir>src/main/java</sourceDestDir>
            <args>
              <arg>-B-Xlombok</arg>
            </args>
            <vmArgs>
              <vmArg>-Djavax.xml.accessExternalSchema=all</vmArg>
            </vmArgs>
          </configuration>
        </execution>
      </executions>
      <dependencies>
        <dependency>
          <groupId>gov.va.xjc</groupId>
          <artifactId>lombok-xjc-plugin</artifactId>
          <version>${lombok-xjc-plugin.version}</version>
        </dependency>
      </dependencies>
    </plugin>
  </plugins>
</build>
```
