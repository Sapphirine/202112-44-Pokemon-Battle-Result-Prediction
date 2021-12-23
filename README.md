# 6893-Big Data Analytics: Pokémon Battle Result Prediction

## Contents

1. [Introduction](#introduction)
2. [Methodology](#methodology)
3. [Datasets](#datasets)
4. [Quick Start](#quick-start)
5. [Contact us](#contact-us)

## Introduction

Project of the course EECS-6893-Big Data Analytics, the goal of the project is to predict battle result of Pokémon, analyze the importance of using machine learning algorithms, and build a Web UI to visualize the prediction of Pokémon battle result.

## Methodology

Machine learning algorithms: KNN, LDA, Random Forest, SVM.

Web UI: HTML, JSON, CSS, Django, Python.

## Datasets

Stored in the algorithm_code folder, see data descriptions in README.md under the same directory of datasets.

## Quick Start

The machine learning models code locates in the algorithm_code folder, the web UI code locates in the frontend_code folder. For the algorithm code, there are two kinds files with different prefixes shown as below:

#### Files Naming and corresponding Code

Differences of two kinds of files locate in: final_stats, list append (both in preprocess() function)

**"plain_" prefix files**: combine two Pokémons attributes into a vector as features, the actual input data structure into the model is:

```python
final_stats = ["HP1","Attack1","Defense1","Sp. Atk1","Sp. Def1","Speed1","Legendary1","HP2","Attack2",
                   "Defense2","Sp. Atk2","Sp. Def2","Speed2","Legendary2"]
```

```python
temp_list.append((first.tolist()+second.tolist()))
```

**"diff_" prefix files**: use the difference of two Pokémons attributes as features, the actual input data structure into the model is:

```python
final_stats = ["HP","Attack","Defense","Sp. Atk","Sp. Def","Speed","Legendary"]
```

```python
temp_list.append(((first-second).tolist()))
```

#### Switching whether to consider Pokémons types

4 situations in total: consider/ not consider Pokémons types，take difference of Pokémons attributes/combine Pokémons attributes into a vector , combining these two options so there are 2 x 2 situations. We use Cross Validation to find best parameters, then test with test data, to find the best model.

In preprocess() function, commenting these tow rows means not considering the Pokémons types: 

```python
first[1] = first[1] * adv_coefficient
first[3] = first[3] * adv_coefficient
```
#### Web app using instruction
First you need to organize the backend and frontend file into such directory in a project:  
-mysite/  
      -__init__.py  
  -asgi.py  
  -lr.sav  
  -setting.py  
  -urls.py  
  -views.py  
  -wsgi.py  
-static/  
  -css/  
    -style.css  
  -image/  
    -ps.png  
    -ps1.png  
    -question-mark.jpg  
-templates/  
  -index.html  
  -refresh.html  
  -refresh1.html  
  -refresh2.html  
  -result.html  
  -test.html  
-db.sqlite3  
-manage.py  

Then you run the command :  
python manage.py runserver  
An address should appear in your terminal, go to the address in your local machine's browser should take you to the web interface.  
There you can start playing around with the web app.

## Contact us

Wenpu Wang: ww2569@columbia.edu

Ruilin Fan: rf2756@columbia.edu

Zikai Zhu: zz2765@columbia.edu
