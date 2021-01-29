# SDOH Data



Overview of SDOH datasets for HGHI/HSPH/BSPH research needs, from the [Presentation on SDOH](https://docs.google.com/presentation/d/1Cv2l9j2-hQvYXyVXblDQ5OM3lE42Z-s4gyr0YL3FV3U/edit?usp=sharing) given 1/29/2021.

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

  - If you’d like earlier archival data, you can check out the [Data.gov catalog](https://catalog.data.gov/dataset/2005-american-community-survey-1-year-estimates). You can also find [summary files](https://www.census.gov/programs-surveys/acs/data/data-via-ftp.html) going back either farther.

*B) PUMS*

  - In addition to these general tabulations, the Census Bureau also makes available [PUMS (Public Use Microdata Sample 
    Files)](https://www.census.gov/content/dam/Census/library/publications/2020/acs/acs_pums_handbook_2020.pdf) to allow 
    researchers to generate more granular datasets for their own needs.

  - PUMS data is available either at the individual or household level, and weighted respectively.
    Geography is at the Regional, State, and PUMAs level.

  - The delineations of PUMAs are a bit complicated to understand and are redrawn based on every decennial Census, but are 
    reviewed in the [Census documentation](https://www.census.gov/content/dam/Census/library/publications/2020/acs/acs_pums_handbook_2020.pdf) (page 5).

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

  - The Census has [detailed guides](https://www.census.gov/programs-surveys/acs/guidance.html) on the ACS and PUMS, each 
    of which cater to a specific demographic (i.e. they have a 
    file for everyday citizens, for journalists, for researchers, etc.)

*C) IPUMS*

  - The IPUMS US project aggregates historical Census data (both from the ACS and PUMS files) across much broader 
    historical ranges.

  - Data is provided for individual-level representative samples from 1850-1880, 1900-present, as well as the ACS files 
    from 2000-present.

  - Note, you are unable to trace individuals across multiple years, and there are substantial differences across sample years. However, there are a set of    
    “harmonized variables” that are shared across the sample period.

  - To explore the data, you need to create a (free) account and select a subsample of interest. There isn’t a traditional 
    “data documentation” PDF (because of the sheer size of the data), but rather a [user interface](https://usa.ipums.org/usa-action/variables/group) to learn more 
    about selected variables of interest.

*R Packages to help work with Census data - [tidycensus](https://cran.r-project.org/web/packages/tidycensus/index.html); [acs](https://cran.r-project.org/web/packages/acs/acs.pdf); [tigris](https://cran.r-project.org/web/packages/tigris/index.html), or for a more detailed guide, see [here](https://rconsortium.github.io/censusguide/r-packages-all.html).*


**2. CDC SVI**

  - Constructed by CDC’s Agency for Toxic Substances and Disease Registry. Data is meant to illustrate a community’s social 
    vulnerability, as measured by the potential inability to or high cost of responding to disasters (naturally, this has 
    meant it has become very relevant during COVID-19).

  - This vulnerability is captured relatively. So they are essentially ranking US tracts and counties by risk levels. 
    *Higher values = more vulnerable.*

  - For documentation on how exactly the SVI calculated their relative rankings, see [this paper](https://www.atsdr.cdc.gov/placeandhealth/svi/img/pdf/Flanagan_2011_SVIforDisasterManagement-508.pdf) from their 2011 
    publication.

  - The four summary themes are based on a set of fifteen social factors (i.e. unemployment, lack of vehicle access, 
    disability, etc.).

  - Started adding Tribal Tracts in 2014, but estimates are not ranked relative to one another or other 
    US tracts.

*Variable Assignment* 

  - There are two separate datasets available by year, at the national and state level. The former is used for relative 
    percentile rankings across the U.S., while the later is used for comparisons within individual states. The majority of 
    their population statistics is pulled directly from the U.S. Census.

  - In the latest file (2018) they included two additional adjunct variables which are not used to calculate relative     
    rankings (daytime population & people without health insurance).

  - Variables prefixed with “E” represent estimates, while those prefixed by “M” represent margins of error (just like the 
    Census, where they get most of their data).

  - Missing Values are coded as -999, so be careful to remove them prior to tabulation.

  - Geographic Shifts: Sometimes U.S. counties do not have relevant population estimates, and the count of these missing 
    counties varies by year. About 645 U.S. counties were missing in the most recent file (2018).
    
 **3. Area Deprivation Index**
 
  - Also known as the “Neighborhood Atlas”, hosted by University of Wisconsin. First created in 1990, and then revamped in 
    2000 (not publicly available as of now).

  - Data is constructed across all Census US Block Groups using data pulled from the five-year ASC files.

  - Data is protected for any communities with fewer than 100 inhabitants, OR 30 housing units, OR more than a third of 
    the population living in group quarters.

  - The single most important indicator is the ADI percentile ranking, for which higher percentiles indicate more 
    disadvantaged communities. For a paper outlining the construction of those metrics, see [this paper](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4251560/pdf/nihms619606.pdf).

  - While data is available at the Block group level, crosswalks so exist which can link these data at the ZCTA-level. 
    However, this is not normally recommended for these specific metrics.

 **4. HRSA AHRF**
 
  - Composite of 50 unique healthcare datasets, covering over 6000 variables - including from the AMA Masterfile data. 
    AMA M.D. data pulled from 1990, 2000, 2005, and from 2010-2018.

  - Important to note some studies have compared AMA survey data to state licensing boards and found sizeable 
    discrepancies.

  - The AMA data provides the following sub-classifications for Physicians’ Major Professional Activities:
    Office Based Practices; Hospital Based Practices; Hospital Full-Time Staff; Residents; Medical Teaching; Medical     
    Research; and Administration.

  - They pull health facility and utilization data from the AHA Annual Survey of Hospitals → in 2018, the survey covered 
    6,146 U.S. hospitals (of which 1,815 did not respond, and values were imputed). Expenditures are pulled from the CMS 
    for 2010, 2015, and 2018. 

  - They also have expenditures for VA facilities from the Office of Policy and Planning, Department of Veteran Affairs 
    from 2012-2018.

  - Also includes Health Professional Shortage Area data (indicate shortages in primary care, dental care, and mental 
    health by U.S. county).

  - They calculate three scores for these healthcare shortages, based on population-to-provider ratio; percentage below       the poverty line; and travel time to the nearest source of care.

  - Variable categories: Codes and ID variables; Health Professions (i.e. physicians, dentists, podiatrists, etc.); Health 
    Facilities (hospital type, employment, nursing facilities, etc.); Utilization (inpatient days; outpatient visits, 
    etc.); Expenditures; Population; Environment (air quality, elevation, ground contamination).

  - The data also includes county-level Rural and Urban Continuum Codes from 2013, pulled from the US Department of 
    Agriculture.

**5. AHRQ**

  - Social: Demographics, Age, Race/Ethnicity, SVI, Segregation, Living Conditions
  - Economic: Workforce/Employment, Poverty, Income
  - Infrastructure: Environment, Crime, Housing, Food Access, Transportation
  - Healthcare: Access, Quality, Health Insurance Status, Health Behavior, Health Status, Utilization

  - Difference between Zip Codes and ZCTAs → ZCTAs constitute a series of Census block groups, which are not defined 
    exactly based on traditional zip codes → so be careful when merging patient information by zip code to the ZCTA files. 
    HRSA provides a [helpful crosswalk](https://udsmapper.org/zip-code-to-zcta-crosswalk/).

*Data from:*

  - American Community Survey (ACS -- includes five-year files, not one and three-year files + based on 2010 Census); 
    Area Health Resource Files (AHRF); Social Vulnerability Index (SVI); amfAR Opioid and Health Indicators Database; CDC 
    Interactive Atlas of Heart Disease and Stroke; Medicare Advantage Penetration Files (MAP); and Civil Rights Data 
    Collection

*Notes on their Collection Procedure:*

  - Variable Assignment → Either linked by single year (i.e. Nursing Home Compare data from 2016 appears in the 2016 file) 
    OR linked by last year available for ranges (i.e. ACS data over the range 2012-2016 appears in the 2016 file).

  - Variable Names → All variables are prefixed by the data source, which will be helpful for differentiating underlying 
    collection

  - Missing Values → Coded as blank, with the exception of the County Health Ranking Data, where they are coded as 
    negative

  - Geographic Shifts → Sometimes county-level indicators are averaged over many years, which means data may be presented 
    for a county which no longer exists, or has not yet been established → the [Census website](https://www.census.gov/programs-surveys/geography/technical-documentation/county-changes.1990.html) reviews the counties 
    for which this might be problematic.
