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
  text: String!
}







```
