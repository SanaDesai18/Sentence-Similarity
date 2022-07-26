# Sentence-Similarity with BERT
Why BERT Helps
BERT, as we already mentioned — is the MVP of NLP. And a big part of this is down to BERTs ability to embed the meaning of words into densely packed vectors.

We call them dense vectors because every value within the vector has a value and has a reason for being that value — this is in contrast to sparse vectors, such as one-hot encoded vectors where the majority of values are 0.

BERT is great at creating these dense vectors, and each encoder layer (there are several) outputs a set of dense vectors.
For BERT base, this will be a vector containing 768. Those 768 values contain our numerical representation of a single token — which we can use as contextual word embeddings.

Because there is one of these vectors for representing each token (output by each encoder), we are actually looking at a tensor of size 768 by the number of tokens.

We can take these tensors — and transform them to create semantic representations of the input sequence. We can then take our similarity metrics and calculate the respective similarity between different sequences.

The simplest and most commonly extracted tensor is the last_hidden_state tensor — which is conveniently output by the BERT model.

Of course, this is a pretty large tensor — at 512x768 — and we want a vector to apply our similarity measures to it.

**Creating The Vector**
For us to convert our last_hidden_states tensor into our vector — we use a mean pooling operation.

Each of those 512 tokens has a respective 768 values. This pooling operation will take the mean of all token embeddings and compress them into a single 768 vector space — creating a ‘sentence vector’.

At the same time, we can’t just take the mean activation as is. We need to consider null padding tokens (which we should not include).

**Sentence-transformers/bert-base-nli-mean-tokens**
This is a sentence-transformers model: It maps sentences & paragraphs to a 768 dimensional dense vector space and can be used for tasks like clustering or semantic search.

Without sentence-transformers, you can use the model like this: First, you pass your input through the transformer model, then you have to apply the right pooling-operation on-top of the contextualized word embeddings.

**OUTPUT OF MOdel**
As The company requirement the output varies from o to 1.

**Contact info**
Sana Desai---sanandesai@gmail.com
