---
title: Physical Intuitions of Gradient Descent
---

There are a few insights that helped me to wrap my head around gradient descent a bit better.
But before we dive in, let's first remember the goal: we have some function $$C(x)$$, and
we want to make it really small. You can think of cost (sometimes called loss) as a score for how good
your model is. For the cost function, lower is better -- the best models have a really
low cost, which means they do a really good job of predicting whatever you're trying to predict.

So how do we make the cost really small? In the case of a neural network, the main knobs we
can turn[^1] are the weights and the biases of the network. Our objective is to figure
our which ways to turn them to get the cost as low as possible.

Let's imagine you're stuck on the side of a mountain in the middle of the night. It's so dark that you can't
see which direction moves you towards the bottom of the mountain -- you're going to have
to figure it out by feel. What should you do? Well, one strategy might be to touch your
toe lightly to the spot immediately in front of you. If it's downhill, it seems like a
pretty good bet that you should step in that direction. If it's steeply uphill, there's
a pretty good bet that you should take a step backwards, since the mountain seems to be
trending downhill in the direction directly behind you. You repeat this process again
in the lateral direction: you take a tiny step immediately to your right and see how
steep the mountain is. If it's sloping down towards the bottom of the mountain, you can
feel confident that you should step in that direction, and if it's sloping upwards, you
can feel pretty good about taking a step to the left. Let's say that after this process
you learn that stepping forward leads downhill, and stepping right leads downhill. You can
walk a little to the right, and a little forward, and you'll be a little further down the
mountain. If you do this enough times, you will hopefully[^2] make it to the bottom.

This is more or less how gradient descent works. The "mountain" is your cost function -- it's some
function that has a minimum point that we're trying to get to[^3]. You can think of the backwards-forwards
direction and the left-right direction as two parameters -- as we move these parameters around, we move
to different places on the mountain. At every step, we check the coordinates immediately ahead; if stepping
in a direction leads down the mountain, we move in that direction, and if it leads higher on the mountain, we go
in the opposite direction. This process is called gradient descent. Breaking the term:
* The **gradient** is just the steepness at any given point. It's the value that we get when we take a tiny step
  in front of us and see if it leads us up or down, and how steeply it does so. In mathematical terms, it's
  the partial derivative of the cost function with respect to a given parameter.
* **Descent** just refers to the fact that we're going forward if the gradient is negative, or we're going backward
  if the gradient is positive. The mechanism by which we do this is to take the parameter we're
  refining and to subtract its gradient[^4] (so, if the gradient is positive we make the parameter smaller
  by subtracting a positive number,
  which is equivalent to "moving backwards" on our mountain, and if the gradient is negative we make
  the parameter bigger by subtracting a negative, which is equivalent to "moving forward")


So it stands to reason that we should be able to do a pretty good job getting to the bottom of our mountain
(or cost function) if we can repeatedly figure out the gradient of the cost function with respect to every
direction (parameter) and subtract it from that direction (parameter). But _how_ do we figure out the gradient? For this we're going to need to lean on calculus.
I'll cover this in a separate post, but for now I _highly_ recommend checking out
[Neural Networks and Deep Learning Chapter 2](http://neuralnetworksanddeeplearning.com/chap2.html) which
provides an _excellent_ intuitive introduction to the numerical side of gradient descent and backpropagation.[^5]

Until next time!

### Footnotes:
[^1]: I'm excluding hyperparameters from this discussion: for the purposes of explanation, let's assume we have already decided upon a specific network architecture / configuration, and we're just trying to get it to perform as well as possible.
[^2]: There's always the chance that you get to a crater on the side of the mountain that seems like it could be the bottom because every direction leads you uphill; this is also something that happens in backpropagation; in ML parlance we call these "local minima"
[^3]: Remember, a lower cost is better, so if we can get to the minimum of the cost function, we have made our model as accurate as we can!
[^4]: We usually only subtract a small portion of the gradient, as we want to be careful about our steps -- steps that are too big could cause us to jump _up_ the hill. I encourage you to think about how this could happen!
[^5]: Really, you should read the rest of the book as well. Michael Nielsen does an _awesome_ job.
