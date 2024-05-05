# Milestone 1: perform exploratory data analysis (EDA) and frame your analysis

**You should thoroughly read through the entire assignment before beginning your work! Don't start the cluster until you are ready.**

**Code and data saved locally on the cluster will be lost when the cluster terminates. If you want to keep data, you must store it in S3. You must store the results (i.e. any plots, csv files) in the data folder of this repo.**

## Submission Details (80 points)

In this assignment you will start working with your Reddit data, decide on the scope of your project, and outline your 10 business goals.

### Before you begin

1. The data you will be using for this project is available in `s3://bigdatateaching` bucket under the `s3://bigdatateaching/reddit/parquet/submissions/` and `s3://bigdatateaching/reddit/parquet/comments/` prefixes.

1. The data is partitioned by year and month as shown below. This is a typically used partitioning scheme for data with a time attribute (see [this link](https://docs.aws.amazon.com/AmazonS3/latest/userguide/optimizing-performance.html) for more on S3 partitioning and optimization).

    ```    
    ├── comments
        ├── yyyy=2022
            ├── mm=01
            ├── mm=02
            ...
            ├── mm=12
        ├── yyyy=2023
            ├── mm=01        
            ...
            ├── mm=12
    ```

1. Just like you did for every assignment you will need to copy over the contents from the `s3://bigdatateaching/` bucket into a bucket in your own account. You DO NOT want to copy over all the data, you only want to copy the data for the subreddit(s) you are interested in working with. This is done through the `project_starter_script.ipynb` notebook provided in this repository. Follow instructions in that notebook to copy over the data into your account.

1. You will develop EDA notebook(s) using PySpark. All your Big Data analysis must be in PySpark. In this assignment you will examine the dataset, make transformations of the data, produce summary statistics and graphs of the data, and answer some of your business goals that only require exploratory work. You may choose to put all your work into one notebook or you may choose to separate it. Either is fine!

<p class="callout danger">
REMEMBER!!! All the output you are making MUST MUST MUST be small data. Can you make a graph of all 1 million+ rows of spark data? NO! You MUST MUST MUST take that big data and collapse it into reasonable data to put into a table or a graph. You should never collect more than ~10,000 rows back to you.
</p>

### Requirements

There are 3 parts to this assignment:

#### **Propose 10 different avenues of analysis for your data**

Make a project plan for your Reddit data with 10 topics that you plan on exploring. Any good data science project can be broken into at least 10 topics. These topics should vary in complexity to include exploratory, NLP, and ML ideas. Each entry of your 10 must include the "business goal" as well as the "technical proposal" for finding the answers. We want to see the "Executive Summary" view of the questions as well as the "Data Science" plans for making it happen.

> Example question based on the data science subreddit https://www.reddit.com/r/datascience/Links to an external site.:

> `Business goal`: Determine the most popular programming languages and the most effective programming languages used to conduct geospatial data analysis.  
    
> `Technical proposal`: Use NLP to identify posts that mention geospatial terms and one or more programming languages. Conduct counts of which programming languages are mentioned the most along with these geospatial terms. Analyze counts over time to check for major deviations and identify the leaders. Conduct sentiment analysis of the posts to assign positive or negative values to programming languages. Present findings for volume metrics and sentiment analysis for the top 5 programming languages to answer the "popular" and "effective" insights for geospatial analysis.

Each business goal must be 1-2 sentences while each technical proposal must be at least 3 sentences. There must be enough details about your plans so you can get feedback. **Include these business requirements in a markdown cell in the `project_eda` notebook**.

#### **Conduct your exploratory data analysis**

-   Report on the basic info about your dataset. What are the interesting columns? What is the schema? How many rows do you have? etc. etc.

-   Conduct basic data quality checks! Make sure there are no missing values, check the length of the comments, remove rows of data that might be corrupted. Even if you think all your data is perfect, you still need to demonstrate that with your analysis.

-   Produce at least 5 interesting graphs about your dataset. Think about the dimensions that are interesting for your reddit data! There are millions of choices. Make sure your graphs are connected to your business questions.

-   Produce at least 3 interesting summary tables about your dataset. You can decide how to split up your data into categories, time slices, etc. There are infinite ways you can make summary statistics. Be unique, creative, and interesting!

-   Use data transformations to make AT LEAST 3 new variables that are relevant for your business questions. We cannot be more specific because this really depends on your project and what you want to explore!

-   Implement regex searches for specific keywords of interest to produce dummy variables and then make statistics that are related to your business questions. Note, you DO NOT have to do textual cleaning of the data at this point. The next assignment on NLP will focus on the textual cleaning and analysis aspect.

-   Find some type of external data to join onto your reddit data. Don't know what to pick? Consider a time-related dataset. Stock prices, game details over time, active users on a platform, sports scores, covid cases, etc., etc. While you may not need to join this external data with your entire dataset, you must have at least one analysis that connects to external data.

-   If you are planning to make any custom datasets that are derived from your reddit data, make them now. These datasets might be graph focused, or maybe they are time series focused, it is completely up to you!

This assignment is worth 80 points. Thus, we expect you to put ***significant*** effort into this assignment. This assignment only requires the Jupyter notebooks.

#### **Create your website**

1. A basic Quarto based website scaffolding has been provided to you in the [`website-source`](../website-source/) directory. You can either use that or create your own (please create your own!).

1. The deployable website should be created in the [`docs`](../docs/) folder. You can do this by copying the content there manually or programatically (the Quarto website provided in [`website-source`](../website-source/) does that automatically).

1. You can host the website under [`georgetown.domains`](http://georgetown.domains/) OR on [GitHub pages](https://pages.github.com/) OR not host it anywhere just have it checked in as part of the [`docs`](../docs/) directory in your repository. Having a public website allows you to showcase your work to the world (prospective employers) but from a grading perspective all 3 options are equal.

1. **For this part of the project, you only need to fill out the EDA portion of your website which would include the 10 business questions and the exploratory analysis**.

## Submitting the Assignment

You will follow the submission process for all labs and assignments:

1. Add all your requested files to the GitHub assignment repo for the appropriate deliverable.
1. Submit a final commit message called "final-submission" to your repo. This is critical so that instructional team can evaluate your work. Do not change your GitHub repo after submitting the "final-submission" commit message.

Make sure you commit **only the files requested**, and push your repository to GitHub!

The files to be committed and pushed to the repository for this assignment are:

- `README.md`
- `.gitignore`
- `LICENSE`
- `code` (this would contain your Jupyter notebook(s))
- `docs`
- `website-source`
- `img/*`
- `data/*`

**Make sure that your `project_eda` notebook includes both a list of the business problems you are solving and the charts and summary tables as described above in the requirements section**.

## Grading Rubric

Many of the assignments you will work on are open-ended. Grading is generally holistic, meaning that there will not always be specific point value for individual elements of a deliverable. Each deliverable submission is unique and will be compared to all other submissions.

- If a deliverable exceeds the requirements and expectations, that is considered A level work.
- If a deliverable just meets the requirements and expectations, that is considered A-/B+ level work.
- If a deliverable does not meet the requirements, that is considered B or lesser level work.

All deliverables must meet the following general requirements, in addition to the specific requirements of each deliverable:

If your the submission meets or exceeds the requirements, is creative, is well thought-out, has proper presentation and grammar, and is at the graduate student level, then the submission will get full credit. Otherwise, partial credit will be given and deductions may be made for any of the following reasons:

Points will be deducted for any of the following reasons:

- Any instruction is not followed
- There are missing sections of the deliverable
- The overall presentation and/or writing is sloppy
- There are no comments in your code
- There are files in the repository other than those requested
- There are absolute filename links in your code
- The repository structure is altered in any way
- Files are named incorrectly (wrong extensions, wrong case, etc.)
