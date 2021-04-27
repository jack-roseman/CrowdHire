Crowd Hire README

Collect and redact resumes (work required: 2)
-Collect resumes through piazza posts for our classmates, through public resume lists, social outreach (facebook), and/or club resume lists. We will have to redact personal information, such as name, email address, and phone number, from the resumes, once acquired. 

Create HIT templates (work required: 3)
-We have the mockup, but need to convert it into a usable Mechanical Turk HIT. It will take four resumes, one being a gold standard resume and the other three being distributed from the remaining resumes. For each resume the worker will answer a few basic questions such as what industry the person has worked in, years of experience, education, and skills.

Create gold standard answers (work required: 2)
-Answer the questions optimally for some number of resumes (to be determined) in order to generate proper gold standard questions for the HITs.

Collect data from crowd (work required: 1)
-Properly distribute the resumes into batches so that they may be put into groups of four to make the HITs available to publish.
-Publish HITs with the resumes we have collected on Amazon Mechanical Turk.

Aggregate data and quality control (work required: 4)
-Filter for quality control based on gold standard
	-If worker fails gold standard, then his work will not be included in aggregation
-Determine majority aggregated questions to generate results for each resume. Depending on the question, this may be a simple average of numerical data or could be a more complicated operation done on a set of words. Present this data in the desired fashion.

Analyze data (work required: 4)
-Calculate metrics and final results based on data collected by the crowd. Depending on requirements this could be a presentation of data in a usable format, a ranking of resumes based on given requirements, or labeling resumes with certain keywords so that they are easily searchable for an interested employer.

Total points overall: 16
________________________________________________________________________________________________________

Quality Control and Aggregation Input/Output Description: A files can be found in "Sample InputOutput QC and Aggregation" Excel file (see sheet names for each part).

Quality Control Input: 

After collecting our data from our MTurk output, we have a csv file with question type as columns and data for each HIT in the rows. The columns include preliminary data, such as HIT ID, Worker ID, question names. Additionally, we have data containing a specific workers’ answers to the questions. For Q1, we indicate a selected response by a numerical value inputted into the respective cell to represent number of years of experience. For Q2 and Q3, the answers are selected from a drop-down menu, which are represented as single string answers (highest degree achieved and position held). Similar to Q1, Q4 indicated selected skills inputted into the respective cells as a boolean. Additionally, the remaining columns represent each worker’s answers to the questions in the Gold standard resume.

Each worker’s responses for a hit are recorded in an individual row. Each row contains one HIT where a worker analyzes three resumes and a gold standard. Since we created fake data and we do not have actual MTurk output, we are missing columns, such as time started, date approved, etc. for each HIT.

Quality Control Output:

This file is the exact same as the input, except it contains a column “GS pass?” that indicates whether or not the worker, completing a specific HIT, passed the gold standard resume. Furthermore, the workers’ answers to the Gold standard questions are removed. “GS pass?” (boolean) is determined by comparing each workers’ answers in the GS section of the QC input to the correct answers (which we will create).

Aggregation Input:

This file contains identical columns, rows, and data as the QC output, however, the rows that contained FALSE for the gold standard are not included in this input (we did not include any such workers in our fake data). 

Aggregation Output:

This file compiles the answers for 3 hits (three different workers) of a specific resume into an aggregated answer for each question of that resume. For Q1, if there is a majority value among the three answers for years of experience, we take the majority as the aggregate output. If not, we use the average of the three answers. For Q2 and Q3, we use the majority value for the highest degree and most recent job title. For Q4, we again use the majority value of booleans to determine the aggregated responses for each skill in each resume.


Quality Control Module:
The quality control module handles filtering the dataset down into only quality acceptable results as defined by our flow chart. As input it takes in the mechanical turk responses that were modeled in the sample QC input file. From there we mark every worker response as having passed the quality control questions. This is done by checking if the quality control worker responses match their ground truth answers. In terms of further work, as long as we pass the answers to the quality control resume from the raw dataset we should not need to do much any further. The biggest changes will actually the names of the columns, as I am not certain these will be the correct columns names of the real mechanical turk data. For this reason I made this part easy to modify.

Aggregation Module:
The file BasicAgg.ipynb handles the aggregation module of the project in a basic fashion. It takes in a file path as input to the processInput function in order to run. The processInput function takes in the results of the quality control module (a csv file) and creates a pandas dataframe for it. The dataframe is then broken down so that there are seperate rows for each of the three resumes in each HIT. The three dataframes that result from this broken down input are passed to aggregateInput. Aggregate input combines the three dfs into one again and performs basic aggregation. For each question in each resume it takes the mode of the question responses to be the aggregated response. It does not do any backup aggregation besides taking the majority, so further work may be required to add a second aggregation function just in case.

________________________________________________________________

Instructions for our HIT:

Please click [HERE](https://workersandbox.mturk.com/projects/3NAD71TD7UBSLV16NWKHYS7FDY42LY/tasks/366FYU4PTGP7R5XTCBT7ABH8RM0EK1?assignment_id=3MTMREQS4VIYJC8SBMFQRNGSQB0WA2&auto_accept=true) to access the link.

In order to reduce the burden on HR teams and recruiters and decrease bias in the recruiting process, we think we can leverage crowdsourcing in order to rank resumes of candidates. In this HIT, we ask that workers use their intuition and reading skills in order to rate resumes using the following form. Please read the resume carefully and pay attention to detail. See step by step instructions below:

Please read the provided resume, taking mental notes of the years of experience, most recent job position, and skills.
Once you have completed reading the resume, please look at the questions provided and fill out the form using the information you have from the resume. 
If a certain skill is not listed on the resume, please do not list it on the form. 
If the industry is not listed in the form, please use the “Other” option. If there are multiple not listed, please choose the one where the person worked the longest.
If the resume has information on years of experience in multiple industries, please list all the industries that you see.
For the most recent job title, please copy and paste the position title as specified on the resume.
Once you have completed all of the questions, please click “Submit.” If you do not answer all of the questions, your attempt will not be accounted for.

Instructions for Resume Collection:

In order to remove some of the biases that come about during the recruiting process, we hope to collect resumes with all personal information (i.e., name, address, number, etc.) redacted. As a result, we need people to redact such information before sending us their resumes.

Open up your resume as a PDF in Acrobat, Preview or another PDF viewer
Using your PDF viewer, highlight the information that you wish to redact.
Go the “tools” option and select the “redact” tool
If you have a Mac that has not been updated to BigSur, you will simply need to add a solid black box on top of the information you wish to be hidden.
Click save
Then upload the redacted resume [HERE](https://tinyurl.com/resume213)

If you have any issues/questions, please reach out to theog26@wharton.upenn.edu

________________________________________________________________


