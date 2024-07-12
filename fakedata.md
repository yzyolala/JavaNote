``` type Earnings {
  desc: String!
  rate: Float!
  hours: Float!
  ytdHours: Float!
  currAmt: Float!
  ytdAmt: Float!
type Taxes {
  taxType: TaxTypeEnum!
  desc: String!
  currAmt: Float!
  ytdAmt: type Deductions {
  desc: String!
  currAmt: Float!
  ytdAmt: Float!
  category: type DepositDistribution {
  accountNbr: String!
  routingNbr: String!
  type: String!
  amount: type BenefitHoursSummary {
  desc: String!
  hours: Float!
  date: String!
  text: query {
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
  }
}







```
