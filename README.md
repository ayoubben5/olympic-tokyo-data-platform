<h2>Details:</h2> 
For this Azure data plateform we gonna be using Azure's solution starting from <b>Data factory</b>, an integration service where you can build, schedule and manage data pipeline connected to multiple sources so we will use it to extract the data from its source and load it into our data lake storage in it’s raw format using <b>data lake gen 2</b> , we will then be performing transformation using pyspark in a <b>azure databricks</b> environnement to make the data ready for analytics but before that we will store the transformation into our data lake storage to be able to connect to <b>Azure synapse analystics</b>.

![image](https://github.com/ayoubben5/olympic-tokyo-data-platform/assets/60117038/948b151a-a0ce-41df-83a1-f7eddef088a2)
  

<h2> Data used: </h2> 
<p>The data we are going to use is the 2021 Tokyo Olympic data This contains the details of over 11,000 athletes, with 47 disciplines, along with 743 Teams taking part in the 2021(2020) Tokyo Olympics.
This dataset contains the details of the Athletes, Coaches, Teams participating as well as the Entries by gender. It contains their names, countries represented, discipline, gender of competitors, name of the coaches:</p>
<p><b>Athletes.csv</b> (PersonName:string , Country:string , Discipline:string )</p>
<p><b>coaches.csv</b> (Name:string , Country:string , Discipline:string, Event:string)</p>
<p><b>EntriesGenderbydiscipline.csv</b> (Discipline:string, Male:int , Female:int ,  Total:int)</p>
<p><b>Medals.csv</b> (Rank:int , Country:string , Gold:int, , Silver:int ,  Bronze:int ,  Total:int , Rank by medals:int)</p>
<p><b>Teams.csv</b> (TeamName:string, Discipline:string, Country:string, Event:string)</p>

# Project execution steps:
## Creating a storage account:

![image](https://github.com/ayoubben5/olympic-tokyo-data-platform/assets/60117038/92b55546-aa9d-493a-b6ba-c1bf93519fdd)

## Creating a container within the storage account:

![image](https://github.com/ayoubben5/olympic-tokyo-data-platform/assets/60117038/35ef5641-0f11-484e-952a-8b0038bc2881)


## Data Factory raw ingestion :

By creating our data pipeline and defining the source,the destination and the data format 

![image](https://github.com/ayoubben5/olympic-tokyo-data-platform/assets/60117038/ab3e0c1d-69d0-46af-8ffb-b525d29d6e6a)

![image](https://github.com/ayoubben5/olympic-tokyo-data-platform/assets/60117038/bdfec567-eff4-409c-821a-24546d41981b)

## Azure Databricks :
First thing we want to do is to create the infrastructure to run workloads from notebooks and spark jobs

![image](https://github.com/ayoubben5/olympic-tokyo-data-platform/assets/60117038/7ffbab3e-d320-49b0-a870-c15c5a8212d9)


### After creating our environment we will start creating our notebook to transform the data and load it into data lake gen 2 :

1. we will mount the cloud object storage to the workspace using familiar file paths relative to the Databricks file system
   ![databricks4 mounting](https://github.com/ayoubben5/olympic-tokyo-data-platform/assets/60117038/4c04460c-ec0d-44bd-8091-a1d027f89860)
   ![databricks5](https://github.com/ayoubben5/olympic-tokyo-data-platform/assets/60117038/387b9c24-667a-4bbb-93a4-6c0eb620c7ac)
2. we can start our transformation process by reading the raw data from our container:
   ![databricks6](https://github.com/ayoubben5/olympic-tokyo-data-platform/assets/60117038/32ea751a-8e50-4489-b383-b2bc15c910bb)

3. Performing aggregations
4. Storing the transformations and aggregations made :
![databricks8](https://github.com/ayoubben5/olympic-tokyo-data-platform/assets/60117038/e6bbe594-e3de-48d8-b57b-1d6077d066a4)

