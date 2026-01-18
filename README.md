[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-22041afd0340ce965d47ae6ef1cefeee28c7c493a6346c4f15d667ab976d596c.svg)](https://classroom.github.com/a/0F6Dg6d7)
## Tutorial-6: GitHub Action

## Student Info:
1. Matric Number:295226
2. Name:ALIA MAISARA BINTI MOHAMMAD SABUDIN


## 🎯 Objective
By the end of this tutorial, students should be able to:
1. Explain the difference between workflow, job, and step
2. Create a simple GitHub Actions workflow
3. Observe how jobs run in parallel, and steps run sequentially
4. Modify the workflow to add a job dependency


## Instructions

### Part A: Repository Setup
1. Create a new GitHub repository
- Name: github-actions-lab
- Public repository
- Add a README file

2. Inside the repository, create this folder:
```
.github/workflows/
```
3. Create a file named:
```
lab-actions.yml
```

### Part B: Create Your First Workflow
Paste the following code into `lab-actions.yml`:
```yml
name: Workflow vs Job vs Step Lab

on: push

jobs:
  job-one:
    runs-on: ubuntu-latest
    steps:
      - name: Step 1 - Print message
        run: echo "This is Step 1 in Job One"

      - name: Step 2 - Print another message
        run: echo "This is Step 2 in Job One"

  job-two:
    runs-on: ubuntu-latest
    steps:
      - name: Step 1 - Print message
        run: echo "This is Step 1 in Job Two"
```
>Commit and push the file.

### Part C: Observe the Execution
1. Go to Actions tab in GitHub
2. Click the running workflow
3. Observe:
   - The workflow name
   - Two jobs running in parallel
   - Steps executing top to bottom inside each job

### Part D: Add Job Dependency
Now modify job-two so it runs after job-one. Update the file:
```yml
job-two:
  needs: job-one
  runs-on: ubuntu-latest
  steps:
    - name: Step 1 - Print message
      run: echo "Job Two runs after Job One"
```
>Commit and push again.

### Part E: Compare Results
You should now observe:
- job-one runs first
- job-two waits until job-one finishes


## Submission
Screenshot of:
1. Workflow page
2. Job execution view

## Results

### Part C: Before Dependency

When the workflow was triggered by a push, two jobs (`job-one` and `job-two`) executed in parallel. Each job ran its steps sequentially from top to bottom. This demonstrates the difference between jobs (parallel execution) and steps (sequential execution).

**Screenshot 1 (Workflow page):**
<img width="1918" height="873" alt="Screenshot 2026-01-18 200533" src="https://github.com/user-attachments/assets/e444dd3a-83b2-4f03-864c-7bd3df9ddbda" />


**Screenshot 2 (Jobs running in parallel):**
<img width="1914" height="742" alt="Screenshot 2026-01-18 201236" src="https://github.com/user-attachments/assets/393f74a5-8e72-4203-91fe-735e34d22993" />


---

### Part E: After Dependency

After adding `needs: job-one`, `job-two` became dependent on `job-one`. Therefore, `job-one` ran first, and `job-two` waited until `job-one` finished before starting. This demonstrates job dependency in GitHub Actions.

**Screenshot 3 (Job dependency view):**
<img width="1919" height="743" alt="Screenshot 2026-01-18 201512" src="https://github.com/user-attachments/assets/64e5f1a6-014c-4dba-bddd-4ae654c1119b" />







