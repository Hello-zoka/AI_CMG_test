# Evaluation for Commit Message Generation - Coding Challenge

In the `AI_CMG_test.ipynb` notebook, you can find my solution for task 2: "What Makes a Good Commit Message?"

## Description

I used a pre-trained BERT model and tokenizer to analyze commit messages and their labels, which indicate which questions were answered in the commit text. Then, I attempted to classify commits from [NNgen](https://github.com/Tbabm/nngen/tree/master/data).

The results were quite promising. We achieved a model with a validation loss of approximately `~0.63`, which is pretty good considering that we used "out of the box" tools and a relatively small training dataset.

## Result analysing

After running the classifier on NNgen commits, I began to question whether the model's predictions were good enough. My thoughts on this matter are somewhat mixed. On one hand, it appears that the model is quite precise when it comes to determining whether nothing was answered or everything was answered. However, there are some errors in understanding whether the question "Why?" was truly addressed. I find it challenging to determine this as well, even since I'm human(probaly?). In my opinion, information about why a commit happened is sometimes genuinely included in its context: changes in files, the type of fix, the issue it's tracked for, and more. Conversely, sometimes such an answer may not even be needed (A samurai has no goal, only path xD). So, there are some commits which are pretty understandle(which == to good), but not answering such questions. Moreover, when looking at a single-line commit, it's often difficult to classify its quality, due to lack of context.

However, if we assume that the best commits answer both questions, the good ones answer at least one of them, and the bad ones answer none, we can conclude that we've identified approximately 1/3 of the best commits, 2/3 of the good commits, and only a few of the bad ones in this example dataset. This seems reasonable since it reflects what people often create in practice. Additionally, some results may fall into a gray area between the nearest categories. The worst commits typically have a more technical character and may not convey much to individuals who are not familiar with the project, which were covered by our classifier(as my eyes could value it).


## How to run

To begin, follow these steps:

1. Clone or download the Jupyter Notebook.
2. Make sure to use GPU for calculations(or be ready to wair ~etirnity).
3. Add a labeled dataset for commit messages, which should include the following information:
    - `message` - the commit message text.
    - `label` - a number from 0 to 3, representing whether a question was answered in the commit message, as follows:
        - `0` indicates that a commit message contains both "Why" and "What". 
        - `1` indicates that a commit message contains neither "Why" nor "What".
        - `2` indicates that a commit message contains "No What".
        - `3` indicates that a commit message contains "No Why".
4. Add files with commit texts, each separated by a newline.
5. Specify the paths to all files in all the necessary places in the code (read the comments for guidance).
6. Just run it!

**P.S.** This was one of my first experiences with training models with more than zero lines of code, so some parts of the code were inspired by ChatGPT. I am for aby feedback and eager to learn to improve my skills at this area.


