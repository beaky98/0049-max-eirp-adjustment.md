# HIP 49: LoRaWAN Sub-region Max EIRP Limit

- Author(s): [@beaky98](https://github.com/beaky98) [@resyncX](https://github.com/resyncX) [@AnhTuDo1998](https://github.com/AnhTuDo1998)[Trinitrophenol81](https://github.com/Trinitrophenol81)
- Start Date: 2021-12-20
- Category: technical
- Original HIP PR: <!-- leave this empty; maintainer will fill in ID of this pull request -->
- Tracking Issue: <!-- leave this empty; maintainer will create a discussion issue -->

# Summary
[summary]: #summary

This proposal suggests adopting a LoraWAN subregion config for max EIRP limit which will allow individual countries within an RF region i.e. AS923 to define max EIRP limit based on each country’s local regulation instead of a single max EIRP limit across the entire AS923 as a result of PoCv11.

# Motivation
[motivation]: #motivation

Helium aims to provide coverage as the people’s network and we are trying to help by restoring the coverage area in countries where the respective max EIRP limits are higher than the 16dBm (40mW) currently set for the entire AS923 region via PoCv11. It has since reduced the coverage area significantly and the effects can be seen clearly with a drop in the number of witnesses and witnessed by others before and after the implementation of PoCv11.

For countries in AS923 region where their max EIRP limit is between 25-27dBm, we can expect to see an increase of coverage area probably close to the same level as prior to PoCv11 (as the previous hardcoded EIRP limit was 27dBm).

This implementation can be extended to other regions as well (if required) 


# Stakeholders
[stakeholders]: #stakeholders

Hotspots in AS923 region where the local regulatory EIRP limit is higher than the current 16dBm EIRP limit set will benefit from this proposal. And this can be extended to regions that are affected.

We have started to reach out to people in Helium discord regional channels: hk-hong-kong, id-indonesia, jp-japan, my-malaysia, ph-philippines, sg-singapore, th-thailand, tw-taiwan. 

As this issue has been raised in this: https://github.com/helium/miner/issues/1105 , we will be contacting them via GitHub to solicit feedback on this HIP.

# Detailed Explanation
[detailed-explanation]: #detailed-explanation

To implement country-specific EIRP limits via LoRaWAN subregions. Individual country EIRP max limit can be defined within the LoRaWAN subregion instead of a fixed value for the entire region.

For countries that do not have a subregion max EIRP limit value defined, it should then fall back to the default regional max EIRP limit value of 16dBm.
This can be extended to any region outside of AS923 if such an issue exists for other regions as well.

The software probably needs to be written to the core blockchain. Software update deployed to all Hotspots, Validators, etc to support the new rules. This is consensus affecting so it needs to be a full deployment.

The LoRaWAN committee of the DeWI needs to propose and manage the subregion settings. They could also propose initial chain variables. These variables should be maintained by the LoRaWan committee on an ongoing basis.


# Drawbacks
[drawbacks]: #drawbacks

TBD

# Rationale and Alternatives
[alternatives]: #rationale-and-alternatives

We have explored the possibility of including this as part of HIP45 as it is the closest HIP with regards to country-specific values.

However considering that is addressing the frequency plan selection for different countries rather than max EIRP limits, it may further complicate things/the deployment process and might not be the best way to implement this hence we have drafted this new HIP for consideration/implementation.

# Unresolved Questions
[unresolved]: #unresolved-questions

- What parts of the design do you expect to resolve through the HIP process
  before this gets merged?

- What parts of the design do you expect to resolve through the implementation
  of this feature?

- What related issues do you consider out of scope for this HIP that could be
  addressed in the future independently of the solution that comes out of this
  HIP?

# Deployment Impact
[deployment-impact]: #deployment-impact

Describe how this design will be deployed and any potential impact it may have on
current users of this project.

- How will current users be impacted?

- How will existing documentation/knowlegebase need to be supported?

- Is this backwards compatible?

        - If not, what is the procedure to migrate?

# Success Metrics
[success-metrics]: #success-metrics

What metrics can be used to measure the success of this design?

- What should we measure to prove a performance increase?

- What should we measure to prove an improvement in stability?

- What should we measure to prove a reduction in complexity?

- What should we measure to prove an acceptance of this by it's users?
