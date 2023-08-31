---
layout: post
title: Week 2 Lab NoteBook
description: A Lab NoteBook Detailing this Week's Hack's
type: tangibles
courses: {'csse': {'week': 1}, 'csp': {'week': 2}, 'csa': {'week': 0}}
categories: ['C4.1']
---

# Lab Notebook

## Project 1: Cancer Predicting Logistic Regression Model

### Description
In this project, I aimed to create a cancer predicting logistic regression model using the `sklearn` library. The goal was to predict whether a given set of features indicates the presence of cancer or not.

### Main Module Used
- `sklearn`: Used for building the logistic regression model.

### Problem Faced
**Problem**: Trying to Import the Data
I faced an issue while trying to import the dataset for training and testing the logistic regression model. The dataset was stored in a CSV file, and I was encountering problems related to incorrect file paths and formatting.

**Solution**: I made sure to provide the correct file path to the `pd.read_csv()` function and double-checked the structure of the CSV file. After addressing these issues, I was able to successfully import the data.

---

## Project 2: Data Table of Boba

### Description
In this project, I created a data table named "Boba" using SQL queries. The table contains information about various types of boba tea.

### Main Module Used
- `pandas`: Used for querying and creating the data table.

### Problem Faced
**Problem**: Styling the Table using Style Tags
While creating the data table, I wanted to apply specific styling using HTML style tags to enhance the visual presentation of the table in Markdown. However, I was encountering difficulties in rendering the desired styles within the Markdown environment.

**Solution**: After researching Markdown's limitations, I realized that Markdown itself has limited support for advanced styling. Instead, I exported the data table to an HTML file using `pandas` and applied the desired styling there. Then, I embedded the styled HTML table directly into the Markdown document, which successfully displayed the table with the intended styles.

---

## Project 3: Python Quiz GUI using Tkinter

### Description
In this project, I developed a Python Quiz GUI application using the `Tkinter` library. The application presents multiple-choice questions to the user and evaluates their answers.

### Main Module Used
- `Tkinter`: Used for building the graphical user interface of the quiz application.

### Problem Faced
**Problem**: Styling the Guide
When designing the GUI, I wanted to style the user guide and instructions with custom fonts and colors to make them more appealing and readable. However, I was struggling to apply consistent styling across different `Tkinter` widgets.

**Solution**: I learned that `Tkinter` provides options to customize fonts and colors for each widget separately. To maintain consistency, I created a function that applies the desired styling parameters to all the relevant widgets, ensuring a uniform and visually pleasing appearance for the user guide and instructions.

---

## Project 4: Python Grade Predictor using Polynomial Regression

### Description
In this project, I aimed to build a Python Grade Prediction Machine Learning model using `sklearn`'s polynomial regression. The model would predict students' grades based on certain features.

### Main Module Used
- `sklearn`: Utilized for constructing the polynomial regression model.

### Problem Faced
**Problem**: Trying to Figure Out What Model to Use
At the outset of the project, I struggled to determine whether polynomial regression was the most suitable model for predicting grades. I was uncertain whether it would capture the underlying relationships between the features and the target variable effectively.

**Solution**: I conducted research on different regression techniques and their applicability to the problem of grade prediction. After analyzing the dataset and the potential non-linear relationships, I concluded that polynomial regression could be a suitable choice. To validate my decision, I performed exploratory data analysis and feature engineering to better understand the relationships, which ultimately supported the use of polynomial regression.

--- 

Remember that learning and problem-solving are key aspects of any project, and overcoming challenges is a valuable part of the journey. Each problem you encountered and solved contributes to your growth as a developer and a problem-solver.
