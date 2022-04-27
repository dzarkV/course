In this video, we'll study the encoder architecture. An example of a popular encoder-only architecture is BERT, which is the most popular model of its kind.

Let's first start by understanding how it works.

We'll use a small example, using three words. We use these as inputs, and pass them through the encoder.

We retrieve a numerical representation of each word. 

Here, for example, the encoder converts the three words “Welcome to NYC” in these three sequences of numbers. The encoder outputs exactly one sequence of numbers per input word.

This numerical representation can also be called a "Feature vector", or "Feature tensor".

Let's dive in this representation. It contains one vector per word that was passed through the encoder. Each of these vector is a numerical representation of the word in question. The dimension of that vector is defined by the architecture of the model, for the base BERT model, it is 768.

These representations contain the value of a word; but contextualized. For example, the vector attributed to the word "to", isn't the representation of only the "to" word. It also takes into account the words around it, which we call the “context”.As in, it looks to the left context, the word on the left of the one we're studying (here the word "Welcome") and the context on the right (here the word "NYC") and outputs a value for the word, within its context. It is therefore a contextualized value.

One could say that the vector of 768 values holds the "meaning" of that word in the text.

How it does this is thanks to the self-attention mechanism. The self-attention mechanism relates to different positions (or different words) in a single sequence, in order to compute a representation of that sequence. As we've seen before, this means that the resulting representation of a word has been affected by other words in the sequence.

We won't dive into the specifics here, but we'll offer some further readings if you want to get a better understanding at what happens under the hood.

So when should one use an encoder? Encoders can be used as standalone models in a wide variety of tasks. For example BERT, arguably the most famous transformer model, is a standalone encoder model and at the time of release, beat the state of the art in many sequence classification tasks, question answering tasks, and masked language modeling, to only cite a few. The idea is that encoders are very powerful at extracting vectors that carry meaningful information about a sequence. This vector can then be handled down the road by additional layers of neurons to make sense of them.

Let's take a look at some examples where encoders really shine

First of all, Masked Language Modeling, or MLM. It's the task of predicting a hidden word in a sequence of words. Here, for example, we have hidden the word between "My" and "is". This is one of the objectives with which BERT was trained: it was trained to predict hidden words in a sequence. Encoders shine in this scenario in particular, as bidirectional information is crucial here. If we didn't have the words on the right (is, Sylvain, and the dot), then there is very little chance that BERT would have been able to identify "name" as the correct word. The encoder needs to have a good understanding of the sequence in order to predict a masked word, as even if the text is grammatically correct,

It does not necessarily make sense in the context of the sequence.

 As mentioned earlier, encoders are good at doing sequence classification. Sentiment analysis is an example of a sequence classification task. 

The model's aim is to identify the sentiment of a sequence – it can range from giving a sequence a rating from one to five stars if doing review analysis, to giving a positive or negative rating to a sequence, which is what is shown here.

For example here, given the two sequences, we use the model to compute a prediction and to classify the sequences among these two classes: positive and negative.

While the two sequences are very similar, containing the same words, the meaning is different – and the encoder model is able to grasp that difference.