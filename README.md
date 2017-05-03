# influence-tech-companies

In this repository the progress of my thesis can be found.

So far, I've made a notebook that reads the DBLP-CSR dataset from a MySQL database that I have imported in my local MySQL installation and constructs it into a Pandas DataFrame.
In the notebook I focussed mainly on the affiliation table for now. The first thing that stood out was that the affiliation column only contains one affiliation per author. I need to find out if that's correct and if that will be an obstacle (which I presume is). If so, I need to check the other dataset DBLP-SIGWEB which is bigger.

From those affiliations I constructed a unique set of all affiliations. I need to find out which affiliations are from private companies and which are from universities. To do that, I found a dataset containing 9363 universities and colleges with the goal of matching the affiliations to that dataset. Unfortunately, the format in which the affiliations are listed deviates from the format from the universities dataset. I managed to remove certain special characters and hyphens, which makes it possible to match Universidad del Bio Bio to Universidad del Bío-Bío. I'm not exactly sure what the percentage of correctly matched universities is yet. I've seen occurrences where in Journals University of Montpellier is used, while the name in the dataset is Université de Montpellier. Thoughts?

Another problem that came up is the amount of information in the affiliations column, because it contains data like 'department' and 'PhD student', et cetera.
I could fix that by splitting strings on commas and removing useless data with a few nifty if else loops. Generally it gives me some good results.
One mismatch example is KU Leuven from affiliations and Katholieke Universiteit Leuven from the universities dataset. I'm thinking of doing a Levenshtein comparison to find the closest match between the two datasets. Would that be a good idea? In an article by Wu et al. (2014) they use the Dempster-Shafer theory to disambiguate authors. I don't yet know if that's applicable in this research.

Because of this disambiguation problem for affiliations, I searched for literature and found quite some in Scientometrics Journals about this problem. I will investigate whether there exist better way of dealing with this because there is some research done after co-authorship, co-publications.

Furthermore, I have found some literature from Scientometrics about university-industry links, as well as an article that focusses on measuring impacts of academic science on industrial research (Tijssen & Van Leeuwen, 2006).
