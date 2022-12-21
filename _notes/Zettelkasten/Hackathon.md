
# Inspiration

As the number of companies developing brain computer interfaces continues to grow (e.g., Neuralink and Synchron), the need for low latency and enegy efficient neural decoding methods does as well. We wanted to show that spiking neural networks, which can be implemented on neuromorphic chips, could be used to decode such signals and fill this gap. 

Additionally, spiking neural networks are closer to the underlying neuron biophysics that produced the real data. We hoped that by using realistic neural dynamics, we could learn more usfeul temporal representations in the data compared to tradiational decoding or artificial neural network methods which rely on average the number of spikes over time. 


# What it does

For our project  


# How we built it

The spiking neural network was built using PyTorch. The equations for the LIF dynamics were discretized and simualted forwards in time using an exponential integration method.  A surrogate gradient method was used to allow gradients to flow freely though the discontinous activation used for spiking. See https://github.com/fzenke/spytorch for a tutorial on surrogate gradient descent. 

# Challenges we ran into

- Took longer than expected to understand the formatting of the spike timing and finger velocity data

- Trying to the tune the hyperparmeters to improve performance was hard given the time constraint of the hackathon

- We tried a more complicated neuron model (LIF with adapation), but performance didn't imporve. However, this might change with more rigous parameter tuning

# Accomplishemnts that we're prooud of

-  We all learnt a lot about spiking neural networks!

- We were able to get a basic spiking neural network running and acheive decent performance on the test set

