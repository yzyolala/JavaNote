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


{
  "id": "3c2fec05-b86e-455f-9d7d-c70c1804ea9e",
  "payAssociateInfo": {
    "userID": 473391472,
    "firstName": "DANIEL",
    "middleInitial": null,
    "lastName": "BEYETTE",
    "nameSuffix": null,
    "addrLine1": "302-94 SIDNEY ST",
    "addrLine2": null,
    "addrLine3": null,
    "city": "BELLEVILLE",
    "stateCode": "ON",
    "stateProvCode": null,
    "zipCode": "K8P 3Z1",
    "payCategory": "Hourly",
    "ascStoreDetails": {
      "divNbr": "C2920001",
      "storeName1": "WAL-MART CANADA, CORP.",
      "storeName2": null,
      "storeNbr": null,
      "addrLine1": "1940 ARGENTIA ROAD",
      "addrLine2": null,
      "city": "MISSISSAUGA",
      "stateCode": "ON",
      "stateProvCode": null,
      "zipCode": null
    },
    "jobTitle": "(CAN) STOCK UNLOADER ASSOCIATE"
  },
  "payPeriodSummary": {
    "win": 224823227,
    "year": null,
    "payrollRunDate": [
      2023,
      6,
      28
    ],
    "payPDEndDate": [
      2023,
      6,
      28
    ],
    "seqRowCd": null,
    "payrollCorpCd": null,
    "checkSeriesCd": null,
    "checkType": null,
    "payToName": null,
    "checkNbr": null,
    "checkDate": [
      2023,
      6,
      29
    ],
    "clearedDate": null,
    "voidDate": null,
    "checkNbr": null,
    "checkType": "Correction",
    "checkAmt": null,
    "totalAmt": null,
    "payFrequency": "Bi-Weekly"
  },
  "checkInfo": {
    "win": 224823227,
    "year": null,
    "payrollRunDate": [
      2023,
      6,
      28
    ],
    "payPDBegDate": [
      2023,
      6,
      28
    ],
    "payPDEndDate": [
      2023,
      6,
      28
    ],
    "checkDate": [
      2023,
      6,
      29
    ],
    "clearedDate": null,
    "voidDate": null,
    "checkNbr": null,
    "checkType": "Correction",
    "checkAmt": null,
    "totalAmt": null,
    "payFrequency": "Bi-Weekly"
  },
  "checkAdviseSummary": [
    {
      "category": "earnings",
      "currAmt": 230.3,
      "ytdAmt": 1159.89
    },
    {
      "category": "taxes",
      "currAmt": 14.28,
      "ytdAmt": 56.8
    },
    {
      "category": "post-tax",
      "currAmt": 0,
      "ytdAmt": 0
    },
    {
      "category": "pre-tax",
      "currAmt": 0,
      "ytdAmt": 0
    },
    {
      "category": "gross-pay",
      "currAmt": 230.3,
      "ytdAmt": 1159.89
    },
    {
      "category": "federal-taxable-wages",
      "currAmt": 0,
      "ytdAmt": 0
    },
    {
      "category": "net-pay",
      "currAmt": 216.02,
      "ytdAmt": 1103.09
    },
    {
      "category": "hours",
      "currAmt": 0,
      "ytdAmt": 67.01
    }
  ],
  "W4": [
    {
      "specialLetter": 0,
      "netClaimAmount": 15000,
      "otherIncome": null,
      "deductionAmt": null,
      "dependentAmt": null,
      "additionalTaxPCT": 0,
      "additionalTaxAmt": null,
      "exemptionQty": null,
      "twoJobs": null,
      "maritalStatus": null,
      "taxTypeCd": "FEDERAL"
    },
    {
      "specialLetter": 0,
      "netClaimAmount": 11865,
      "otherIncome": null,
      "deductionAmt": null,
      "dependentAmt": null,
      "additionalTaxPCT": 0,
      "additionalTaxAmt": null,
      "exemptionQty": null,
      "twoJobs": null,
      "maritalStatus": null,
      "taxTypeCd": "ONTARIO"
    },
    {
      "specialLetter": null,
      "netClaimAmount": null,
      "otherIncome": null,
      "deductionAmt": null,
      "dependentAmt": null,
      "additionalTaxPCT": null,
      "additionalTaxAmt": null,
      "exemptionQty": null,
      "twoJobs": null,
      "maritalStatus": null,
      "taxTypeCd": null
    }
  ],
  "earnings": [
    {
      "desc": "REGULAR EARNINGS",
      "rate": 0,
      "hours": 0,
      "ytdHours": 51.19,
      "currAmt": 0,
      "ytdAmt": 842.07
    },
    {
      "desc": "O/T @ 1.5",
      "rate": 0,
      "hours": 0,
      "ytdHours": 7,
      "currAmt": 0,
      "ytdAmt": 172.73
    },
    {
      "desc": "VAC PAY YE $",
      "rate": 0,
      "hours": 0,
      "ytdHours": 8.82,
      "currAmt": 0,
      "ytdAmt": 145.09
    },
    {
      "desc": "REGULAR EARNINGS- RETRO",
      "rate": 0,
      "hours": 0,
      "ytdHours": 0,
      "currAmt": 230.3,
      "ytdAmt": 0
    }
  ],
  "taxes": [
    {
      "taxType": "TAX",
      "desc": "CPP EMPLOYEE CONTRIBUTION",
      "currAmt": 0,
      "ytdAmt": 37.89
    },
    {
      "taxType": "TAX",
      "desc": "EI EMPLOYEE PREMIUMS",
      "currAmt": 0,
      "ytdAmt": 18.91
    },
    {
      "taxType": "TAX",
      "desc": "CPP EMPLOYEE CONTRIBUTION- RETRO",
      "currAmt": 10.53,
      "ytdAmt": 0
    },
    {
      "taxType": "TAX",
      "desc": "EI EMPLOYEE PREMIUMS- RETRO",
      "currAmt": 3.75,
      "ytdAmt": 0
    }
  ],
  "deductions": [],
  "depositDistribution": [],
  "holdIndicator": null,
  "_rid": "Ubx1A1f0aafNAAAAAAAAAA==",
  "_self": "dbs/Ubx1AA==/colls/Ubx1A1f0aac=/docs/Ubx1A1f0aafNAAAAAAAAAA==/",
  "_etag": "\"02000454-0000-0500-0000-667b3e040000\"",
  "_attachments": "attachments/",
  "_ts": 1719352836
}


```
