# Overview 

This folder contains all the scripts to run the data analysis.

# Scripts

0. [00_read_raw_data.R](./00_read_raw_data.R)
1. [01_clean_data.R](./01_clean_data.R)
2. [02_visualize_data.R](./02_visualize_data.R)
3. [03_analyze_data.R](./03_analyze_data.R)
4. [04_generate_final_result.R](./04_generate_final_result.R)

# Usage

To reproduce the data analysis, you can firstly clone the repo to the local computer. 

```
git clone https://github.com/UBC-MDS/DSCI_522_BlackFriday_Analysis.git
```

### Usage via shell

You then nevigate to the `root` directory of the project and run the following commands step by step.
```
# step 1 clean data
Rscript src/01_clean_data.R data/BlackFriday.csv data/BlackFriday_tidy.csv

# step 2 run exploratory data analysis
Rscript src/02_visualize_data.R data/BlackFriday_tidy.csv imgs

# step 3 analyze data via t-test and CLT-based estimation
Rscript src/03_analyze_data.R data/BlackFriday_tidy.csv results

# step 4 make plots to visualize analysis results
Rscript src/04_generate_final_result.R results imgs

# step 5 Render Markdown file to generate project report
Rscript -e "rmarkdown::render('./doc/Report.Rmd', 'github_document')"
```

Or, you can also run all scripts via a shell script.

```
bash run_all.sh
```

### Usage via Make

If you are using `Make`, you can run the following commands.
```
# To run all scripts and generate a final report 
make all
```

```
# To remove all figures and analyzed results
make clean
```

### Usage via Docker


For people with Docker installed on their machines, you can download a docker image of the project from Docker Hub.

```
docker pull mru4913/dsci_522_blackfriday_purchases_analysis
```

To run this analysis using Docker, you should clone/download this repository, as shown above, use the command line to navigate to the root of this project on your computer, and then type the following(Please fill in PATH_ON_YOUR_COMPUTER with the absolute path to the root of this project on your computer).

```
docker run --rm -v <PATH_ON_YOUR_COMPUTER>:/home/data_analysis mru4913/dsci_522_blackfriday_purchases_analysis make -C '/home/data_analysis' all
```

To clean all the file generated, you can run the following.
```
docker run --rm -v <PATH_ON_YOUR_COMPUTER>:/home/data_analysis mru4913/dsci_522_blackfriday_purchases_analysis make -C '/home/data_analysis' clean
```