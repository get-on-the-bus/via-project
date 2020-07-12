# Data from U.S. Census Bureau

**This product uses the Census Bureau Data API but is not endorsed or certified by the Census Bureau.**

1. API Data Discovery Tool
    1. [HTML format](https://api.census.gov/data.html)
    1. [JSON format](https://api.census.gov/data.json)
1. [American Community Survey 5-Year Data](https://www.census.gov/data/developers/data-sets/acs-5year.html)
    1. API Template [https://api.census.gov/data/2018/acs/acs5?get=B00001_001E&for=block%20group:*&in=state:48&in=county:029&in=tract:*](https://api.census.gov/data/2018/acs/acs5?get=B00001_001E&for=block%20group:*&in=state:48&in=county:029&in=tract:*)
1. [Project Open Data Schema](https://project-open-data.cio.gov/schema/)
1. [The Census Data Application Programming Interface (API)](www.census.gov/data/developers/updates/new-discovery-tool.html)
1. [Request a Census API Key](http://api.census.gov/data/key_signup.html)
1. [API Developers Guide](https://www.census.gov/data/developers/guidance/api-user-guide.html)
1. [API terms of service](https://www.census.gov/data/developers/about/terms-of-service.html)
1. [ACS Subject Definitions](https://www2.census.gov/programs-surveys/acs/tech_docs/subject_definitions/2018_ACSSubjectDefinitions.pdf?#) (PDF)

## How to get the census data into a notebook in your personal folder:
`df = pd.read_csv('../resource_files/census_data/acs5_name.csv').set_index('block_group')`
## And the data dictionary:
`df_dd = pd.read_csv('../resource_files/census_data/census_field_names.csv').set_index('field_code')`
### Within the df_dd:
1. `group_code` and `group_name` indicate the overall grouping within the American Community Survey. All columns within the same group are answering the same question(s). Some of the columns are subtotals of other columns, but these can be deciphered quickly by looking at the `full_text`.
1. `full_text` shows the specific subgrouping of answers with pipes delimiting possible responses, i.e. "Estimate|Total", which is the combined count of "Estimate|Total|Male" and "Estimate|Total|Female".
1. `is_orig` tells whether the field is from the original Census file (y) or is a calculated derived from combining other fields (n).
1. `field_code` is the code used by the Census Bureau, which enables tracing back to the source. If the field is calculated, there will be a suffix appended, generally an underscore followed by a letter or number.
1. `disposition` indicates what we're doing with the field. (k for keep, m for merge into a calculated field, and x for ignore)