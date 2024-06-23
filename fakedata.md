```java
{
  "id": "4",
  "payAssociateInfo": {
    "uniqueID": "111111111",
    "firstName": "John",
    "middleInitial": "A",
    "lastName": "Doe",
    "addrLine1": "Update Rd",
    "addrLine2": "2089 North Pebble Beach Drive",
    "addrLine3": "CHARLOTTETOWN, PRINCE EDWARD ISLAND",
    "zipCode": "75231",
    "payCategory": "Hourly",
    "ascStoreDetails": {
      "stateCode": "PE",
      "stateProvCode": "PE",
      "divNbr": "3",
      "storeName": "",
      "storeNumber": "CA-03162",
      "jobTitle": "General Associate"
    }
  },
  "payPeriodSummary": {
    "win": "2121212",
    "year": "2024",
    "payrollRunDate": "2024-04-07",
    "payEndDate": "2024-04-05",
    "seqRowCd": "1",
    "payrollCorpCd": "WS",
    "checkSeriesCd": "DU",
    "checkType": "D",
    "payToName": "John A Doe",
    "checkNbr": "44998409",
    "checkDate": "2023-03-30",
    "grossCheckAmt": "7264.18",
    "netCheckAmt": "1485.9"
  },
  "checkInfo": {
    "payPDBegDate": "2023-03-23",
    "payPDEndDate": "2024-04-05",
    "checkDate": "2024-04-11",
    "clearedDate": "2023-04-13",
    "voidDate": null,
    "checkNbr": "44983490",
    "checkType": "D",
    "checkAmt": "1485.9",
    "totalAmt": "1485.9",
    "payFrequency": "Bi-Weekly"
  },
  "checkAdviseSummary": [
    {
      "category": "pretax",
      "current": "133",
      "ytd": "446",
      "hours": null,
      "ytdhours": null
    },
    {
      "category": "taxes",
      "current": "123",
      "ytd": "446",
      "hours": null,
      "ytdhours": null
    },
    {
      "category": "earnings",
      "current": "123",
      "ytd": "456",
      "hours": null,
      "ytdhours": null
    },
    {
      "category": "netpay",
      "current": "123",
      "ytd": "456",
      "hours": null,
      "ytdhours": null
    },
    {
      "category": "hours",
      "current": "80",
      "ytd": "160",
      "hours": null,
      "ytdhours": null
    }
  ],
  "w4": [
    {
      "specialLetter": "0",
      "netClaimAmount": "0",
      "otherIncome": "0",
      "deductionAmt": "0",
      "dependentAmt": "0",
      "additionalTaxPCT": "0",
      "additionalTaxAmt": "0",
      "exemptionQty": "0",
      "twoJobs": "",
      "maritalStatus": "S",
      "taxTypeCd": "FEDERAL"
    },
    {
      "specialLetter": "0",
      "netClaimAmount": "0",
      "otherIncome": "0",
      "deductionAmt": "0",
      "dependentAmt": "0",
      "additionalTaxPCT": "0",
      "additionalTaxAmt": "0",
      "exemptionQty": "0",
      "twoJobs": "",
      "maritalStatus": "S",
      "taxTypeCd": "ONTARIO"
    }
  ],
  "earnings": [
    {
      "taxCd": "1000",
      "desc": "REGULAR EARNING",
      "hours": "58.87",
      "rate": "17.65",
      "currAmt": "3076.93",
      "ytdAmt": "21538.51"
    },
    {
      "taxCd": "05",
      "desc": "CO STK CONT",
      "hours": null,
      "rate": null,
      "currAmt": "11.25",
      "ytdAmt": "202.5"
    },
    {
      "taxCd": "81",
      "desc": "MGMT INCENTIVE",
      "hours": null,
      "rate": null,
      "currAmt": "6615.69",
      "ytdAmt": "6615.69"
    }
  ],
  "taxes": [
    {
      "desc": "EMPLOYEE TOTAL TAX",
      "currAmt": "345.56",
      "ytdAmt": "3816.53"
    },
    {
      "desc": "CPP EMPLOYEE CONTRIBUTION",
      "currAmt": "188.91",
      "ytdAmt": "1732.63"
    },
    {
      "desc": "EI EMPLOYEE PREMIUMS",
      "currAmt": "44.18",
      "ytdAmt": "405.21"
    }
  ],
  "deductions": [
    {
      "desc": "MAJOR MED",
      "currAmt": "33",
      "ytdAmt": "229.28",
      "category": "preTax"
    },
    {
      "desc": "LTD",
      "currAmt": "8.3",
      "ytdAmt": "58.09",
      "category": "preTax"
    },
    {
      "desc": "401K",
      "currAmt": "123.08",
      "ytdAmt": "1126.18",
      "category": "preTax"
    },
    {
      "desc": "DENTAL",
      "currAmt": "11.25",
      "ytdAmt": "202.5",
      "category": "preTax"
    }
  ],
  "depositDistribution": [
    {
      "acctNbr": "xxxxxxxx5337",
      "institutionName": "Canada Bank Institution",
      "type": "BANK ACCOUNT",
      "amt": "1000"
    }
  ]
}


<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.walmart</groupId>
    <artifactId>paystub-api-global</artifactId>
    <version>0.0.1-SNAPSHOT</version>

    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>2.7.11</version>
        <relativePath/>
    </parent>

    <properties>
        <java.version>17</java.version>
    </properties>

    <dependencyManagement>
        <dependencies>
            <dependency>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-dependencies</artifactId>
                <version>2.7.11</version>
                <type>pom</type>
                <scope>import</scope>
            </dependency>
            
            <!-- Manage versions for the conflicting dependencies -->
            <dependency>
                <groupId>net.java.dev.jna</groupId>
                <artifactId>jna</artifactId>
                <version>5.13.0</version>
            </dependency>
            <dependency>
                <groupId>net.java.dev.jna</groupId>
                <artifactId>jna-platform</artifactId>
                <version>5.6.0</version>
            </dependency>
            <dependency>
                <groupId>com.microsoft.azure</groupId>
                <artifactId>msal4j</artifactId>
                <version>1.14.0</version>
            </dependency>
            <dependency>
                <groupId>com.nimbusds</groupId>
                <artifactId>nimbus-jose-jwt</artifactId>
                <version>9.22</version>
            </dependency>
            <dependency>
                <groupId>com.walmart.platform.data</groupId>
                <artifactId>strati-af-ccm-client-spring</artifactId>
                <version>109.4.2</version>
            </dependency>
            <dependency>
                <groupId>com.walmart.platform.data</groupId>
                <artifactId>strati-af-configuration-api</artifactId>
                <version>2.2.6</version>
            </dependency>
        </dependencies>
    </dependencyManagement>

    <dependencies>
        <!-- Spring Boot Dependencies -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>
        
        <!-- Example of excluding a conflicting transitive dependency -->
        <dependency>
            <groupId>com.example</groupId>
            <artifactId>example-dependency</artifactId>
            <exclusions>
                <exclusion>
                    <groupId>net.java.dev.jna</groupId>
                    <artifactId>jna</artifactId>
                </exclusion>
                <exclusion>
                    <groupId>net.java.dev.jna</groupId>
                    <artifactId>jna-platform</artifactId>
                </exclusion>
            </exclusions>
        </dependency>

        <!-- Adding the dependencies directly -->
        <dependency>
            <groupId>net.java.dev.jna</groupId>
            <artifactId>jna</artifactId>
            <version>5.13.0</version>
        </dependency>
        <dependency>
            <groupId>net.java.dev.jna</groupId>
            <artifactId>jna-platform</artifactId>
            <version>5.6.0</version>
        </dependency>
        <dependency>
            <groupId>com.microsoft.azure</groupId>
            <artifactId>msal4j</artifactId>
            <version>1.14.0</version>
        </dependency>
        <dependency>
            <groupId>com.nimbusds</groupId>
            <artifactId>nimbus-jose-jwt</artifactId>
            <version>9.22</version>
        </dependency>
        <dependency>
            <groupId>com.walmart.platform.data</groupId>
            <artifactId>strati-af-ccm-client-spring</artifactId>
            <version>109.4.2</version>
        </dependency>
        <dependency>
            <groupId>com.walmart.platform.data</groupId>
            <artifactId>strati-af-configuration-api</artifactId>
            <version>2.2.6</version>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>${java.version}</source>
                    <target>${java.version}</target>
                </configuration>
            </plugin>
            <plugin>
                <groupId>org.jacoco</groupId>
                <artifactId>jacoco-maven-plugin</artifactId>
                <version>0.8.8</version>
                <executions>
                    <execution>
                        <goals>
                            <goal>prepare-agent</goal>
                        </goals>
                    </execution>
                    <execution>
                        <id>report</id>
                        <goals>
                            <goal>report</goal>
                        </goals>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>
</project>


```
