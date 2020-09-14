# Personal opinion on:

### Jahrer, M., Töscher, A. and Legenstein, R. (2010). Combining predictions for accurate recommender systems. In Proceedings of the 16th ACM SIGKDD International Conference on Knowledge Discovery and Data Mining, 693-702. ACM.

The paper focuses on the performance improvements, mainly based on RMSE, when combining the predictions of multiple collaborative filtering algorithms, in contrast to the predictions of a single algorithm. This idea makes a lot of sense, since each algorithm has pros and cons. Some of them suffer from the cold start problem, others are better at recommending more original titles, etc. Because of this, it is to be expected that finding a way to combine the results should yield a better outcome than the original algorithms by themselves, and thus, taking the strengths of each algorithm, and trying to minimize the drawbacks of each one. The paper uses the Netflix prize dataset for the whole process.

After the introductions, the authors move onto a quick explanation of the collaborative filtering algorithms to be used. A table with an arrangement of all the algorithms to be used, and their performance (RMSE) as a standalone algorithm can be found too. Along with that, they included three extra columns, training time, prediction time and memory needed. The memory used column is actually pretty interesting, as it is not usually considered in most papers, but models can get ridiculously big when working with big datasets, such as the Netflix prize dataset.

After this, they explain several ways of performing the blending of the results. They took several typical machine learning algorithms for decision making. Something interesting can be found in the NN description. Quoting the authors: 

> The output neuron has a sigmoid activation function with an output swing of -1 to +1. To generate rating predictions in the range of [1; 5] we use a simple output transformation. For example the output is multiplied by <img src="https://render.githubusercontent.com/render/math?math=\alpha"> = 3:6 and the constant <img src="https://render.githubusercontent.com/render/math?math=\beta"> = 3:0 is added.

They used this to make a transformation from a [-1, 1] range to a [1, 5] range, but the results doesn't add up. If we take the borders, <img src="https://render.githubusercontent.com/render/math?math=-1 * 3.6 + 3 = -0.6"> and <img src="https://render.githubusercontent.com/render/math?math=1 * 3.6 + 3 = 6.6">, resulting in a [-0.6, 6.6] range.

Finally, they move onto the results. As it can be seen, the best results were obtained by a neural network with 1 hidden layer of 70 neurons. But, if we compare this to the neural network with 1 hidden layer and 30 neurons, the results are pretty much the same, with a training times 8 times longer. Besides, the model is a lot more complex, making it more prone to overfitting, so I think the better model is the one with only 30 neurons. Finally, they showcase some results on the qualifying set of the Netflix prize.

As a closing thought, I feel like the authors oversold the results in the introduction. Quoting the authors:

> For example a linear combination of all single models leads to an RMSE of 0.87. [...] More sophisticated blending techniques lower the RMSE below 0.87.

When they showcased their results, not a single method resulted in a RMSE lower than 0.87, except when tested results on the qualifying set, which got them to 0.866004. Despite this being an improvement, I was expecting something more drastic. Nevertheless, the idea results in improvement, and I find the whole concept of the paper pretty interesting. Something I would've liked to see is some testing aimed specifically to the problems of specific algorithms, like the cold start problems. Also, maybe the inclusion of a simpler algorithm would've been interesting, like most common.

