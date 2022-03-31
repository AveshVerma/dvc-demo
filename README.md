# dvc-demo
This is just a demo for DVC

## 4.2.1 Data Versioning



DVC consists of commands you can run along with git to track large files, directories, or ML model files. Think "Git for data". It handle arbitrarily large files and directories with the same performance that you get with small code files.

First initialize Git

```shell
git init
```

Now initialize DVC

```shell
dvc init
```
Download the example dataset from [UC Irvine Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/bike+sharing+dataset)

Create a data Directory in your current working directory and keep your hour.csv dataset or any choice of your data in that directory

```
└── data
    └── hour.csv <-- or your dataset
```

Now as we get the data we will add it to **dvc tracking**
- for linux of macOS
```shell
dvc add data/hour.csv
```
- for Windows
```shell
dvc add data\hour.csv
```


As we will do this DVC will instruct us to run a git command

- for linux of macOS
```shell
git add data/hour.csv.dvc data/.gitignore
```
- for Windows
```shell
git add data\hour.csv.dvc data\.gitignore
```

After adding it we have to commit the changes
```shell
git commit -m "Add data"
```

Now we will have a **.dvc** file in data folder
It is kind of of metafile (link to our data)
We can see the content using **cat** command in linux or directly open as text file in windows

Now we want to push our data to remote storage.
So for this we can add DVC Remote(Google drive, s3 bucket etc..)

We will use Google drive for this demo

Login to google drive and create a folder anywhere in your google drive


If you dont have DVC Drive installed, run this command before your proceeed further -

```shell
pip install dvc[gdrive]
```

Get the Folder ID and run the below command

```shell
dvc remote add -d dvc_remote gdrive://Folder ID
```

> **Note** 
In case of GDrive for the first time it will ask for authentication, 
1. Once your run the aboove command it will provide a URL in the terminal.
2. Copy and paste the url in the browser and select your gmail id to sign in
3. Allow required access.
4. You'll land up on a page which will provide you an access code.
5. Copy and poste that access code in your terminal to configure gdrive for the first time for DVC remote data storage.

Now we will Commit and push

```shell
git commit .dvc/config -m "Configure remote storage"
dvc push
```
