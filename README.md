[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.162765.svg)](https://doi.org/10.5281/zenodo.162765)
<a href="https://www.buymeacoffee.com/H2wlgqCLO" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" height="21px" ></a>
<a href="https://liberapay.com/khufkens/donate"><img alt="Donate using Liberapay" src="https://liberapay.com/assets/widgets/donate.svg" height="21px"></a>

# MCD10A1: a robust MODIS snow cover and snow phenology product

## Description

The Google Earth Engine (GEE) code within this project combines MODIS Aqua - Terra snow cover products and derives snow melt - accumulation (snow phenology) dates.

The original MODIS products (MOD10A1 & MYD10A1, for the Terra and Aqua platforms respectively) as processed by the National Snow and Ice Data Center (NSIDC) have the tendency to be biased low.

My code fuses these two data streams using a maximum value approach to account for this bias. More importantly, the script also generates a derived snow phenology product where I calculate the date of snow melt (< 5% snow cover) in spring and and snow accumulation (> 5%) in autumn.

As an example the script runs a simple regression analysis to mark trends in snow melt dates, answering the question if snow melt occurs later or earlier over time.

## Use
You can clone the project, copy and paste the code into your current workspace / project or use the [GEE link](https://code.earthengine.google.com/bd06f9efa757b7fbf9d2ae282d319282).

## Example

Below you see a snow melt trend map of the US and Canada, with earlier snow melt marked in red and later snow melt marked in blue. 

Some clear trends can be seen in the mountain ranges in the West of the US with very pronounced earlier snow melt dates. High latitudes throughout Alaska and Canada also see a shorter snow season. Some later snow melt date trends can be noted as well, sweeping east from the middle of Alberta, Canada, to the great lakes.

Caution is needed in interpreting the trend analysis as generated by the code. The analysis relies on a simple linear regression which might be skewed by outliers. I suggest using a panel analysis or a robust regression analysis before making any scientific inference.

![](https://github.com/khufkens/MCD10A1/raw/master/output/snowmelt_trends.png)

## Validation

The MCD10A1 product has been validated against the SNOTEL network of snow dept sensors. Although both metrics are not equivalent, where SNOTEL measures snow depth and MCD10A1 landscape cover, some correspondence should exists. Results of this analysis show that overall MCD10A1 data is biased early (especially for lower latitudes). The SNOTEL data were processed using my [snotelr package](https://khufkens.github.io/snotelr/) and snow phenology statistics procedures.

![](https://github.com/khufkens/MCD10A1/raw/master/output/density_distribution_bias.png)

The previously mentioned difference in the metrics and the scale of the measurements might explain a part of this bias. Furthermore, canopy type (height) seems to have an important influence on this bias if one compares high versus low vegetation types (figures below).

Snow melt dates are better constrained than snow accumulation at the end of the season. Again, this is not surprising as snow melting is a far more continuous & abrupt process compared to snow accumulation through various snow storms. Here wind has a particularly strong effect on the amount and location of snow accumulation.

In all cases, high latitude sites have a better agreement between SNOTEL estimated values and the MCD10A1 retrieved data. The latter results indicate that at least for high latitudes the combined MCD10A1 product is robust.

![](https://github.com/khufkens/MCD10A1/raw/master/output/snow_melt_validation.png)

![](https://github.com/khufkens/MCD10A1/raw/master/output/snow_acc_validation.png)

## Acknowledgements

Please acknowledge my code by citing the github release through it's DOI, or better make me co-author on any publication which extensively uses this code! Keep in mind that this code is released under a **AGPLv3 license**, which permits commercial use but **requires that the source code (of derivatives) is always open** even if hosted as a web service (de facto the case for GEE applications).
