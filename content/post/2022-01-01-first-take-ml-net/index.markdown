---
title: 'First Take: ML.NET '
author: Andrew Borst
date: '2022-01-01'
slug: first-take-ml-net
categories:
  - Data Science
tags:
  - ML.NET
  - Regression
---

After perusing documentation on Microsoft's [ML.NET landing page](https://dotnet.microsoft.com/en-us/apps/machinelearning-ai/ml-dotnet), I was a bit nervous my data science skills are becoming unnecessary in today's automated model building world. I had just finished a capstone project in Regression as the final step in a certificate program from the MIT Applied Data Science Program so I had data ready for a regression model comparison. Let's use the [ML.NET Model Builder](https://dotnet.microsoft.com/en-us/learn/ml-dotnet/get-started-tutorial/intro) and take it for a spin with wrangled used car pricing data. 

The tutorial was easy to follow and within a few minutes the model builder was making used car price predictions. The final model was not as successful when compared to the models we developed in the data science capstone. However, I am pleased with the output since the generated model should be easy to improve and consumed in any application using Web API. Another option in ML.NET is to build your model in the machine learning framework of your choice (ie. Pytorch), convert it to the open standard format of [ONNX](https://docs.microsoft.com/en-us/azure/machine-learning/how-to-use-automl-onnx-model-dotnet), and consume in your .NET application. That workflow would be more productive since Jupyter Notebooks/RStudio allow interactive data wrangling and exploration.   


### Model Metrics 

| Model                           | Train R^2 &nbsp;   | Train RMSE |
|:----------------------          | :---------  | :--------- |
| ML.NET FastTweedieRegression &nbsp;    | 0.87         | 0.32       |
| Ridge Tuned                     | 0.96         | 0.18       |
| Random Forest Tuned             | 0.97         | 0.16       |


***

### Auto-generated C# code for the model  

![Generated Code](Model_builder_generated_code.jpg)
