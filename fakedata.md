```java

List<RootPaystub> findByPayPeriodSummary_WinAndPayPeriodSummary_PayrollRunDateLessThanEqualAndPayPeriodSummary_PayrollRunDateGreaterThanEqual(int win, String startDate, String endDate);

@Query("SELECT * FROM c WHERE c.payPeriodsummary.win = @win AND c.payPeriodsummary.payrolRunDate <= @endDate AND c.payPeniodsummary.payrolRunDate >= @startDate")
    List<Employee> findByPayPeriodSummary(@Param("win") int win, @Param("startDate") String startDate, @Param("endDate") String endDate);

SELECT c.payPeriodSummary
FROM c
WHERE c.win = '224823227'
AND ((c.payPeriodSummary.payPDBegDate[0] = 2023 AND c.payPeriodSummary.payPDBegDate[1] = 6 AND c.payPeriodSummary.payPDBegDate[2] >= 1)
    OR (c.payPeriodSummary.payPDBegDate[0] = 2023 AND c.payPeriodSummary.payPDBegDate[1] > 6))
AND ((c.payPeriodSummary.payPDEndDate[0] = 2023 AND c.payPeriodSummary.payPDEndDate[1] <= 7 AND c.payPeriodSummary.payPDEndDate[2] <= 31)
    OR (c.payPeriodSummary.payPDEndDate[0] = 2023 AND c.payPeriodSummary.payPDEndDate[1] < 7))

package com.walmart.paystub.api.global.services;

import com.walmart.paystub.api.global.models.paystub.PaystubDTO;
import com.walmart.paystub.api.global.models.paystub.RootPaystub;
import com.walmart.paystub.api.global.repositories.RootPaystubRepository;
import org.junit.jupiter.api.BeforeEach;
import org.junit.jupiter.api.Test;
import org.mockito.ArgumentMatchers;
import org.mockito.InjectMocks;
import org.mockito.Mock;
import org.mockito.MockitoAnnotations;
import org.springframework.boot.test.context.SpringBootTest;

import java.time.LocalDate;
import java.util.ArrayList;
import java.util.List;

import static org.mockito.Mockito.when;
import static org.junit.jupiter.api.Assertions.assertNotNull;

@SpringBootTest
public class PaystubServiceImplTest {

    @Mock
    private RootPaystubRepository rootPaystubRepository;

    @InjectMocks
    private PaystubServiceImpl paystubService;

    @BeforeEach
    void setup() {
        MockitoAnnotations.openMocks(this);
    }

    @Test
    void getRootpaystubsByQuery() {
        // Arrange
        Long win = 224823227L;
        LocalDate payPDBegDate = LocalDate.of(2023, 6, 28);
        LocalDate payPDEndDate = LocalDate.of(2023, 6, 28);

        List<RootPaystub> mockPaystubs = new ArrayList<>();
        mockPaystubs.add(new RootPaystub());

        when(rootPaystubRepository.findByPayPeriodSummary_WinAndCheckInfo_PayPDBegDateAndCheckInfo_PayPDEndDate(
                ArgumentMatchers.anyLong(), ArgumentMatchers.any(LocalDate.class), ArgumentMatchers.any(LocalDate.class)
        )).thenReturn(mockPaystubs);

        PaystubDTO paystubDTO = new PaystubDTO();
        paystubDTO.setWin(win);
        paystubDTO.setPayPDBegDate(payPDBegDate);
        paystubDTO.setPayPDEndDate(payPDEndDate);

        // Act
        List<RootPaystub> rootpaystubs = paystubService.getRootpaystubsByQuery(paystubDTO);

        // Assert
        assertNotNull(rootpaystubs);
    }
}

@GetMapping("/getRootpaystubsByQuery")
    public ResponseEntity<List<RootPaystub>> getRootpaystubsByQuery() {
        String winStr = request.getHeader("win");
        String payPDBegDateStr = request.getHeader("payPDBegDate");
        String payPDEndDateStr = request.getHeader("payPDEndDate");

        Long win = Long.parseLong(winStr);
        DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd");
        LocalDate payPDBegDate = LocalDate.parse(payPDBegDateStr, formatter);
        LocalDate payPDEndDate = LocalDate.parse(payPDEndDateStr, formatter);

        PaystubDTO paystubDTO = new PaystubDTO();
        paystubDTO.setWin(win);
        paystubDTO.setPayPDBegDate(payPDBegDate);
        paystubDTO.setPayPDEndDate(payPDEndDate);

        List<RootPaystub> rootpaystubs = paystubService.getRootpaystubsByQuery(paystubDTO);

        return new ResponseEntity<>(rootpaystubs, HttpStatus.OK);
    }

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

return RootPaystub.builder()
                .id("3c2fec05-b86e-455f-9d7d-c70c1804ea9e")
                .payAssociateInfo(PayAssociateInfo.builder()
                        .userID(473391472L)
                        .firstName("DANIEL")
                        .middleInitial(null)
                        .lastName("BEYETTE")
                        .addrLine1("302-94 SIDNEY ST")
                        .addrLine2(null)
                        .addrLine3(null)
                        .city("BELLEVILLE")
                        .stateCode("ON")
                        .stateProvCode(null)
                        .zipCode("K8P 3Z1")
                        .payCategory("Hourly")
                        .ascStoreDetails(AscStoreDetails.builder()
                                .divNbr("C2920001")
                                .storeName1("WAL-MART CANADA, CORP.")
                                .storeName2(null)
                                .storeNbr(null)
                                .addrLine1("1940 ARGENTIA ROAD")
                                .addrLine2(null)
                                .city("MISSISSAUGA")
                                .stateCode("ON")
                                .stateProvCode(null)
                                .zipCode(null)
                                .build())
                        .jobTitle("(CAN) STOCK UNLOADER ASSOCIATE")
                        .build())
                .payPeriodSummary(PayPeriodSummary.builder()
                        .win(224823227L)
                        .year(null)
                        .payrollRunDate(Collections.singletonList(LocalDate.of(2023, 6, 28)))
                        .payPDEndDate(Collections.singletonList(LocalDate.of(2023, 6, 28)))
                        .seqRowCd(null)
                        .payrollCorpCd(null)
                        .checkSeriesCd(null)
                        .checkType(null)
                        .payToName(null)
                        .checkNbr(null)
                        .checkDate(LocalDate.of(2023, 6, 29))
                        .grossCheckAmt(230.3)
                        .netCheckAmt(216.02)
                        .build())
                .checkInfo(CheckInfo.builder()
                        .payPDBegDate(LocalDate.of(2023, 6, 28))
                        .payPDEndDate(LocalDate.of(2023, 6, 28))
                        .checkDate(LocalDate.of(2023, 6, 29))
                        .clearedDate(null)
                        .voidDate(null)
                        .checkNbr(null)
                        .checkType("Correction")
                        .checkAmt(null)
                        .totalAmt(null)
                        .payFrequency("Bi-Weekly")
                        .build())
                .checkAdviseSummary(List.of(
                        CheckAdviseSummary.builder().category("earnings").currAmt(230.3).ytdAmt(1159.89).build(),
                        CheckAdviseSummary.builder().category("taxes").currAmt(14.28).ytdAmt(56.8).build(),
                        CheckAdviseSummary.builder().category("post-tax").currAmt(0.0).ytdAmt(0.0).build(),
                        CheckAdviseSummary.builder().category("pre-tax").currAmt(0.0).ytdAmt(0.0).build(),
                        CheckAdviseSummary.builder().category("gross-pay").currAmt(230.3).ytdAmt(1159.89).build(),
                        CheckAdviseSummary.builder().category("federal-taxable-wages").currAmt(0.0).ytdAmt(0.0).build(),
                        CheckAdviseSummary.builder().category("net-pay").currAmt(216.02).ytdAmt(1103.09).build(),
                        CheckAdviseSummary.builder().category("hours").currAmt(0.0).ytdAmt(67.01).build()
                ))
                .w4(List.of(
                        W4.builder().specialLetter(0.0).netClaimAmount(15000.0).otherIncome(null).deductionAmt(null)
                                .dependentAmt(null).additionalTaxPCT(0.0).additionalTaxAmt(null).exemptionQty(null)
                                .twoJobs(null).maritalStatus(null).taxTypeCd("FEDERAL").build(),
                        W4.builder().specialLetter(0.0).netClaimAmount(11865.0).otherIncome(null).deductionAmt(null)
                                .dependentAmt(null).additionalTaxPCT(0.0).additionalTaxAmt(null).exemptionQty(null)
                                .twoJobs(null).maritalStatus(null).taxTypeCd("ONTARIO").build()
                ))
                .earnings(List.of(
                        Earnings.builder().desc("REGULAR EARNINGS").rate(0.0).hours(0.0).ytdHours(51.19).currAmt(0.0).ytdAmt(842.07).build(),
                        Earnings.builder().desc("O/T @ 1.5").rate(0.0).hours(0.0).ytdHours(7.0).currAmt(0.0).ytdAmt(172.73).build(),
                        Earnings.builder().desc("VAC PAY YE $").rate(0.0).hours(0.0).ytdHours(8.82).currAmt(0.0).ytdAmt(145.09).build()
                ))
                .taxes(List.of(
                        Taxes.builder().taxType(TaxTypeEnum.TAX).desc("CPP EMPLOYEE CONTRIBUTION").currAmt(0.0).ytdAmt(37.89).build(),
                        Taxes.builder().taxType(TaxTypeEnum.TAX).desc("EI EMPLOYEE PREMIUMS").currAmt(0.0).ytdAmt(18.91).build(),
                        Taxes.builder().taxType(TaxTypeEnum.TAX).desc("CPP EMPLOYEE CONTRIBUTION- RETRO").currAmt(10.53).ytdAmt(0.0).build(),
                        Taxes.builder().taxType(TaxTypeEnum.TAX).desc("EI EMPLOYEE PREMIUMS- RETRO").currAmt(3.75).ytdAmt(0.0).build()
                ))
                .deductions(Collections.emptyList())
                .depositDistribution(Collections.emptyList())
                .holdIndicator(null)
                .build();

```
