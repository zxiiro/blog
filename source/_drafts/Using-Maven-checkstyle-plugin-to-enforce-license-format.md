title: Using Maven checkstyle plugin to enforce license format
tags:
- maven
- opendaylight
---
On the OpenDaylight project one of the issues we've had to resolve lately is in regards to ensuring all projects have the appropriate EPL license header at the top of the file. We were able to use the maven-checkstyle-plugin's license checking support to automatically find projects that are missing headers as well as projects that have headers that do not conform to the style that is recommended by the project. Additionally we are able to use this to automatically prevent contributors from committing future code into the repo that are missing these headers.

## LICENSE.txt RegEx

The maven-checkstyle-plugin supports license checking via a RegEx parser that you can define by providing a LICENSE.txt with the RegEx rules you'd like to use. Here is an example of what is being used by OpenDaylight at time of this writing:

{% codeblock LICENSE.txt %}
^/[*]+$
^ \* Copyright \([cC]\) [0-9]{4}(, [0-9]{4})? .* All rights reserved.$
^ \*( )?$
^ \* This program and the accompanying materials are made available under the$
^ \* terms of the Eclipse Public License v1.0 which accompanies this distribution,$
^ \* and is available at http://www.eclipse.org/legal/epl-v10.html$
^ [*]+/$
{% endcodeblock %}

Let's walkthrough this line by line:

**Line 1, 7**
Checks for the Java starting comment at minimum "/\*" but supports also as many additional "\*"s as desired. Similarily on the last line we want to ensure that the closing comment ends with "\*/" with as many additional "\*"s as desired.

**Line 2**
Ensures that a Copyright line exists and is formatted correctly. This line can actually appear more than once as configured in the check-license.xml.

**Line 3**
Style ensuring that a blank line is left.

**Line 4-6**
Ensures that the EPL license header is intact and format agreed by OpenDaylight.

## check-license.xml

This file tells Maven how to use the LICENSE.txt file.

Setting up a custom execution

{% codeblock Custom License Execution lang:xml %}
            <execution>
              <id>check-license</id>
              <goals>
                <goal>check</goal>
              </goals>
              <phase>process-sources</phase>
            </execution>
{% endcodeblock %}

Configuration

{% codeblock Custom License Configuration lang:xml %}
              <configuration>
                <configLocation>check-license.xml</configLocation>
                <includeResources>false</includeResources>
                <includeTestResources>false</includeTestResources>
                <sourceDirectory>${project.build.sourceDirectory}</sourceDirectory>
                <excludes>
                  org/opendaylight/yang/gen/**,
                  **/config/yang/**,
                  **/protobuff/messages/**,
                  **/thrift/gen/*.java
                </excludes>
                <failsOnError>false</failsOnError>
                <consoleOutput>true</consoleOutput>
              </configuration>
{% endcodeblock %}

{% codeblock Full Code lang:xml %}
        <plugin>
          <artifactId>maven-checkstyle-plugin</artifactId>
          <version>${checkstyle.version}</version>
          <dependencies>
            <dependency>
              <groupId>org.opendaylight.odlparent</groupId>
              <artifactId>checkstyle</artifactId>
              <version>${odl.checkstyle.version}</version>
            </dependency>
          </dependencies>
          <configuration>
            <configLocation>odl_checks.xml</configLocation>
            <!-- <sourceDirectory> is needed so that checkstyle ignores the
                 generated sources directory -->
            <sourceDirectory>${project.build.sourceDirectory}</sourceDirectory>
            <excludes>
              org/opendaylight/yang/gen/**,
              **/config/yang/**,
              **/protobuff/messages/**,
              **/thrift/gen/*.java
            </excludes>
            <failsOnError>false</failsOnError>
            <consoleOutput>true</consoleOutput>
          </configuration>
          <executions>
            <execution>
              <id>check-license</id>
              <goals>
                <goal>check</goal>
              </goals>
              <phase>process-sources</phase>
              <configuration>
                <configLocation>check-license.xml</configLocation>
                <includeResources>false</includeResources>
                <includeTestResources>false</includeTestResources>
                <sourceDirectory>${project.build.sourceDirectory}</sourceDirectory>
                <excludes>
                  org/opendaylight/yang/gen/**,
                  **/config/yang/**,
                  **/protobuff/messages/**,
                  **/thrift/gen/*.java
                </excludes>
                <failsOnError>false</failsOnError>
                <consoleOutput>true</consoleOutput>
              </configuration>
            </execution>
            <execution>
              <goals>
                <goal>check</goal>
              </goals>
              <phase>process-sources</phase>
            </execution>
          </executions>
        </plugin>
{% endcodeblock %}
