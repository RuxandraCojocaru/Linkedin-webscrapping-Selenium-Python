# Linkedin web-scrapping with Selenium, in Python

## GOAL:
Automatically collect data from the Linkedin job-search page. The wanted data consists of:
+ the job description 
+ the job name 
+ the company name
+ the location
+ whether the job is remote/hybrid/on-site
+ whether it is full or part-time 
+ the position offered, from Entry-level/Associate/Internship
+ how many employees are working in the company 
+ the industry.


## STEPS TO FOLLOW:
#### 1. Create a Chrome web driver object
#### 2. Acces the link https://www.linkedin.com/jobs/search/?currentJobId=3325068125&f_E=1%2C2%2C3&f_TPR=r2592000&geoId=106670623&location=Romania&refresh=true&sortBy=DD

#### 3. Sign-in procedure: 
+ identify Sign In button
+ identify mail and password labels
+ write mail and password
+ press Enter

![Untitled 2](https://user-images.githubusercontent.com/101098099/221193613-ade4b08f-9ac7-4861-83d5-c6e1acb70210.gif)


#### 4. For all pages available (maximum 40), do the following: 
+ search by class for all the elements on page that contain job results
+ for each result, scroll a little in the list and click on the the job name
+ to the right a new panel will open, collect the wanted information from there, transforming text so that there are no commas
+ translate text into english if it is in romanian
+ write job description into txt file
+ write the remaining data into data.csv

![Untitled 2 (1)](https://user-images.githubusercontent.com/101098099/221197152-0d64e223-ef16-47ae-be5d-aff4e3eec422.gif)


#### 5. Taking care of Exceptions:
+ <b>NoSuchElementException</b>:  This means a job result is missing some data that I want. In this case I will skip over the result. In the console 'Data not complete, skipped.' gets printed.
+ <b>StaleElementReferenceException</b>:  This happens when a company's name is also a link, which throws the driver off track, following the link. There were only a few instances of this occurring. To solve this, I sent the driver back(), retook hold of the job results elements, and continued parsing the list starting with the one  next in line.
![image](https://user-images.githubusercontent.com/101098099/221198300-a2de1d40-15c3-4086-9a1a-475c00d4f531.png)
![rsz_221198300-a2de1d40-15c3-4086-9a1a-475c00d4f531](https://user-images.githubusercontent.com/101098099/221215113-3cb863ae-3141-4c12-a4c6-4bf468f466e2.png)


#### 6. Going to the next page
+ Identify the 10 existing page-buttons
+ If the page I am on is eighter in the first 8 or the last 8, simply click() on the corresponding button
+ If the page is numbered between 9-32, click the sixth button

![image](https://user-images.githubusercontent.com/101098099/221200802-353e8ceb-16bd-4462-bbbc-7c6c2fe8409e.png)
![Untitled 4](https://user-images.githubusercontent.com/101098099/221200874-ca176d26-34c3-4b2c-9b64-235dc8aec1d2.gif)
      

## RESULTS:
Collected 842 txt files with job descriptions, and the remaining variables were put in data.csv. The row number corresponds with the name of the txt file. This way, it will be easier to analyse the data in a later project.
