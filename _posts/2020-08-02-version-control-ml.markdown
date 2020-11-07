---
layout: post
title: "Version control your machine learning experiments"
date: 2020-08-02
tags: version-control
categories: machine-learning
excerpt_separator: <!--more-->
---
![Photo by Hani Bdran on Unsplash](/images/version_control_ml_1.jpg)

Nowadays, learning from data to gain business insights is common for almost every industry. These insights include— predictability, customer churn behavior, forecasting, etc.. Machine learning is the key player in generating these insights.

Building a good ML model requires a lot of experiments that involves multiple iterations of different algorithms over data, creating new variables, adding more data etc.. As the number of iterations grows, it becomes harder to keep track of these experiments.

In this article I will talk about a system to effectively version control machine learning project. I will also share some tools that will help you in easily implementing this system.

## In what scenarios you create a new version?
### 1. Data changes
Whenever there is a change in the modeling data, you create a new version of the model. ML models are trained on the modeling data. As the modeling data changes, model parameters will also change. You change the data when you do the following:

- When you capture more data.
- When you normalize/standardized data.
- When you create new variables — combination of variables, dummy variables, trends, etc..
- When you drop existing variables.
- When you fill missing data or drop missing data.
- Or any other way, in which some change happen in the data.

### 2. Model changes
Different modeling algorithms have different performance on the same training data. Each new algorithm you apply, you do a new experiment. This new experiment is a new version of the model.

Another scenario in which you create a new version, where you keep the data and the algorithm same, but, the model hyper-parameters changes.

## Why do you need to keep track of model versions?
In the modeling phase, a unique combination of training data and algorithm, will result in a single experiment. When you run different experiments, each experiment has different performance on the validation data. With each experiment, model performance may improve or degrade. Consider following table:

![Sample model performance](/images/version_control_ml_2.png)

Suppose, you have done 50+ experiments, and realize that one of the earlier experiments had better generalization than the current one. In the above table, we see that the model 4 has the better performance of both train and validation data. Because you did a lot of experiments, you don’t remember exactly what data and what algorithm you used in that model. In such cases, it becomes very difficult to reproduce the exact same results. That is why you need a versioning system with which you can easily keep track of all of the experiments without losing your older work.

## Model Versioning
Model versioning is a systematic approach to keep track of all your modeling experiments, so that, when you need it, you can retrieve it.

### Version Naming
As you saw in earlier section that a model changes either when data changes or algorithm changes or both. Given all this kind of changes, it is important to have a meaningful and consistent version naming system, so that, you know at a high level what is going on with a version.

![version nameing](/images/version_control_ml_3.png)

I use the four number system to specify a model number.

- First number tells me the project version. If I am working on it for the first time, I will assign x=1.
- Second number tells me the data version that I used for the modeling. Initially, I set y=1. During the modeling process, we may need to modify data multiple times. Each time I modify data, I increment the number y.
- Third number I use for the modeling algorithm. For each data version, I start it from 1. For example, for data version y, for the first algorithm I apply, I set z=1, for the second algorithm, z=2, etc.
- Forth number I use for the minor changes to model, like when algorithm hyper-parameters changes, it produces different results so different number for w in that case.

For example, if I am working on an ML project for the first time. I created one version of the modeling data and I applied logistic regression algorithm to that data. In this case, my complete version number will become 1.1.1.0. Now, if I change the algorithm to random forest for the same data, I will call my version 1.1.2.0. In case, I find better parameters setting for the random forest, I will call that version 1.1.2.1. This way, I can easily track my models.

## Versioning Tools
The aforementioned version system can be implemented using regular file system. For if your data is in CSV, you name your file as <filename><version>.csv. Similarly, code files can be managed in the same way.

But above approach starts to fail when you are dealing with a lot of files. An efficient approach to deal with versioning is to use dedicated software. There the two version control software that we can use for this purpose-
- [git][git-link] — for the code version control.
- [dvc][dvc-link] — for the data version control.

Both git and dvc are open-source software. For the complete usage information, checkout their documentation.

## Conclusion
You can use model versioning using the above system or you can define your own system. The important thing is follow a systematic approach while doing experiment so that it becomes easy to reproduce results when you need them.

Follow me on [Quora](https://www.quora.com/profile/Romee-Panchal). I write answers related to data science and machine learning.

[git-link]: https://git-scm.com/
[dvc-link]: https://dvc.org/
