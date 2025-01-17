# Columbia University Academic Commons Weeding Project
A project of weeding legacy duplicate materials from Academic Commons, Fall 2022.

A list of duplicate resources are identified from Academic Commons (AC) — the digital scholarship repository of Columbia University. Duplicates are flagged and pointed to the ones that would be remained in the repository for further actions.

- First created: 2022-11-10.
- Last updated: 2022-12-23 version 2.

## all_dupe_and_related.ipynb

From the duplicate list of parent items, this script searches for their children (assets) from the repository. The resulting list will be exported as 2 CSV files. On Hyacinth — the backend digital object management platform — the exported list will be used to merge stats of duplicates before removal. On DataCite, the duplicates will be redirected to appropriate resources.

**Inputs:**
- 1 CSV file with the full AC corpus from Hyacinth (published and unpublished, assets and items)
- 1 CSV file with defined duplicates, with the following column titles: 'delete--DOI', 'delete--PID', 'OR Digital Object Type > String Key', 'OR Title 1 > Sort Portion', 'keep--PID', 'keep--DOI' (note: you can amend the code, if you do not have all of these column titles)

**Outputs:**
- 1 CSV file for Hyacinth
- 1 CSV file for DataCite

**Main Processes:**
1. Import (a) the complete data exported from AC, and (b) the list of current duplicates identified in AC.
2. Select items from (b) that are marked as duplicates ('Yes dupe').
3. Look up bulk AC data for duplicates' child assets.
4. Output as 2 CSV, one for Hyacinth, the other one for DataCite.

## all_dupe_and_related_v2.ipynb

Adding a new part in [21] to do a child-level mapping from the duplicate asset to its equivalent keeping asset. This mapping facilitates Hyacinth to merge usage statistics before removing the duplicates. The mapping will skip any unpublished duplicates and metadata XML.

**Inputs:**
- 1 CSV file with the full AC corpus from Hyacinth (published and unpublished, assets and items)
- 1 CSV file with defined duplicates, with the following column titles: 'delete--DOI', 'delete--PID', 'OR Digital Object Type > String Key', 'OR Title 1 > Sort Portion', 'keep--PID', 'keep--DOI' (note: you can amend the code, if you do not have all of these column titles)

**Outputs:**
- 1 additional CSV file for Hyacinth

**Main Processes:**
1. Collect a list of child assets of the stay-published parent items.
2. Continue to work on the duplicate child assets found before this step, while skipping those that had not been published on Academic Commons, and the duplicate items’ metadata XML, which were unintentionally published.
3. Mapping the two sets of assets.
4. Output as a CSV file for Hyacinth.

