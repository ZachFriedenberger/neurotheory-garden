# Neuropixel Data Analysis

## What we checked before
1. Average response centered on the image change (across heriachy)
	- ER increased on image change. 
	- BF was constant around ~10%
	
2. Average hit vs. miss differences centered on the image change (across heriachy)
	- No difference in BF, except for the odd time bin. Hard to be confident in these increases becasue they seemed to be randomly placed in time and occurred in areas with less neurons (possibly noise)
	- ER seemed to respond faster to hits in the H.O. areas and slwoer in the L.O. areas. 
	
4. Single unit activity
	- ER and BF were temporally uncorrelated with eachother
	- Hard to say what is noise and what isn't without a specific correlate


## What we did before that was good
- Shuffling bursts and events ISIs
- Shuffling hit vs. miss labels


## What we want to check in the new data

**Q: What new data do we have available?**

- Subtype classification (SST, VIP, PYR)
- Behavioural variables
	- Timing of  licks and reward delivery
	- Running speed, eye position and pupil area
- Different image sets for testing novelty
	- Novel image set was not used for training the mice
- Receptive field characterization


**Q: What have we learned from the Doron data that can help us here?**

- BF variance decreases with accuracy
- Timing moment of BF response occurs sooner after training

**Q: What different questions can we answer or how can we build upon those results?**

- Take advantage of the ability to test multiple different encodings (expectation, novelty, reward, possibly attention)
- We need to take advantage of the fact that we have multi-unit recordings across the entire visual heiarchy (how does the timing of ER/BF depend on the level of the heiarchy?)
- Can we take advantage of the fact that we have receptive field characterization data? 

1. Check if BF is encoding information related to expectation/prediction
	- Look at BF centered around omitted images
	- We would expect to see a signal that starts in the L.O. areas and travels to the H.O. areas if something like heiarchical predictive coding is using dendrites to compute missmatch/error signals
		- There has been some theoretical work on dendritic predictive coding and there was that paper that Ricahrd was reviewing combing burst multiplexing and predictive coding

2. Check if BF is encoding novelty
	- 

3. Check is BF changes centered on the reward delivery times
	- We now have reward delivery times and the lick times instead of just looking at the delivery window
	- We can compare the active to the passive trials again 

4. Look at d-prime as a proxy for attention 

5. Look at pupil area as a proxy for attention
	


# Questions

- What theory/model of the visual system do we have in mind when looking at this data?
- 

# Spike sorting quality metrics

## Firing rate

## Presence ratio

- Fraction of time during a session that a unit is spiking
- Can be used to avoid drifitng units or 





