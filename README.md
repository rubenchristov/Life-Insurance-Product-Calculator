# Life Insurance Product Calculator

### Overview
This Excel Workbook is an interactive life insurance product calculator for different products with multiple dropdown options. 
Users are also free to select different policy assumptions such as the annual effective interest rate, mortality table, coverage term, and more.
The calculator outputs a net single premium value to be paid by the policyholder at outset, and optionally an equivalent amount for regular premium and benefit payments instead of a single amount.

All mortality data are taken from the [Society of Actuaries](https://mort.soa.org/Default.aspx).

The full list of currently supported inputs are as follows:
- Policyholder current age, gender, and region
- Annual effective interest rate
- Sum assured
- Policy/product type (whole life, term, endowment, pure endowment)
- Term of coverage
- Premium frequency (single, annual, semi-annual, quarterly, monthly)
- Premium paying period (while alive, limited term)
- Premium paying term (if limited term is chosen)
- Benefit frequency (single, annual, semi-annual, quarterly, monthly)
- Benefit payment term
- Mortality table

### Key Assumptions and Limitations
- Constant interest rate from policy inception until final payment stream.
- Death benefits are paid starting at end of year of death, but can be regular payments more frequent than yearly
- Timing for death benefits currently only allow for payments starting at the end of year of death for simplicity, which can be sooner in practice.
- Maturity benefits are paid immediately upon policy maturity, but can also be regular payments instead of at once
- For decimal ages, the Uniform Distribution of Deaths (UDD) assumption is used.
- Current policyholder age/Age at policy inception is assumed to be Age at Last Birthday
- Expenses and fees are currently not included in the calculations.
- Lapses and withdrawals are also currently not included.
- Mortality table selection currently only include a very limited number of options.

### Methodology
Using the sum assured, mortality assumptions, and effective interest rate, the calculator finds the expected present value of the benefits (sum assured), by considering all the possible timings where the benefits can be paid out and their corresponding probabilities of occurring. Afterwards, each of these possible benefits are discounted back to policy inception (time 0) using the discount factor.

Under the equivalence principle, the expected value of premiums (money coming in to the insurer) must match the expected value of benefits (money coming out). Thus, the calculator will output a Net Single Premium, assumed to be paid at time 0, that equals the latter.

The calculator also provides the option of regular premium and benefit payments instead of a single amount. To account for this, multiple annuity-due factors are computed, including whole life and temporary annuity-dues for premium conversion, as well as certain annuity-due for benefit conversion. When applicable, the Net Single Premium and the Sum Assured will be divided by the appropriate annuity factor to obtain the exact level amount.
