# Predicting and Pricing Employee Attrition

**A statistical analysis and predictive model built on IBM's HR Analytics dataset**

## The problem

Employee turnover is expensive and, in most cases, foreseeable. Using IBM's HR Analytics Employee Attrition dataset (1,470 employee records), this project set out to answer three questions a business actually needs answered:

1. **Why** are employees leaving?
2. **What** is that costing the company, and where?
3. **Can** we flag at-risk employees before they resign?

Rather than stopping at descriptive charts, this project moved through formal hypothesis testing, a validated logistic regression model, a cost estimate by department, and a predictive model evaluated on unseen data.

## Approach

The analysis followed a five-stage research design, with every statistical test chosen only after checking its assumptions (normality, variance, multicollinearity, linearity of the logit, and expected cell counts) rather than defaulting to the most familiar test.

| Stage | Question | Method |

| RQ1 | Does overtime relate to attrition? | Chi-square test |
| RQ2 | Do income and tenure differ between leavers and stayers? | Mann-Whitney U test |
| RQ3 | Do satisfaction and work-life balance predict attrition, controlling for income and overtime? | Logistic regression |
| RQ4 | What does attrition cost, and where? | Cost modelling by department |
| RQ5 | Can attrition be predicted in advance? | Logistic regression, trained/tested on a held-out split |

A key discipline throughout: when an assumption check failed (for example, a Box-Tidwell test showing Age and Tenure were non-linear predictors), the model was corrected rather than left as-is, even after results had already been produced once.

## Key findings

- **Overtime is the strongest driver of attrition.** Employees who work overtime are **4.6x** more likely to leave, even after controlling for income, satisfaction, and tenure.
- **Satisfaction and work-life balance matter independently.** Each one-level improvement in job satisfaction lowers the odds of leaving by 29%, and each one-level improvement in work-life balance lowers it by 23% — both hold even after accounting for pay and overtime.
- **Risk is concentrated in the first two years.** Attrition risk drops sharply after an employee's second year and then levels off, identifying early tenure as the critical retention window.
- **Raw totals were misleading — attrition rate told a different story.** Research & Development had the most leavers and the highest total cost, simply because it is the largest department. Once measured by *rate*, Sales had the highest attrition rate of the three departments (20.6%), making it the real priority, not R&D.
- **A predictive model can catch at-risk employees in advance.** Evaluated on employees the model had never seen, it correctly identified **77% of actual leavers**, against a naive baseline that would have caught none.

## Business impact

The analysis translated into a set of concrete, defensible recommendations: prioritise retention efforts in Sales rather than R&D; review overtime policy, since it is the single largest lever identified; and focus onboarding and engagement specifically on an employee's first two years, where risk is highest. The predictive model gives HR a ranked, evidence-based starting point for retention conversations, rather than a reactive response after someone has already resigned.

## On the predictive model's trade-off

The model prioritises **recall over precision** by design: it is tuned to minimise missed leavers, even at the cost of occasionally flagging an employee who was not actually at risk. For a retention use case, this is the right trade-off — missing a genuine resignation is more costly to a business than one extra check-in with an employee who was never going to leave.

## Tools and methods

Python (pandas, scipy, statsmodels, scikit-learn) for data cleaning, hypothesis testing, and model building · Power BI for the interactive dashboard · Logistic regression, chi-square tests, Mann-Whitney U tests, Box-Tidwell linearity testing, and VIF-based multicollinearity checks.

## Limitations

Replacement cost is estimated using a standard HR rule-of-thumb (75% of annual salary) rather than confirmed organisational figures, and the dataset does not specify a currency. The model's test set contained only 47 actual leavers, so performance estimates carry some uncertainty. Full detail on these and other limitations is available in the complete report.

---

**Olayiwola Ahmed Bolaji** · Statistics graduate (FUTA) · Data Analyst
[olayiwolaahmed17@gmail.com](mailto:olayiwolaahmed17@gmail.com) · Lagos, Nigeria
