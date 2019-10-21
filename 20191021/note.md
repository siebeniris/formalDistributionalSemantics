# Building a shared world: Mapping distributional to model-theoretic semantic spaces
* Aurelie Herbelot & Eva Maria Vecchi (2015)

### abstract
a function relationship 
* distributional information
* vectorial concept represnetations in which dimensions are predicates and weights are generalised quantifiers.

=> learn model of such relationship

initial results:

at least for domain-specific data, map between formalisms, and generate high-quality vector representations which encapsulate set overlap information.

further investigation:

generate natural language quantifiers from such vectors.



## Datasets:
1. quantified McRae norms
	* QME (by Herbelot and Vecchi 2015)
	for each concept-feature pair (C,f), the annotation provides a natural language quantifier expressing the ratio of instances of C having the feature f, (as elicited by 3 coders)

	The quantifiers in use are NO, FEW, SOME, MOST, ALL.

	An additional Label KIND, for usages of the concept as a kind, where quantification does not apply (e.g., beaver symbol-of-Canada). 
	cohen kappa = 0.59

	6156 instances. an average of 11 features per concept 


spearman rank correlation between the three annotators => 0.63

2. Additional animal data
	* a set of 72 animal concepts with quantification annotations along 54 features.

## Semantic spaces:
### The distributional semantic space
1. co-occurrence based space (DS __cooc__ )

a word is represented by co-occurrence counts with content words (nouns, verbs, adjectives and adverbs)

* source corpus:
ukWaC (2009 dump of the English Wikipedia) and the BNC (2.8 billion tokens)
* select top 10k content word for the contexts, using a bag-of-words approach and counting co-occurrences within a sentence
* apply positive Pointweise Mutual Information to the raw counts, and reduce the dimensions to 300 through SVD

2. context-predicting vectors (DS __Mikolow__ )

better than 1.

explore this as a vlid distributional representation of a word's semantics

### The model-theoretic space

* the ontology: a world(*state of affairs* or a simple situation), with everything that is contained in that world

	* formalized as a *set* of entities

* the denotation function associates words with their *extensions* in the model, i.e. the sets they refer to.

It is possible to define a truth function for sentences, which computes whether a particular statement corresponds to the model or not.

It is not always possible to learn the cardinalities from distributional data. This means that the a model built from distributional data does not support denotation in the standard way, and thus precludes the definition of a truth function: we cannot verify the truth of the sentence *There are 25957 white horses in the world*.  => underspecified set-thereotic representation of some shared beliefs about the world (`model-theoretic` space)

* definition of the `ontology` 

a toy vector with only four dimnensions for the concept *horse*

| a\_mammal|1|
|---|---|
|has\_four\_legs |0.95|
|is\_brown|0.35|
|is\_scaly|0|

## Experiments

* 3 model-theoretic spaces built from McRae and AD datasets
	* convert the annotation into a numerical format
		* ALL -> 1, MOST -> 0.95, SOME -> 0.35, FEW -> 0.05, NO -> 0
			(These values correspond to the weights giving the best inter-annotator agreement in Herbelot and Vecchi (2015), when calculating weighted Cohen's kappa on QMR)


