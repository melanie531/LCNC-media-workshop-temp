# Part 1 - Data Wrangler

## Importing datasets from a data source (S3) to Data Wrangler

* Initialize SageMaker Data Wrangler via SageMaker Studio UI.
    * There are two ways that you can do this, either from the Launcher screen as depicted here:
    ![image](./img/image-1.png)
    * Or from the SageMaker resources menu on the left, selecting Data Wrangler, and new flow
    ![image](./img/image-1-1.png)
    ![image](./img/image-1-2.png)
* It takes a few minutes to load.
![image](./img/image-2.png)
* Once Data Wrangler is loaded, you should be able to see it under running instances and apps as shown below.
![image](./img/image-3.png)
* Next, make sure you have copied the data paths from the previous section, as you will need them in this section.
* Once Data Wrangler is up and running, you can see the following data flow interface with options for import, creating data flows and export as shown below.
![image](./img/image-4.png)
* Make sure to rename the untitled.flow to your preference (for e.g., join.flow)
* Paste the S3 URL for the tracks.csv file into the search box below and hit go.
![image](./img/image-5.png)
* Select the CSV file from the drop down results. On the right pane, make sure COMMA is chosen as the delimiter and Sampling is *None*. Hit *import* to import this dataset to Data Wrangler.
![image](./img/image-6.png)
* Once the dataset is imported, the Data flow interface looks as shown below.
![image](./img/image-7.png)
* Since currently you are in the data flow tab, hit the import tab (left of data flow tab) as seen in the above image.
* Import the second part file (ratings.csv) following the same set of instructions as noted previously.
![image](./img/image-8.png)

### Transform tracks dataset
* We firstly want to perform some data transformation using Data Wrangler. Let us walkthough how to perform different transformations using built-in and custom formula functionality in Data Wrangler. 
    * As the *genre* column in the tracks dataset is a categorical feature, we need to perform one-hot encoding to trasform this feature. 
    * Click on the tracks file transform block as show in the image below and select **Add transform**:
    ![image](./img/image-9.png)
    * Select **Add step** as shown below.
    ![image](./img/image-10.png)
    * In the **ADD TRANFORM** window, double click the option **Encode categorical**.
    ![image](./img/image-11.png)
    * Then on the **ENCODE CATEGORICAL** window, choose *One-hot encode* as the Transform type, *genre* as the input columns, and *Columns* as the output style. Click *Preview* and the output is shown as below:
    ![image](./img/image-12.png)
    * Click **Add** to add the tranform step to the flow. If you go back to the *Data Flow*, you can see the step has been added.
    ![image](./img/image-13.png)
    
* We also want to generate a new feature based on the danceability of the track. Danceability describes how suitable a track is for dancing based on a combination of musical elements including tempo, rhythm stability, beat strength, and overall regularity.
    * Click on the newly added **One-hot encode** step and select *Add transformation*:
    ![image](./img/image-14.png)
    * Select **Add step** and choose **Custom formula**.
    ![image](./img/image-15.png)
    * Copy and paste below formula and put **danceability** to the *Output Column*.
   
    <code>0.3\*valence + 0.1\*liveness + 0.1\*energy</code>
    
    ![image](./img/image-16.png)

    * Click **Preview** and **Add** the step to the flow.
    ![image](./img/image-17.png)

### Joining datasets - first join
* Given, we have imported both the part CSV files in the previous steps. Let us walk through on how to join these CSV files based on a common unique identifier column. 