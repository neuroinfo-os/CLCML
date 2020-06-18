
# Deep Brain Stimulation Programming 2.0: 
## Future Perspectives for Target Identification and Adaptive Closed Loop Stimulation
### Franz Hell, Carla Palleis, Jan H. Mehrkens, Thomas Koeglsperger, and Kai Bötzel
### Frontiers in Neurology, 2019; 10: 314. doi: 10.3389/fneur.2019.00314


### Summary
The most of the article is dedicated to a comprehensive overview over recent research on the target structures and targeting strategies in Deep Brain Stimulation (DBS). The second part focuses on  on closed-loop stimulation and associated biofeedback signals. (The following summary covers only the latter topic)


Problem statment. Open-loop DBS are prone to reduction of efficiency over time due to chanhes in patients' condition.
Closed loop adaptive DBS involves two distinctive parts: feedback signals (biomarkers) and mechanisms of control. The fisrts step is necessay to describe relation to a clinical symptom. Adaptive control mechanisms are used for adjustment of a  stimulation.

__Biomarkers__
1. _Electrophysiological measurements_. Eg. Local field potentials (LFP) which use beta frequency amplitude as a mechanism to trigger the stimulation;  Electromyography; Kinematic sensors; ECoG 


2. _Neurochemical sensing_. Recently several devices were developed: detectors  wich sence changes in dopamine concentration in rodents; WINCS Harmoni®: implanted neurochemical sensor which measures neurotransmitter concentration. One should notice, that these devicesn have een used only in preclinical DBS studies!


3. _External mechanistic sensors_ Accelerometers,  EMG sensors. State-of-the-art devices incorporate several sensors. E.g. a smart glove contains two touch sensors, two 3D-accelerometers and a force sensor to assess tremor, rigidity and bradykinesia of hand and arm [https://ieeexplore.ieee.org/abstract/document/5999113]. (ToDo: add Heldman et al. [https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4760891/], [https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4372473/])

__Control Mechanisms__
1. _Beta threshold targeting_. Stimualtion is turned on, when the amplitude of oscillatory activity in the β-band exceeds a certain threshold, or only when pathological long β bursts are detected.  But, unfortunately,  beta oscillations and beta oscillatory characteristics are sensitive to medication and patient's behavior. 


2. _Noise cancellation_.   This control mechanism is based on the effect of noise cancellation: when specific phases of the tremor sensed by an accelerometer attached to a hand of a parkinsonian patient, the stimulation applied on the talamus.


3. _Stimulation on demand_. E.g. cortical electrodes sense β-band desynchronization in patients with essential tremor in the beginning of a movement. Then the stimulation applied only in a movevent, but stays tirned off during restinf states. However, this approach reduces tremor only with a delay, as it is not capable (yet) to predict a movement before it occurs.

4. _Coordinated reset stimulation_.  The method implies brief high-frequency pulse trains when, specific structures known to produce clinical symptomth produce rhythmic synchronized oscillations. This leads to  reduction of  symptoms such as tremor within patients with Parkinson desease.


### Future Perspectives

- Learning disease symptoms severity and underlying neural activity with ML.
- Integrating parameters for ML from different kinds of biomarkers.
- Decoding and predicting patiens neural and clinical states.
- Application of reinforcment learning to learn and control stimulation.
- Inferring the causal structure of brain networks to reduce amount of time and cost needed to gather enough data for ML.
(Methods such as Granger causality , dynamic causal modeling, structural equation modeling, and causal Bayesian networks have already showed their  effectivness in revealing neronal dynamics of several brain regions).


