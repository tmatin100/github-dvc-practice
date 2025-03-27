# github-dvc-practice
Assignment for practicing GitHUB and DVC foundations.

Assignment: GitHub and DVC Foundations Practice
Objective
By the end of this assignment, you will be able to:
•	Set up and manage a GitHub repository.
•	Utilize Git for version control of your codebase.
•	Implement DVC for data versioning and management.
•	Collaborate effectively using branches and pull requests.
•	Understand the integration between GitHub and DVC in a data-centric project.
Prerequisites
•	Basic understanding of Git and GitHub.
•	Familiarity with command-line interfaces.
•	Python installed on your machine.
•	An active GitHub account.
•	Basic knowledge of DVC is helpful but not required.
Tools and Resources
•	Git
•	GitHub
•	DVC
•	Visual Studio Code or any other code editor
•	Sample dataset (provided in the assignment) - 

Assignment Structure
Part 1: Setting Up the GitHub Repository
1.	Create a New Repository on GitHub
o	Log in to your GitHub account.
o	Click the "+" icon in the top-right corner and select "New repository."
o	Name the repository github-dvc-practice.
o	Add a short description, e.g., "Assignment for practicing GitHub and DVC foundations."
o	Choose the repository to be public or private based on your preference.
o	Initialize the repository with a README.md file.
o	Click "Create repository."
2.	Clone the Repository Locally
o	Open your terminal or command prompt.
o	Navigate to the directory where you want to clone the repository.
o	Execute:
bash
Copy
git clone https://github.com/your-username/github-dvc-practice.git
o	Replace your-username with your actual GitHub username.
Part 2: Git Fundamentals
3.	Create a Python Script
o	Inside the cloned repository, create a new file named analysis.py.
o	Add the following Python code:
python
Copy
def greet(name):
    return f"Hello, {name}!"

if __name__ == "__main__":
    user_name = input("Enter your name: ")
    print(greet(user_name))
4.	Commit and Push Changes
o	Stage the new file:
bash
Copy
git add analysis.py
o	Commit the changes with a message:
bash
Copy
git commit -m "Add analysis script"
o	Push to GitHub:
bash
Copy
git push origin main
5.	Create and Merge a Branch
o	Create a new branch named feature/greeting:
bash
Copy
git checkout -b feature/greeting
o	Modify analysis.py to include a farewell message:
python
Copy
def farewell(name):
    return f"Goodbye, {name}!"

# Add the following lines below the greet function
print(farewell(user_name))
o	Stage, commit, and push the branch:
bash
Copy
git add analysis.py
git commit -m "Add farewell function"
git push origin feature/greeting
o	On GitHub, create a Pull Request to merge feature/greeting into main.
o	Review the changes and merge the Pull Request.
Part 3: Introducing DVC for Data Management
6.	Install DVC
o	If not already installed, install DVC using pip:
bash
Copy
pip install dvc
7.	Initialize DVC in the Repository
o	Navigate to your repository directory in the terminal.
o	Initialize DVC:
bash
Copy
dvc init
o	This command creates a .dvc directory and updates .gitignore.
8.	Add a Remote Storage for DVC
o	For this assignment, we'll use a local directory as remote storage.
o	Create a directory outside your repository to serve as remote storage, e.g., ../dvc-remote.
o	Add the remote to DVC:
bash
Copy
dvc remote add -d myremote ../dvc-remote
o	Push the DVC configuration to GitHub:
bash
Copy
git add .dvc/config .gitignore
git commit -m "Configure DVC remote storage"
git push origin main
9.	Track a Dataset with DVC
o	Download a sample dataset or create a dummy dataset. For this assignment, create a file named data/sample_data.csv with the following content:
csv
Copy
id,value
1,10
2,20
3,30
o	Add the dataset to DVC:
bash
Copy
dvc add data/sample_data.csv
o	This creates data/sample_data.csv.dvc.
o	Commit and push the changes:
bash
Copy
git add data/sample_data.csv.dvc .gitignore
git commit -m "Track sample dataset with DVC"
git push origin main
o	Push the data to the remote storage:
bash
Copy
dvc push
10.	Modify the Dataset and Track Changes
o	Update data/sample_data.csv by adding a new row:
csv
Copy
id,value
1,10
2,20
3,30
4,40
o	Update the DVC tracking:
bash
Copy
dvc add data/sample_data.csv
o	Commit and push the changes:
bash
Copy
git add data/sample_data.csv.dvc
git commit -m "Update sample dataset with new entry"
git push origin main
o	Push the updated data to the remote storage:
bash
Copy
dvc push
Part 4: Collaboration with Git and DVC
11.	Simulate a Collaborative Change
o	Clone the repository to a new directory to simulate another collaborator:
bash
Copy
git clone https://github.com/your-username/github-dvc-practice.git collaborator
o	Navigate to the cloned repository:
bash
Copy
cd collaborator
o	Pull the latest changes:
bash
Copy
git pull origin main
o	Pull the latest data using DVC:
bash
Copy
dvc pull
o	Make a change to analysis.py, e.g., add a function to calculate the sum of values from the dataset:
python
Copy
import pandas as pd

def sum_values():
    df = pd.read_csv('data/sample_data.csv')
    return df['value'].sum()

# Add the following lines in the main block
    print(f"Sum of values: {sum_values()}")
o	Install pandas if not already installed:
bash
Copy
pip install pandas
o	Stage, commit, and push the changes:
bash
Copy
git add analysis.py
git commit -m "Add sum_values function to analysis script"
git push origin main
o	Push any new DVC-tracked data if applicable.
12.	Integrate Collaborative Changes
o	Back in the original repository directory, pull the latest changes:
bash
Copy
git pull origin main
o	Pull the latest data using DVC:
bash
Copy
dvc pull
o	Verify that the new function works by running the script:
bash
Copy
python analysis.py

