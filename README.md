# SystemDS
[![MIT License](https://img.shields.io/apm/l/atomic-design-ui.svg?)](https://github.com/tterb/atomic-design-ui/blob/master/LICENSEs)
![contributors](https://img.shields.io/github/contributors/TharunKumarReddy5/SystemDS.svg)
![codesize](https://img.shields.io/github/languages/code-size/TharunKumarReddy5/SystemDS.svg) 
![pullrequests](https://img.shields.io/github/issues-pr/TharunKumarReddy5/SystemDS.svg) 
![closedpullrequests](https://img.shields.io/github/issues-pr-closed-raw/TharunKumarReddy5/SystemDS.svg)

# System Investigation - SystemDS (Team Optimizers)

SystemDS (formerly known as SystemML was developed by IBM and then open-sourced in 2015. SystemDS is an open source ML system which supports end-to-end data science activities right from data cleaning, integration, feature engineering, model training, deployment and serving. It is platform and infrastructure independent, essentially running over CPUs, GPUs in local, distributed environments. It provides support for declarative languages like R and scripting languages like Python, compiles the code and can then run on local CPU/GPU, hybrid or distributed environments on Apache Spark. In contrast to existing systems - that either provide homogeneous tensors or 2D Datasets - and to serve the entire data science lifecycle, the underlying data model are DataTensors, i.e., tensors (multi-dimensional arrays) whose first dimension may have a heterogeneous and nested schema. Overall, it's a scalable Machine Learning system with distinguishing characteristics as follows:

1. Algorithm customizability via R-like and Python-like languages.
2. Multiple execution modes, including Spark MLContext, Spark Batch, Standalone, and JMLC.
3. Automatic optimization based on data and cluster characteristics to ensure both efficiency and scalability.

The latest version of SystemDS supports: Java 8+, Python 3.5+, Hadoop 3.x, and Spark 3.x, Nvidia CUDA 10.2 (CuDNN 7.x) Intel MKL (<=2019.x). For this document, we stick to naming the system SystemDS apart from diagrams, which could be referenced from old documents, hence the name would be SystemML. We will be covering some of the key features and/or characteristics of SystemDS as follows.

## Dependencies

Install the dependencies from the requirements.txt file using

    python -m pip install -r requirements.txt
    
## Repository Structure:
Here are the main folders in our github SystemDS repository:
```bash
.
├── CHANGELOG.txt
├── LICENSE
├── MANIFEST.in
├── Procfile
├── README.md
├── app
│   ├── main.py
│   ├── static
│   │   ├── css
│   │   ├── diagrams.png
│   │   ├── evalml.svg
│   │   ├── image_exp3.jpeg
│   │   ├── img.png
│   │   ├── sklearn.png
│   │   └── w3.css
│   └── templates
│       └── index.html
├── docs
│   └── MLPA.pptx
├── examples
│   ├── machine_learning_pipeline.png
│   ├── ml_pipeline_params.PNG
│   ├── ml_pipeline_params.pdf
│   ├── sample_models
│   │   ├── automl_pipeline.pkl
│   │   ├── ml_pipeline.pkl
│   │   └── ml_pipeline_income_classification.pkl
│   ├── sample_usage.ipynb
│   └── sample_usage.py
├── icons
│   └── tree.png
├── mlpipeline_analyzer
│   ├── __init__.py
│   │   ├── suggest
│   │   │	├── PipelineSuggest.py
│   │   │	├── __init__.py
│   └── visualizer
│       ├── PipelineDiagram.py
│       ├── PipelineNode.py
│       ├── __init__.py
├── requirements.txt
├── setup.py
├── tests
│   ├── test_app
│   │   └── test_main.py
│   └── test_mlpipeline_analyzer
│       ├── test_suggest
│       └── test_visualizer
├── uploads
│   └── sample-pipeline.pkl
├── .coveragerc
├── .gitignore
├── .travis.yml
├── .wsgi.py
```

## Code Examples:

**Code example_1**: Here in this part, the user uploads a model .pkl file which is then passed as an input to the PipelineDiagram class. The two ML pipeline diagrams are created using .show and .show_params:

    evalml_pipeline = joblib.load('models/automl_pipeline.pkl')
    a = PipelineDiagram(evalml_pipeline)
    a.show(title='Evalml ML Pipeline Diagram')
    a.show_params(title='Evalml Machine Learning Parameters Pipeline')

**Code example_2**: Here in this part, the suggest function generates the output for the varoius components of the model depending upon what the user specifies:

    b = PipelineSuggest()
    b.fit(data = df, response = 'survived', predictor_list = ['pclass','age','gender'], problem_type='binary', objective='auto', test_size=0.2)
    b.suggest(suggest_type='fe')
    b.suggest(suggest_type='model')
    b.suggest(suggest_type='all')    

## Authors
- [Tharun Kumar Reddy Karasani](https://github.com/TharunKumarReddy5)
- [Sravan Hande](https://github.com/sravankr96)
- [Rohit Lokwani](https://github.com/rohitl17)

![GitHub Contributors Image](https://contrib.rocks/image?repo=TharunKumarReddy5/SystemDS)


