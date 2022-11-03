
# Variant Spark

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Faehrc%2FVariantSpark-Azure-deployment%2Fmaster%2Fazuredeploy.json)

[![Visualize](https://raw.githubusercontent.com/Azure/azure-quickstart-templates/master/1-CONTRIBUTION-GUIDE/images/visualizebutton.svg?sanitize=true)](http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2Faehrc%2FVariantSpark-Azure-deployment%2Fmaster%2Fazuredeploy.json)

_variant-spark_ is a scalable toolkit for genome-wide association studies optimized for GWAS like datasets.

Machine learning methods and, in particular, random forests (RFs) are a promising alternative to standard single SNP analyses in genome-wide association studies (GWAS). RFs provide variable importance measures to rank SNPs according to their predictive power.
Although there are number of existing random forest implementations available, some even parallel or distributed such as: Random Jungle, ranger or SparkML, most of them are not optimized to deal with GWAS datasets, which usually come with thousands of samples and millions of variables.

_variant-spark_ currently provides the basic functionality of building random forest model and estimating variable importance with mean decrease gini method and can operate on VCF and CSV files. Future extensions will include support of other importance measures, variable selection methods and data formats.

_variant-spark_ utilizes a novel approach of building random forest from data in transposed representation, which allows it to efficiently deal with even extremely wide GWAS datasets. Moreover, since the most common genomics variant calls VCF and uses the transposed representation, variant-spark can work directly with the VCF data, without the costly pre-processing required by other tools.

_variant-spark_ is built on top of Apache Spark – a modern distributed framework for big data processing, which gives variant-spark the ability to to scale horizontally on both bespoke cluster and public clouds.

The potential users include:

- Medical researchers seeking to perform GWAS-like analysis on large cohort data of genome wide sequencing data or imputed SNP array data.
- Medical researchers or clinicians seeking to perform clustering on genomic profiles to stratify large-cohort genomic data
- General researchers with classification or clustering needs of datasets with millions of features.

### Community

Please feel free to add issues and/or upvote issues you care about. Also join the [Gitter chat](https://gitter.im/VariantSpark/Lobby).
We also started [ReadTheDocs](https://variantspark.readthedocs.io/en/latest/) and there is always the this repo's issues page for you to add requests. Thanks for your support.

### Learn More

To learn more watch this video from YOW! Brisbane 2017.

[![variant-spark YOW! Brisbane 2017](/images/YOW__Conference_2017_Lynn_Langit___Denis_Bauer_-_Cloud_Data_Pipelines_-_YouTube.png?raw=true)](https://www.youtube.com/watch?v=0nw5nQ5T27E)

### Bicep

Bicep is free and supported by Microsoft support and is fun, easy, and productive way to build and deploy complex infrastructure on Azure. If you are currently using ARM you will love Bicep simple syntax. Bicep also support [declaring existing resources](https://docs.microsoft.com/en-us/azure/azure-resource-manager/bicep/resource-declaration?tabs=azure-powershell#reference-existing-resources).
More resources available at this [Link](https://docs.microsoft.com/en-us/azure/azure-resource-manager/bicep/overview#benefits-of-bicep-versus-other-tools)

## Prerequisites
- Managed Identity needs to be enabled as a resource provider inside Azure
- For the bash script, `jq` must be installed.

## How To Use

To clone and run this repo, you'll need [Git](https://git-scm.com), [Bicep](https://github.com/Azure/bicep/blob/main/docs/installing.md) and [azure-cli](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli) installed on your computer. Strongly recommend to use vs code to edit the file with bicep extension installed ([instructions](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-bicep)) for intellisense and other completions.
From your command line:

### Option 1:
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Faehrc%2FVariantSpark-Azure-deployment%2Fmaster%2Fazuredeploy.json)

Click on the above link to deploy the template. This will take you to your azure subscription and ask you to fill out certain parameters. Once completed the entire infrastructure will be created along with databricks workspace which can be used to run the default notebook.

### Option 2

If you need to customize the template you can use the following command:

```bash
# Clone this repository
$ git clone https://github.com/aehrc/VariantSpark-Azure-deployment.git

# Go into the repository
$ cd variant-databricks

# Update main.bicep file with variables as required. Default is for southeastasia region.
# Refer to Azure Databricks UDR section under References for region specific parameters.
$ code main.bicep

# Run the build shell script to create the resources
$ ./build.sh
```

Note: Build script assume Linux environment, If you're using Windows, [see this guide](https://docs.microsoft.com/en-us/windows/wsl/install-win10) on running Linux

## Credits

This template is based on ARM templates from the below repo:
- [Azure One-Click-Databricks](https://github.com/Azure/one-click-databricks)
- [Modern-data-warehouse-dataops](https://github.com/Azure-Samples/modern-data-warehouse-dataops)
- [Azure PrivateLink Templates](https://github.com/dmauser/PrivateLink)


