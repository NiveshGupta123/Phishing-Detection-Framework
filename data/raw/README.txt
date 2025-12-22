==========================================================================
RAW DATA SOURCE SPECIFICATION
==========================================================================

[!] NOTE TO EVALUATORS:
This project utilizes a large-scale dataset of 80,000+ phishing and legitimate 
webpages. Due to size constraints, the raw HTML files are not hosted on GitHub.

Please follow the instructions below to reproduce the environment.

--------------------------------------------------------------------------
1. DATASET ORIGIN
--------------------------------------------------------------------------
* NAME: Phishing Websites Dataset (Mendeley Data)
* DESCRIPTION: A collection of legitimate and phishing website instances, 
  each containing the URL and the relevant HTML page content.

* STATISTICS:
  - Total Instances: ~83,275
  - Legitimate Websites (Label 0): 50,000
  - Phishing Websites (Label 1): 30,000

--------------------------------------------------------------------------
2. FILE STRUCTURE & MAPPING
--------------------------------------------------------------------------
The original dataset uses an SQL dump (`index.sql`) as the root mapping file. 
For this project, we have converted/exported this metadata into CSV format 
to simplify the parsing pipeline.

* MAPPING FILE: `url,webpage,result.csv` (Derived from index.sql)
  - This file maps every URL to its corresponding HTML filename.
  - COLUMNS:
      1. rec_id: Unique record ID
      2. url: The original URL of the webpage
      3. website: Filename of the downloaded HTML (e.g., '1635698138155948.html')
      4. result: Label (0 = Legitimate, 1 = Phishing)
      5. created_date: Date of download

--------------------------------------------------------------------------
3. INSTALLATION INSTRUCTIONS
--------------------------------------------------------------------------
To reproduce the Feature Extraction phase (`01_Data_Preprocessing.ipynb`):

1. Download the full dataset from the source (Mendeley).
2. Unzip the archive.
3. Place the raw HTML folder and the `url,webpage,result.csv` file into:
   >  Phishing-Detection-Framework/data/raw/

--------------------------------------------------------------------------
4. PREPROCESSING LOGIC
--------------------------------------------------------------------------
Our script reads `url,webpage,result.csv`, locates the corresponding HTML 
file listed in the 'website' column, parses the DOM structure, and extracts 
features to generate the final dataset.