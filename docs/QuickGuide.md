# Quick Guide

In the repository you will find a more detailed introduction on the technicalities of python, jupyter notebooks and git in the folder ''docs''. In the following, a quick installation guide of this repo and submission of exercises will be given.

## Cloning the Repository

Use either the https or ssh link to clone the repository on your local machine. Open a terminal, go to your preferred location and type either:
```
git clone https://github.com/leitgebc/StatisticsAndDataAnalysis2023.git
```
or 
```
git clone git@github.com:leitgebc/StatisticsAndDataAnalysis2023.git
```

Looking at your local directory now, a new directory called ''StatisticsAndDataAnalysis2023'' should have appeared. Go inside the directory and you will see the contents of the github repo.

## Updating the Repository Locally

Whenever there have been changes to the remote repository, it is necessary to update your local copy of it too. In case you have made no changes to the repo locally that could cause a conflict with the remote version, you can simple execute:
```
git pull
```
inside ''StatisticsAndDataAnalysis2023''. The repo should then be updated. Look at the terminal output however to see if any conflicts have occured. Treatment of conflicts is discussed in detail in the ''docs'' folder.

## Submitting Exercises

Place your exercise solution inside the ''submission'' folder on your local machine. Please make sure that the filename contains your name and the exercise sheet you are referring to.
Type then in the main directory:
```
git add submissions/<your filename>
```

Next you need to stage a commit. This is done by:
```
git commit -m <commit message>
```
Please always make sure you write a meaningful commit message, e.g. "submission of exercise sheet X by <name>".
Finally, you can move your changes to the remote repository by typing:
```
git push
```

## Using Conda

To make all the necessary libraries available, a convenient way is to use conda. A more detailed explanation is given [here](https://leitgebc.github.io/StatisticsAndDataAnalysis2023/CondaEnvironment.html). You'll have to create an environment equipped with Python and the needed packages. Every time you'd like to use the Jupyter notebooks, you need to activate the environment and start jupyter-lab or jupyter-notebook in your command line.



