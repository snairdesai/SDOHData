# SDOH Data

Overview of SDOH datasets for HGHI/HSPH/BSPH research needs.

**1. ACS, PUMS, and IPUMS**

*A) ACS*

  - The ACS is a [nationwide survey](https://www2.census.gov/programs-surveys/acs/tech_docs/subject_definitions/2019_ACSSubjectDefinitions.pdf) focusing on social, economic, housing, 
    demographic, and other community indicators. It is far more detailed than the decennial Census.

  - The Census publishes ACS Data Profiles, tabulated either yearly (more frequent, but with larger margin of errors and 
    less granularity) or every five years.

  - The annual sample size of the ACS is roughly 3.5M households. For one-year ACS tabulations, only counties with 
    populations of greater than 65,000 inhabitants are included. 

  - The five-year tabulations aggregate results from each annual survey over the period, which allows for information even 
    in counties with smaller population shares.

  - Unlike the decennial Census, the ACS aggregates indicators over periods of time (one year or five years). The Census '     captures a moment in time. 

  - If you’d like earlier archival data, you can check out the Data.gov catalog. You can also find summary files going back     either farther back.

*B) PUMS*

  - In addition to these general tabulations, the Census Bureau also makes available PUMS (Public Use Microdata Sample 
    Files) to allow researchers to generate more granular datasets for their own needs.

  - PUMS data is available either at the individual or household level, and weighted respectively.
    Geography is at the Regional, State, and PUMAs level.

  - The delineations of PUMAs are a bit complicated to understand and are redrawn based on every decennial Census, but are 
    reviewed in the Census documentation (page 5).

  - PUMAs are identified by a five-digit code, which must be uniquely identified across states (meaning you can have the  
    same PUMAs codes across states).

  - There are also PUMA codes available for individuals’ Place of Work (POW) and migrations (MIG). These aren’t always 
    aligned with standard PUMAs.

  - PUMS files include about 66% of respondents from a given ACS year or five-year period (data is available at the 
    individual level, and de-identified).

  - When downloading the files, note they are individually composed (i.e. separated into “a”, “b”, “c”, “d”) and must be 
    combined to create a national dataset.

  - For context: One-year PUMS files constitute about 1% of the total US population (therefore five-year files constitute 
    about 5%).

  - You can also match the housing files to the individual files by the SERIALNO variable.

  - There are 250 PUMS individual-level variables, and 200 household-level variables (so, a lot). 

  - The Census has detailed guides on the ACS and PUMS, each of which cater to a specific demographic (i.e. they have a 
    file for everyday citizens, for journalists, for researchers, etc.)

*C) IPUMS*

  - The IPUMS US project aggregates historical Census data (both from the ACS and PUMS files) across much broader 
    historical ranges.

  - Data is provided for individual-level representative samples from 1850-1880, 1900-present, as well as the ACS files 
    from 2000-present.

  - Note, you are unable to trace individuals across multiple years, and there are substantial differences across sample       years. However, there are a set of “harmonized variables” that are shared across the sample period.

  - To explore the data, you need to create a (free) account and select a subsample of interest. There isn’t a traditional 
    “data documentation” PDF (because of the sheer size of the data), but rather a user interface to learn more about 
    selected variables of interest.

*R Packages to help work with Census data - tidycensus; acs; tigris → for a more detailed guide, see here.*


