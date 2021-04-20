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
