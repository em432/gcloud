## Name: Emeje Othniel 
## Email Address: emejeothniel@gmail.com
##  **GOOGLE AFRICA DEVELOPERS SCHOLARSHIP**
## **PHASE 2 PROJECT**
## **COURSE: Building Batch Data Pipelines on GCP**
## **Lab Title: Serverless Data Analysis with Dataflow : MapReduce in Dataflow (Java)**

### Lab objective
* Preparation
* Identify Map and Reduce operations
* Execute the pipeline
* Use command line parameters


 Therefore is further divided into ****4 Tasks****  
* ****Task 1**** Preparation
* ****Task 2**** is to identify Map and Reduce operations
* ****Task 3**** Execute the pipeline
* ****Task 4**** Use of the command line parameters


### Setup of the Environment
* Open the Google cloud SDK and type in

```markdown
gcloud init 
```
* Selete your configuration as shown below
```markdown
Pick configuration to use:
 [1] Re-initialize this configuration [default] with new settings
 [2] Create a new configuration
Please enter your numeric choice:
```
after that your network authentication will be in progress and you will be taken to sign-up your google  account online *ensure you have a good data connection*  
```markdown
Network diagnostic detects and fixes local network connection issues.
Checking network connection...done.
Reachability Check passed.
Network diagnostic passed (1/1 checks passed).

Choose the account you would like to use to perform operations for
this configuration:
[1] XXXXXX@gmail.com (your given account registed with google)
[2] Log in with a new account
Please enter your numeric choice:

```
after that select your project or create your project
```
Pick cloud project to use:
 [1] aaaa-xxxx-123456 (assuming you have a project registered)
 [2] Create a new project
Please enter numeric choice or text value (must exactly match list
item): (Number)
```
and follow the given instruction and type **Y** if required
##### OR
You can list the active account name with this command:

```markdown
gcloud auth list
```
output
```markdown
Credentialed accounts:
 - <myaccount>@<mydomain>.com (active)
 ```
 Example output do not copy
 ```markdown
 Credentialed accounts:
 - google1623327_student@qwiklabs.net
```
You can list the project ID with this command:
```markdown
gcloud config list project
```

### Task 1. Preparation
Verify that the repository files are in Cloud Shell Editor
1. Clone the repository from the Cloud Shell command line:
```markdown 
git clone https://github.com/GoogleCloudPlatform/training-data-analyst
```
2. You should see the **training-data-analyst** directory, when you type
```markdown
ls
```
***this automatically list the directories.***

In the next steps you will verify that you have a Cloud Storage bucket

3. gsutil is the command line for accessing and manipulating Cloud Storage from the
command line. mb is the specific command for creating, or making, a bucket

```markdown
gsutil mb create
```
4. to verify your bucket have been created type in... ensure to replace this **<your unique bucket name (Project ID)**
```markdown
BUCKET="<your unique bucket name (Project ID)>"
echo $BUCKET
```
the **echo** function **automatically displays your unique bucket name**

5. Verify that the dataflow is enabled
you can check this on [Dataflows](https://cloud.google.com/dataflow/docs/.) for more information
6. If necessary, Enable the API.

7. to view a list of all your dataflow jobs, type the following command into terminal
```markdown
     gcloud dataflow jobs list 
```
8. To view more information about your job
  ```markdown
  export JOBID=<X>
  gcloud dataflow jobs describe $Jobid
  ```

### Task 2. Identify Map and Reduce operations

1.  In the Cloud Shell code editor navigate to the directory /training-data-analyst/courses/data_analysis/lab2/javahelp/src/main/java/com/google/cloud/training/dataanalyst/javahelp and view the file IsPopular.java in the Cloud Shell editor. Do not make any changes to the code.

Alternatively, you could view the file with nano. Do not make any changes to the code. 
```markdown
cd ~/training-data-analyst/courses/data_analysis/lab2/javahelp/src/main/java/com/google/cloud/training/dataanalyst/javahelp
nano IsPopular.java
```
>Normally, you would develop this Java code in an Integrated Development Environment such as Eclipse or IntelliJ (not in CloudShell)

Can you answer these questions about the file IsPopular.java?

>What getX() methods are present in the class MyOptions?

>What is the default output prefix?

>How is the variable outputPrefix in main() set?

>What are the key steps in the pipeline?

>Which of these steps happen in parallel?

>Which of these steps are aggregations?


### Task 3. Execute the pipeline

1. Copy and paste the following Maven command in your terminal
```markdown
export PATH=/usr/lib/jvm/java-8-openjdk-amd64/bin/:$PATH
cd ~/training-data-analyst/courses/data_analysis/lab2/javahelp
mvn compile -e exec:java \
 -Dexec.mainClass=com.google.cloud.training.dataanalyst.javahelp.IsPopular
```
***Note  It will take 4-5 mintues to complete the process.***

2. Examine the output file:
```markdown
cat /tmp/output.csv
```
you can check more information on [Maven](https://cloud.google.com/appengine/docs/standard/java/tools/maven)

### Task 4. Use command line parameters
1. Change the output prefix from the default value:
```markdown
  mvn compile -e exec:java \
  -Dexec.mainClass=com.google.cloud.training.dataanalyst.javahelp.IsPopular \
  -Dexec.args="--outputPrefix=/tmp/myoutput"
```
2. What will be the name of the new .csv file that is written out?
3. Note that we now have a new file in the /tmp directory:
    ```markdown
    ls -lrt /tmp/*.csv
    ```
    

>In conclusion to this project we were able to get our hands on in 

* Setting up the environment
* Identifying  Map and working with Reduce operations
* Executing the pipeline and finally
* the use of command line parameters

***faithinGod***

***Jesus***