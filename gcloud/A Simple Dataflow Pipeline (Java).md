
##  **GOOGLE AFRICA DEVELOPERS SCHOLARSHIP**
## **PHASE 2 PROJECT**
## **COURSE: Building Batch Data Pipelines on GCP**
## **Lab Title: Serverless Data Analysis with Dataflow: A Simple Dataflow Pipeline (Java)**

### Lab objectives

In this lab, you will learn how to write a simple Dataflow pipeline and run it both locally and on the cloud.

   * Setup of the Environment
   * Setup a Java Dataflow project using Maven
   * Write a simple pipeline in Java
   * Execute the query on the local machine
   * Execute the query on the cloud

 Therefore is further divided into ****5 Tasks****  
* ****Task 1****. Preparation - For this lab, you will need the training-data-analyst files and a Cloud Storage bucket.
* ****Task 2**** Create a new Dataflow project
* ****Task 3**** Pipeline filtering
* ****Task 4**** Execute the pipeline locally
* ****Task 5**** Execute the pipeline on the cloud

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

### Task 2. Create a new Dataflow project 
 The goal of this lab is to become familiar with the structure of a Dataflow project and learn how to execute a Dataflow pipeline. You will use the powerful build tool Maven to create a new Dataflow project.
 
 1. Return to the browser tab containing Cloud Shell. In Cloud Shell navigate to the directory for this lab:
 
 ```markdown
 cd ~/training-data-analyst/courses/data_analysis/lab2
```
2. Copy and paste the following Maven command:
```markdown
mvn archetype:generate \
  -DarchetypeArtifactId=google-cloud-dataflow-java-archetypes-starter \
  -DarchetypeGroupId=com.google.cloud.dataflow \
  -DgroupId=com.example.pipelinesrus.newidea \
  -DartifactId=newidea \
  -Dversion="[1.0.0,2.0.0]" \
  -DinteractiveMode=false
```
*  What directory has been created?

*  What package has been created inside the 
src directory?
3. Examine the Maven command that was used to create the lab code:
```mackdown
cat ~/training-data-analyst/courses/data_analysis/lab2/create_mvn.sh
```
* What directory will get created?
* What package will get created inside the src directory?

### Task 3. Pipeline filtering
1.  view the file with nano. Do not make any changes to the code.
```markdown 
cd ~/training-data-analyst/courses/data_analysis/lab2/javahelp/src/main/java/com/google/cloud/training/dataanalyst/javahelp/
nano Grep.java
```
this command automatically directs you to
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
3. 
gsutil is the command line for accessing and manipulating Cloud Storage from the
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

3. Verify that the dataflow is enabled
you can check this on [Dataflows](https://cloud.google.com/dataflow/docs/.) for more information
4. If necessary, Enable the API.

5. to view a list of all your dataflow jobs, type the following command into terminal
```markdown
     gcloud dataflow jobs list 
```
6. To view more information about your job
  ```markdown
  export JOBID=<X>
  gcloud dataflow jobs describe $Jobid
  ```

### Task 2. Create a new Dataflow project 
 The goal of this lab is to become familiar with the structure of a Dataflow project and learn how to execute a Dataflow pipeline. You will use the powerful build tool Maven to create a new Dataflow project.
 
 1. Return to the browser tab containing Cloud Shell. In Cloud Shell navigate to the directory for this lab:
 
 ```markdown
 cd ~/training-data-analyst/courses/data_analysis/lab2
```
2. Copy and paste the following Maven command:
```markdown
mvn archetype:generate \
  -DarchetypeArtifactId=google-cloud-dataflow-java-archetypes-starter \
  -DarchetypeGroupId=com.google.cloud.dataflow \
  -DgroupId=com.example.pipelinesrus.newidea \
  -DartifactId=newidea \
  -Dversion="[1.0.0,2.0.0]" \
  -DinteractiveMode=false
```
*  What directory has been created?

*  What package has been created inside the 
src directory?
3. Examine the Maven command that was used to create the lab code:
```mackdown
cat ~/training-data-analyst/courses/data_analysis/lab2/create_mvn.sh
```
* What directory will get created?
* What package will get created inside the src directory?

### Task 3. Pipeline filtering
1.  view the file with nano. Do not make any changes to the code.
```markdown 
cd ~/training-data-analyst/courses/data_analysis/lab2/javahelp/src/main/java/com/google/cloud/training/dataanalyst/javahelp/
nano Grep.java
```
this command automatically directs you to **/training-data-analyst/courses/data_analysis/lab2 then select the path javahelp/src/main/java/com/google/cloud/training/dataanalyst/javahelp/ and view the file Grep.java**

 Can you answer these questions about the file Grep.java?
>What files are being read?What is the search term?Where does the output go?

There are three apply statements in the pipeline:

>What does the first apply() do?

>What does the second apply() do?

>Where does its input come from?

>What does it do with this input?

>What does it write to its output?

>Where does the output go to?

>What does the third apply() do?

### Task 4. Execute the pipeline locally
1.In your terminal paste the following Maven command:
```markdown
cd ~/training-data-analyst/courses/data_analysis/lab2

export PATH=/usr/lib/jvm/java-8-openjdk-amd64/bin/:$PATH
cd ~/training-data-analyst/courses/data_analysis/lab2/javahelp
mvn compile -e exec:java \
 -Dexec.mainClass=com.google.cloud.training.dataanalyst.javahelp.Grep
```
2. The output file will be output.txt. If the output is large enough, it will be sharded into separate parts with names like: output-00000-of-00001. If necessary, you can locate the correct file by examining the file's time.
```markdown
ls -al /tmp
```
3. Examine the output file. Replace "-*" below with the appropriate suffix.
```markdown
cat /tmp/output-*
```
*Does the output seem logical?*

### Task 5. Execute the pipeline on the cloud
1. Copy some Java files to the cloud.
```markdown
gsutil cp ../javahelp/src/main/java/com/google/cloud/training/dataanalyst/javahelp/*.java gs://$BUCKET/javahelp
```
2. Edit the Dataflow pipeline in Grep.java. In the Cloud Shell code editor navigate to the directory /training-data-analyst/courses/data_analysis/lab2 and edit the file Grep.java.
```markdown 
cd ~/training-data-analyst/courses/data_analysis/lab2/javahelp/src/main/java/com/google/cloud/training/dataanalyst/javahelp
```
3. Replace Input and Output variables with your Bucket name. These must be the actual value, not the environment variable. Recall your Bucket name:
```markdown
echo $BUCKET
```
Replace the variables.
```markdown
String input = "gs://<YOUR-BUCKET-NAME>/javahelp/*.java";
String outputPrefix = "gs://<YOUR-BUCKET-NAME>/javahelp/output";
```
>Make sure that you changed the input and outputPrefix strings that are already present in the source code (do not copy-and-paste the entire line above because you will then end up with two variables named input).

Example lines before:
```markdown 
String input = "src/main/java/com/google/cloud/training/dataanalyst/javahelp/*.java";
String outputPrefix = "/tmp/output";
```
Example lines after edit (use your values):
```markdown
String input = "gs://qwiklabs-gcp-your-value/javahelp/*.java";
String outputPrefix = "gs://qwiklabs-gcp-your-value/javahelp/output";
```

4. Examine the script to submit the Dataflow to the cloud:
```markdown
cd ~/training-data-analyst/courses/data_analysis/lab2/javahelp
cat run_oncloud1.sh
```
What is the difference between this Maven command and the one to run locally?

5. Submit the Dataflow job to the cloud.
```markdown 
bash run_oncloud1.sh $DEVSHELL_PROJECT_ID $BUCKET Grep
```
Because this is such a small job, running on the cloud will take significantly longer than running it locally (on the order of 2-3 minutes).

Example completion of command line (do not copy):
```markdown 
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 01:50 min
[INFO] Finished at: 2018-02-06T15:11:23-05:00
[INFO] Final Memory: 39M/206M
[INFO] ------------------------------------------------------------------------
```
6. In order to monitor your jobs in dataflow
```markdown 
gcloud dataflow jobs list
```
7. Therefore, using the job ID you can run the describe function command to display more information about the job.
```markdown
export JOBID=<X>
gcloud dataflow jobs describe $JOBID
```
8. Examine the output in the Cloud Storage bucket.
```markdown
gsutil cp gs://$BUCKET/javahelp/output* .
cat output*
```

>In conclusion to this project we were able to get our hands on in 

   * Setting up of the Environment
   * Setting up a Java Dataflow project using Maven
   * Writing a simple pipeline in Java
   * Executing the query on the local machine
   * Executing the query on the cloud

***faithinGod***

***Jesus***
