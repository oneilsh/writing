# 5 W's for Data Science

## What is data science?

This is a question I've been asking a lot lately--of myself and colleagues both here and elsewhere, from Statistics to Computer
Science, and more applied fields like Bioinformatics, Public Health, and Forestry. Partially this is because of a recent 
grant we've been funded, 
(Data Science for the Public Good)[https://workspace.oregonstate.edu/data-science-for-the-public-good],
where the plan is to build teams to work on data-driven problems with stakeholders in rural Oregon. There are several
educational components as well, where at least a working definition for our own use will be helpful.

It's no secret, however, that Data Science doesn't have a universally agreed-upon scope. It's a young field, and like
Bioinformatics draws from several other more established fields. Views differ significantly: ask a 
database administrator, statistician, computer scientist, and team manager what data science is, and you'll likely get 
four answers with as much difference as commonality. In my investigations, a few themes have emerged.

### Data

It's generally recognized that Data Science without data is like a book without pages: nonsensical. However, data 
comes with context, some domain or application. *Domain knowledge* is thus frequently considered a pillar of
data science; working with data without understanding its context can be dangerous or impossible. Moreso, solid 
domain knowledge boosts the effectiveness of methods--the best data science is often a creative process of matching
the right method to the right question, with the right data. 

While considered important, discussion of domain knowledge as part of data science usually stops there, or we run the risk 
of considering everything data science, save the theoretical. Still, I wonder if there's more that can be said here. Are
there general types of domain knowledge particularly important for data science we can point to? It's probably safe
to say a domain expert should be broadly aware of the types of data available and methods for data collection in their field.
What else?

Where opinions really diverge are in the potential methods and philosophies, and the relative importance of them.  


### Statistics, Machine Learning, Data Mining

Statistics is sometimes described as the "original" data science, and I don't disagree--the field predates computers, even 
Baggage and Lovelace's work in the early 1800's. Mathematical statistics brought scientific thinking to data analysis when 
datasets were small and very difficult to generate. 

The relationship of computer science to data, on the other hand, has grown
hand-in-hand with the availability of data, much of it gathered automatically with the help of computers. Data is abundant,
and the usual question is not how to get more, but how to efficiently analyze what's given. The traditional methods of
computer science are often not statistical in nature, nor are the data sets representative of a population. 
For [example](https://www.ncbi.nlm.nih.gov/pubmed/18936519),
given an MRI scan indicating the location of tumors, plan a radiation therapy treatment that minimizes
radiation exposure to healthy tissue and maximizes exposure for the tumor. Traditional computer science goes so far as to 
provide gaurantees on algorithm performance no matter the input, within defined bounds. Data distributions such as Gaussian
or Poisson are usually just not part of the equation. 

Where the two field meets are in making predictions utilizing, or describing patterns in, data that are
gathered from a larger population. Approaches here (usually classified as machine learning) have come from both Statistics
(e.g. mathematical regression models) and Computer Science (e.g. decision trees and neural networks). Both fields
evaluate their methods rigorously, but frequently do so in different ways. Confidence intervals and p-values are the order
of the day in statistics, whereas prediction performance on test data is primary in supervised machine learning. 
These aren't exclusive by any means, particularly as both fields continue to evolve. But it does
align with the "work with the data available, as bad or opaque as it may be" focus of CS. 

By contrast, I asked our Statistics department Chair, Lisa Ganio, for her thoughts on "data science." Her top-5 points
(paraphrased) illustrate a different philosophy:

1. Measurements always vary--In the real world we need to capture the precision of our measurements in order for measurements to be useful. 
We should understand the difference between accuracy and precision in measurements. 

2. Representation and Scope of Inference--data/measurements represent a group of things. We must understand the
definition of the group before we can draw conclusions from the data. This can be difficult, making it difficult to
determine what conclusions we can draw, potentially leading to big mistakes.

3. Variation can be understood visually--even simple tools like scatterplots reveal a host of information not captured
by summary statistics or more sophisticated methods. 

4. Having data in hand is not enough to know how to "analyze" it. The sampling scheme should effect how we analyze data.

5. Sampling variation matters--if we do the work again, we’ll get a different answer. It's important to distingish 
sampling variation from variation due to inherent processes. 

Here the focus on the sampling process--the data generation method--is front-and-center. Poor results in machine
learning often result precisely from working with data not representative for the task. Lack or bias in data is
well-known in machine learning, where methods like data augmentation and regularization try to alleviate these problems. 
Still, "found" datasets are common in data science and perhaps too often trusted, resulting in issues such as
[racial biases in facial recognition
systems](https://www.wired.com/story/best-algorithms-struggle-recognize-black-faces-equally/). While no longer as [trendy](https://trends.google.com/trends/explore?date=all&geo=US&q=%22data%20mining%22,%22machine%20learning%22)
as machine learning, "data mining" may still be a useful term.

On the other hand, many "less-statistical" methods have been designed to work specifically with such found, messy, or complex data, 
and have provided undeniable value despite questionable rigor. Some methods lend themselves well to more statistical
evaluation (e.g. [bootstrap-based confidence
intervals](https://machinelearningmastery.com/calculate-bootstrap-confidence-intervals-machine-learning-results-python/) for decision trees), 
while for other methods this is an [active area of research](https://pubs.acs.org/doi/10.1021/acs.jcim.8b00542). 


### Engineering

Machine learning and statistics may be top of mind for "data science," but far more happens behind the scenes when
turning data into insights. Data science is largely a programming-based exercise, and with that comes all of the
challenges of software development, with the additional challenges of data management, and increasingly the challenges
of "systems engineering" as the scale of data and methods continue to grow. 

<img src="https://i.imgur.com/jcbBJOf.png" width=40% />

Data science is in many ways a tool-oriented discipline, whether evaluating which type of database to use
in (e.g. MySql or MongoDB?), how to coordinate code and analyses across teams (GitHub or GitLab?), the programming
language of choice (R or Python?), or how to combine data, code, and visualizations (Jupyter Notebooks or RMarkdown?).


### Ethics, Equity, and Inclusion

With the growth of powerful methods and massive datasets, ethical considerations are an
[increasing](https://sdsi.stanford.edu/about/ethics-and-data-science) focus of data
science. The racially-biased facial recognition example above is one example (particularly given the potential use
of such systems by governments or others in power). Datasets containing personal information abound, despite regulations
like FERPA, HIPPA, GDPR, and others. 

Methods of data science make it easier than ever to deceive: "lies, damn lies, statistics, and machine learning." 
Deep learning in particular makes it easier than ever to [generate](https://en.wikipedia.org/wiki/Deepfake) 
realistic looking audio, images, and video, based on sample data. Some methods in data science are also resource-intensive. 
A recent [paper](https://arxiv.org/abs/1906.02243) analyzed the carbon footprint of developing a
natural-language processing application:


> The process can emit more than 626,000 pounds of carbon dioxide equivalent--nearly five times the lifetime emissions of the average
> American car (and that includes manufacture of the car itself). 

(Note, however, that this is for the development
(training) of the method; application of the trained result is quite efficient.)

With the huge diversity of skills and knowledge encompassed by "data science," teamwork is a strong value in the
community. Organizations such as [R-Ladies](https://rladies.org/), [PyLadies](https://www.pyladies.com/), and
[Code2040](http://www.code2040.org/) seek to reduce gender and racial gaps in data/computer science, and as mentioned
above data science recognizes the unique contributions of engineers, statisticians, software developers, and domain
experts. 

Finally, data scientists are often fervent open-source advocades, and the majority of data science software are
open-source (even many of those developed at for-profit companies, such as Tensorflow (Google) and RStudio (RStudio)), enabling free access to 
data science tools. 




