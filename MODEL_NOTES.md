# Modeling Notes

## Why the original notebook was revised

The original analysis produced very high model performance while relying heavily on `storage_issue_reported_l3m`. In the supplied dataset this feature has a Pearson correlation of approximately 0.987 with `product_wg_ton`.

That does not prove leakage, but it is strong enough to require investigation. The revised notebook therefore keeps the original modeling idea but explicitly compares models with and without the feature.

## Interview-safe interpretation

Do not claim that storage issues *cause* product weight. A safer statement is:

> "The dataset contains an unusually strong relationship between storage issues reported in the last three months and product weight. I treated this as a feature-validity concern and ran a leakage-aware comparison excluding the variable."

## Production recommendation

Before deploying a prediction system, define the exact prediction timestamp and confirm that every input feature is available at that time and is not derived from the target or from future information.
