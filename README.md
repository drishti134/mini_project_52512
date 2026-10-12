What Do Employers Want from Graduates?
Exploratory Data Analysis of 120,000+ LinkedIn Job Postings (2023–2024)

As a soon-to-be graduate, I wanted to know what recruiters actually ask for, using real job ads instead of general careers advice. This project collects, cleans and explores a large dataset of LinkedIn job postings, and compares entry-level jobs with more senior ones.

Key findings
Finding	Result
Entry-level jobs that ask for 2+ years of experience (among those stating a number)	64%
Median advertised salary: entry level vs mid-senior	$52,831 vs $108,750
Entry-level jobs that allow remote work	5.3% (vs 14.7% mid-senior)
Entry-level jobs that disclose a salary	25.2%
Entry-level jobs that mention AI	1.9% (vs 4.4% mid-senior)

The data is a snapshot of spring 2024 (98.5% of postings were listed in April 2024), mostly from the US.

Data
Source: LinkedIn Job Postings (2023–2024) by Arsh Koneru, Kaggle
Collected with: the open-source LinkedIn-Job-Scraper
Size: 123,849 postings, 11 linked CSV files (557 MB); 115,413 postings after cleaning

The raw data is not included in this repository because of its size. Download it from Kaggle (see below).

Repository structure
├── prepare_linkedin_data.py   # joins the Kaggle files into one table, converts dates, derives text variables
├── EDA_LinkedIn_Jobs.ipynb    # cleaning, descriptive statistics and all charts
├── figures/                   # charts exported from the notebook
├── report/                    # final project report (PDF)
├── requirements.txt
└── README.md

How to reproduce
Install the libraries:
   pip install -r requirements.txt
Download the dataset from Kaggle and unzip it into a folder called data/ in this repository.
Build the combined table (creates linkedin_jobs_2023_2024.csv):
   python prepare_linkedin_data.py
Open and run EDA_LinkedIn_Jobs.ipynb. It saves the charts to figures/ and the cleaned data to linkedin_jobs_clean.csv.

Methods
Data preparation: joining postings with skills, industries and company tables; converting millisecond timestamps to dates; extracting mentions_ai and years_experience_asked from job descriptions with regular expressions.
Data-quality checks: structural vs genuine missing values, discontinuous dates, impossible salaries (up to $535M/year), re-posted jobs, invalid codes.
Handling: structural blanks recoded, implausible salaries removed, re-posts dropped, "Not specified" category for missing experience level. Imputation was tested and rejected for years of experience.
Analysis: mean, median and standard deviation by experience level; distributions; skill-area comparison; correlations.

Limitations and next steps
Single snapshot, mostly US; salary known for about 30% of postings.
The AI flag is keyword-based, so it also catches companies describing their own AI products.
Next steps: salary regression, a pay-disclosure classifier, NLP on full descriptions, and monthly re-scraping (including Polish postings) to build a real time series.
Author

Drishti Roy — Mini Project, Kozminski University (2026)
