query {
  getCertainPayStub(
    win: "224823028",
    payrollRunDate: "2023-06-28",
    sequenceRowCode: "01"
  ) {
    id
    holdIndicator
    payPeriodSummary {
      win
      year
      payrollRunDate
      payPeriodEndDate
      sequenceRowCode
      payrollCorpCode
      checkSeriesCode
      checkType
      payToName
      checkNbr
      checkDate
      grossCheckAmount
      netCheckAmount
    }
    payAssociateInfo {
      userID
      firstName
      middleInitial
      lastName
      nameSuffix
      addrLine1
      addrLine2
      addrLine3
      city
      stateCode
      countyCode
      regionCode
      zipCode
      payCategory
      ascStoreDetails {
        divNbr
        storeName1
        storeName2
        storeNbr
        addrLine1
        addrLine2
        city
        stateCode
        countyCode
        regionCode
        zipCode
      }
      jobTitle
    }
    checkInfo {
      payPDBeDate
      payPEndDate
      checkDate
      clearedDate
      voidDate
      checkNbr
      checkType
      checkAmt
      totalAmt
      payFrequency
    }
    checkAdviseSummary {
      category
      currAmt
    }
    w4 {
      specialLetter
      netClaimAmount
      otherIncome
      deductionAmt
      dependentAmt
      additionalTaxPCT
      additionalTaxAmt
      exemptionQty
      maritalStatus
      taxTypeCd
    }
    earnings {
      desc
      rate
      hours
      ytdHours
      currAmt
      ytdAmt
    }
    taxes {
      taxType
      desc
      currAmt
      ytdAmt
    }
    deductions {
      desc
      currAmt
      ytdAmt
      category
    }
    depositDistribution {
      accountNbr
      routingNbr
      type
      amount
    }
    benefitHoursSummary {
      desc
      hours
      date
      text
    }
  }
}