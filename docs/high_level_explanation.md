# Project Overview — Cancer Gene Expression Classification

The data has tumour samples from 801 real cancer patients. For each sample, scientists measured how active each of ~20,000 genes is which is called gene expression profiling via RNA-Seq.

```
INPUT  →  A row of 20,531 numbers (one per gene), each representing
          how "loudly" that gene is turned on in a patient's tumour

OUTPUT →  Which of 5 cancer types this sample belongs to:
          BRCA (breast), KIRC (kidney), COAD (colon),
          LUAD (lung), PRAD (prostate)
```

## Why build a model for this?

This model is not for diagnosis since if we have the tumour sample we know where we got that from when collecting the sample itslef. So what is this model for then? The model will predict the cancer type from the RNA-seq and trends found from here can create the link required for researchers to discover which genes are more linked to each cancer type. That can then be used to discover drugs and work with treatments ect. This project does not aim to push new research, however, it works towards more verifying findings in other research papers and working towards the best machine learning practices for projects like this.

### The bigger picture

1. 20,531 genes from the sample's sequencing is input to a Random Forest model which will then classify the cancer type
2. After training the model can be interpreted to link each cancer type to the genes most heavily linked to it. To produce a ranked list of the most (correlated) genes per cancer type.

### Why being accurate is important for this problem
To derive that link of high correlation between the gene and cancer class is important, because based on this the findings of the set of genes being important will be derived. But it *must* be noted that "Important for the model" does not mean that "this gene causes cancer." A gene might be flagged as important because it's a reliable *marker* since its expression happens to differ between cancer types but  not because it caused the cancer.

## What are transcription factors? (from my layman's perspective)

- Genes have one specific job to carry out. If one gene causes an issue then the problem is not big, but when groups cause issues then there are problems like cancer.
- Transcription factors have the job of turning other genes on or off. If a gene breaks, the cell might get a little sick. But when a TF breaks it starts interacting incorrectly with thousands of genes. The tissues go rogue and become cancer. These transcription factors also happen to be genes.
- The goal is to build the model find the most important genes and then check if these genes are transcription factors.
- If the model flags a TF gene as having a strong correlation for a cancer type then that gives a finding that could be helpful in research of drugs ect.
