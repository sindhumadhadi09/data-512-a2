### Goal:
The goal of this assignment is to explore the concept of bias through data on Wikipedia articles - specifically, articles on political figures from a variety of countries.
[Link to the problem statement](https://docs.google.com/document/d/11eswL84T-H6bli8aX_-XndCN6tAZ4bIb9Z2ywiIf2fE/edit?usp=sharing) 

### Data Source

Data fro this project is used from the follwing sources:
The Wikipedia politicians by country dataset can be found on Figshare.[Link](https://figshare.com/articles/dataset/Untitled_Item/5513449) 
The population data is available in CSV format as WPDS_2020_data.csv[link](https://docs.google.com/spreadsheets/d/1CFJO2zna2No5KqNm9rPK5PCACoXKzb-nycJFhV689Iw/edit#gid=283125346). This dataset is drawn from the world population data sheet published by the Population Reference Bureau.[Link](https://www.prb.org/international/indicator/population/table/)


- **Article Quality estimation using ORES**
The predicted quality scores for each article in the Wikipedia dataset. We're using a machine learning system called ORES. This was originally an acronym for "Objective Revision Evaluation Service" but was simply renamed “ORES”. ORES is a machine learning tool that can provide estimates of Wikipedia article quality. The article quality estimates are, from best to worst:
FA - Featured article
GA - Good article
B - B-class article
C - C-class article
Start - Start-class article
Stub - Stub-class article

These were learned based on articles in Wikipedia that were peer-reviewed using the Wikipedia content assessment procedures.[link](https://en.wikipedia.org/wiki/Wikipedia:Content_assessment).  
For this particular project we are using the `articlequality`  model to predict the article quality.  

[ORES Documentation](https://www.mediawiki.org/wiki/ORES)  
[ORES Endpoint](https://ores.wikimedia.org/v3/)  
The results are stored at `A2_data/page_data_prediction.csv`.


### Data Storage
All data files that are used for the analysis are stored in the `A2_data`. Few of them are raw data dwonloaded from the source, whereas others are the files saved during processing to ensure reproducibility.  
 The Data file are:
 WPDS_2020_data.csv, page_data.csv -- (raw data)
 page_data_prediction.csv,wp_wpds_countries-no_match.csv,wp_wpds_politicians_by_country.csv --(implemented d

The final dataset "wp_wpds_politicians_by_country" has the following structure:


Column | Value | Description |
| ------------- |:-------------:| -----|
country| string|The country name|
article_name|string |The Wikipedia article title|
revision_id| numeric |The revision_id of the article's last edit|
article_quality|string| The quality class returned by the ORES service|
population|numeric| The population of the country|

### Code
All the code involved in this project are saved as a `Jupyter notebook` : `hcds-a2-bias.ipynb`.

The notebook was divided into 5  sections:
- Step 1: Getting the Article and Population Data
- Step 2: Cleaning the Data
- Step 3: Getting Article Quality Predictions
- Step 4: Combining the Datasets
- Step 5: Analysis
- Step 6: Results

These steps helps in answering the follwing questions:
- Top 10 countries by coverage: 10 highest-ranked countries in terms of number of politician articles as a proportion of country population
  Bottom 10 countries by coverage: 10 lowest-ranked countries in terms of number of politician articles as a proportion of country population
- Top 10 countries by relative quality: 10 highest-ranked countries in terms of the relative proportion of politician articles that are of GA and FA-quality
  Bottom 10 countries by relative quality: 10 lowest-ranked countries in terms of the relative proportion of politician articles that are of GA and FA-quality
- Geographic regions by coverage: Ranking of geographic regions (in descending order) in terms of the total count of politician articles from countries in each       region as a proportion of total regional population
- Geographic regions by coverage: Ranking of geographic regions (in descending order) in terms of the relative proportion of politician articles from countries in   each region that are of GA and FA-quality

### Libraries Used: 
- json
- matplotlib
- pandas
- requests



## License
The code is licensed under [MIT](LICENSE).
