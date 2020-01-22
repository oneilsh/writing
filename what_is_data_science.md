# What is Data Science?

"What is data science?" is a question I've been asking a lot lately -- of myself, via research and conferences, and in consersations with
colleagues here and elsewhere in Computer Science and Statistics, and more more applied fields like Bioinformatics, 
Public Health, and Forestry. 

Partially this is due to a recent grant we've been funded, 
[Data Science for the Public Good](https://workspace.oregonstate.edu/data-science-for-the-public-good) (DSPG).
DSPG aims to organize teams for data-driven projects in collaboration with stakeholders in rural Oregon. 
There are several educational components and connections to [Cooperative Extension](https://extension.oregonstate.edu/), 
where at least a working definition of the field for our own use is needed.

It's no secret however that data science, and even Data Science, doesn't have a universally agreed-upon scope. It's a young field, and like
Bioinformatics draws from several other more established fields. Views differ significantly: ask a 
database administrator, statistician, computer scientist, and team manager what data science is, and you'll likely get 
four answers with as much difference as commonality. In my investigations, a few themes have emerged.

### Data

*Data* is of course a crucial component of Data Science. However, data 
comes with context, some domain or application. *Domain knowledge* is thus frequently considered a pillar of
data science, because working with data without understanding its context can be dangerous or impossible. Moreso, solid 
domain knowledge boosts the effectiveness of methods: the best data science is often a creative process of matching
the right method to the right question, with the right data. 

While considered important, discussion of domain knowledge as part of data science usually stops there, or we run the risk 
of considering nearly everything (save the purely theoretical) Data Science. Still, I wonder if there's more that can be said. Are
there general types of domain knowledge that serve data science we can point to? It's probably safe
to say a domain expert should be broadly aware of the types of data available and methods for data collection in their field. Still, many
data are hiding even from domain experts -- on neglected FTP servers, in file cabinets, and in mysterious databases backing applications 
serving single offices. As a result, data science sometimes includes explicit discussion of "data discovery." 

Where opinions really diverge are in the potential data science methods and philosophies, and the relative importance of them.  


### Statistics, Machine Learning, Data Mining

Statistics is sometimes described as the "original" data science, and I don't disagree--the field predates ideas about 
automated computation, including even Baggage and Lovelace's work in the early 1800's. Mathematical statistics brought 
scientific thinking to data analysis when datasets were small and very difficult to generate. 

The relationship of computer science to data, on the other hand, has grown
hand-in-hand with the availability of data, much of it gathered cheaply and automatically with the help of computers. Data is abundant,
and the usual question is not how to get more, but how to efficiently analyze what's already there. The traditional methods of
computer science are often not statistical in nature, nor are the data sets representative of a population. 
For an [example](https://www.ncbi.nlm.nih.gov/pubmed/18936519),
given an MRI scan indicating the location of tumors, we might desire to plan a radiation therapy treatment that minimizes
exposure to healthy tissue and maximizes exposure for the tumor. Traditional computer science goes so far as to 
provide gaurantees on algorithm performance no matter the input, within defined bounds. Distributions such as Gaussian
or Poisson are usually just not part of the equation. "Online algorithms" represent an extreme in this area; here a method
needs to make a decision or prediction based on data seen thus far, but the decisions must be made as data are revealed incrementally. 
In designing such a method, a computer scientist may go so far as to hypothesize an *adversary* generating data specifically to thwart
the chosen method, with the goal of designing an unthwartable method (measured by the performance of the method compared to an oracle
who knows all the data in advance). 

Where the two fields meet are in making predictions utilizing, or describing patterns in, data that are
gathered from a larger population, a.k.a. "machine learning." Approaches here have come from both Statistics
(e.g. mathematical regression models) and computer science (e.g. decision trees and neural networks). Both fields
evaluate their methods rigorously, but frequently do so in different ways. Confidence intervals and p-values are the order
of the day in statistics, whereas prediction performance on test data is primary in supervised machine learning. 
These aren't exclusive by any means, particularly as both fields continue to evolve and integrate. But it does
align with the "work with the data available, as bad or opaque as it may be" focus of CS. 

By contrast, I asked our Statistics department Chair, Lisa Ganio, for her thoughts on "data science." Her top-5 points
(paraphrased) illustrate a very different philosophy:

1. Measurements always vary: In the real world we need to capture the precision of our measurements in order for measurements to be useful. 
   We should understand the difference between accuracy and precision in measurements. 

2. Representation and Scope of Inference: Data/measurements represent a group of things. We must understand the
   definition of the group before we can draw conclusions from the data. This can be difficult for some data, potentially leading to 
   big mistakes.

3. Variation can be understood visually: Even simple tools like scatterplots reveal a host of information not captured
   by summary statistics or more sophisticated methods. 

4. Data alone is not enough: Having data in hand is not enough to know how to "analyze" it. The sampling scheme should effect how we analyze data.

5. Sampling variation matters: If we do the work again, we’ll get a different answer. It's important to distingish 
   sampling variation from variation due to inherent processes. 

Here the focus on the sampling process -- the data generation method -- is front and center. Poor results in machine
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

Machine learning and statistics may be top of mind for "data science," but far more is involved in
turning data into insights. Data science is heavily programming-oriented, and with that comes all of the
challenges of software development and maintenance, with the *additional challenges* of data and analysis management (with
e.g. databases and parallel processing frameworks). 

As the scale of data and methods continues to grow, increasingly these challenges issues evolve into "systems engineering,"
or the more focused [data engineering](https://www.oreilly.com/radar/data-engineers-vs-data-scientists/), depending
on one's perspective.

<img src="https://i.imgur.com/jcbBJOf.png" width=40% />

Large computing clusters aside, data science is a tool-oriented discipline. Decisions must be made about which type of database to store data in
(e.g. MySql, MongoDB, or none?), how to coordinate code and analyses across teams (GitHub, GitLab, other?), the programming
language(s) used (R, Python, Julia, Go, ...?), libraries to use (Keras or PyTorch?), how to organize 
data, code, and visualizations (Jupyter Notebook? RMarkdown?), how to present results (the same Jupyter Notebook? Static report? Interactive dashboard?),
and how to make the whole project reproducible (Docker? Conda?).

Even if we consider data engineering an independent subfield, real data analysis necessitates consideration of tools and systems. Given
the primacy of data in data science, there's a strong case for data science to encompase these topics as well.


### Ethics, Equity, and Inclusion

With the growth of powerful methods and massive datasets, ethical considerations are an
[increasing](https://sdsi.stanford.edu/about/ethics-and-data-science) topic data
science. The racially-biased facial recognition [systems](https://www.wired.com/story/best-algorithms-struggle-recognize-black-faces-equally/) above are one 
example (particularly given the potential use
of such systems by governments or others in power). Datasets containing personal information abound despite regulations
like FERPA, HIPPA, and GDPR, meaning data scientists must occasionally consider both the ethical and legal implications of their work.

Methods in data science make it easier than ever to deceive: "lies, damn lies, statistics, and machine learning." 
Deep learning in particular enables easy [generation](https://en.wikipedia.org/wiki/Deepfake) 
realistic audio, images, and video based on sample data. 

Some methods in data science are also resource-intensive. 
A recent [paper](https://arxiv.org/abs/1906.02243) analyzed the carbon footprint of developing a
natural-language processing application:

> The process can emit more than 626,000 pounds of carbon dioxide equivalent--nearly five times the lifetime emissions of the average
> American car (and that includes manufacture of the car itself). 

(Note, however, that this is for the development
(training) of the method; application of the trained result, "Hey Siri, what's the weather in New York?," is quite efficient.)

With the huge diversity of skills and knowledge encompassed by "data science," teamwork is a strong value in the
community. Organizations such as [R-Ladies](https://rladies.org/), [PyLadies](https://www.pyladies.com/), and
[Code2040](http://www.code2040.org/) seek to reduce gender and racial gaps in data/computer science, and as mentioned
above data science recognizes the unique contributions of engineers, statisticians, software developers, and domain
experts. 

Finally, data scientists are often fervent open-source advocades, and the majority of data science software are
open-source, including many of those developed at for-profit companies such as Tensorflow (Google) and RStudio (RStudio). 

