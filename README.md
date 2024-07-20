# Data Analysis Project: Cleaning a Messy Job Postings Dataset using SQL.
### Hi every one in this project i use kaggle to download messy uncleaned dataset of job postings.
### After downloading the dataset from [Kaggle](https://www.kaggle.com/datasets/rashikrahmanpritom/data-science-job-posting-on-glassdoor), and opening it on Excel,
![1_ljZBLqWLSfyb-DRzvl_8Qw (1)](https://github.com/user-attachments/assets/692923ac-dd0c-4132-80ca-2b67f378dc85)
The dataset as a CSV file
<br>
### I then imported it into SQL Server.

![1_wuXiVkb_8hEoWbRUl4CePw](https://github.com/user-attachments/assets/13e2fddd-f487-42f3-8a72-2bec891ac522)
The dataset in SQL Server
### The goal of this cleaning exercise is to:
1- Remove the dollar signs, the letter ‘K’ and the ‘(Glassdoor est.)’ from the Salary Estimate column. We should be left with only numbers in that column.<br>
2- Get rid of the Duplicate values in the dataset.<br>
3- Get rid of the numbers in the Company name.<br>
4- Create new City and State columns from the Location column.<br>
5- The first thing I did was to remove the index column, ‘cos it’s as a result of direct importation from Python, and why would I need 2 index columns anyway? Also, working with spaced-out columns that need ‘[]’ irks me, so I renamed the columns to replace the spaces with underscores.<br><br>
![1_Td8-qI_-PTn2bosxktV-Xw](https://github.com/user-attachments/assets/bed00a33-e1d0-4b0e-a1b8-fca28084f5a5)<br>
As earlier mentioned, I removed the ‘$’ and ‘K’ from the Salary_Estimate column, and replaced them with ‘’<br>.

![1_nhtUX7EALKJlGi41zLG-ZA](https://github.com/user-attachments/assets/bd2f8a3a-0d69-458e-879c-110f6cf79746)<br>
Now for the removal of ‘(Glassdoor est.)’. After going through a bit of stress, I got 3 different ways to remove it. 3 ways, the same output. God! How I love SQL!<br>

![1_C8ZNDDCUQ1w1fq6rG2ZY1A](https://github.com/user-attachments/assets/7132eee6-94ad-400c-b616-35a0acf2bc7f)<br>
Then I added the new Salary_Estimate column to the table, trimmed the white spaces in the new column, and deleted the old column.<br>
![1_XUzafo7XOVXOtA0CEfkYkQ](https://github.com/user-attachments/assets/fb713312-e787-4216-acb6-7c67c1e21b4c)<br>
![1_bdx06Hdv53asS3-hduPEhQ](https://github.com/user-attachments/assets/8652a3ab-5d45-458a-b681-88bbff60fdfd)<br>
Time to get rid of the duplicate values. While going through the dataset, I noticed that some ‘duplicate values’ were not really duplicates. Some job postings had the same information in all the columns except the Salary_Estimate column.<br>
### Example<br>
![1_Kpc3su7Ef3Jc_9E4O-o0Fg](https://github.com/user-attachments/assets/a84a904f-10b4-4c3a-9a0c-cf0b28615680)<br>
Here, we see that we have 167 rows of duplicate values, but once we add the Salary_Estimate column to the mix, here’s what we get.<br>
![1_ITzYZAUoZv4gfgN2reWgBQ](https://github.com/user-attachments/assets/4efb8d26-b146-4924-9831-2f0f9374a6f6)<br>
Just 13 rows, to show that the other rows had a difference. So, I deleted these duplicate rows and got back 659 rows.<br>
![1](https://github.com/user-attachments/assets/966bfc8b-1262-4b36-8e13-b1af8a3c7243)<br>
Then I removed the numbers from the company name, added the new Company_Name column, and dropped the old column.<br>
![2](https://github.com/user-attachments/assets/bb9aa070-5137-43cb-a4f4-2fe2c739a60e)<br>
![3](https://github.com/user-attachments/assets/0c089b6c-a147-4809-b96f-8d7f5b87fa50)<br>
I broke out the City and State names from the Location column, then created new columns for Location_City and Location_State.<br>

![4](https://github.com/user-attachments/assets/52d68e70-eb4d-4db7-a685-548c0f4491da)<br>
![5](https://github.com/user-attachments/assets/486fc6af-9a38-4ebc-99d8-a1ba68551024)<br>
I also did the same for the headquarters.<br>
![6](https://github.com/user-attachments/assets/9c395e96-1d59-493c-a2bf-177986e33b4b)<br>
While doing this separation, I observed that some rows didn’t have any comma (,), thereby making them impossible to break out, and rendering their values NULL.<br>
![7](https://github.com/user-attachments/assets/f6edd8c6-9aca-46ef-a77c-f2e4214ef4d0)<br>
![8](https://github.com/user-attachments/assets/ad2049f0-1d1a-4fb5-87f4-70573c7b3211)<br>

So I decided to correct this by doing a self-join on the table, and replacing these NULL values with information from the Location column.<br>

Then I changed ‘-1’s in the Founded column to NULL, and then deleted unused columns.<br>

![9](https://github.com/user-attachments/assets/6086e330-5d2c-48a2-b90e-f44067d2bb83)<br>

![10](https://github.com/user-attachments/assets/f1b32620-2d60-4017-8c5d-aa93637eede5)<br>





