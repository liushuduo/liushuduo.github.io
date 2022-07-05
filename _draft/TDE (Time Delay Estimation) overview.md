# TDE (Time Delay Estimation) overview

Broadly speaking, TDE can be categorized into the two following types. 

1. TOA (Time of Arrival): the clean reference signal is known.
2. TDOA (Time Difference of Arrival): no explicit reference signal known. However, more than one receivers are utilized thus the time difference of signal arrivals can be determined. 

It is not an easy task to perform TOA or TDOA for TDE. The difficulties are:

1. Signal is generally immersed in ambient noise;
2. Each observation signal may contain multiple attenuated and delayed replicas of the source signal due to reflections from boundaries and objects;
3. Multipath propagation effect introduces reverberation;
4. The source of wavefront may also move from time to time.

## Signal Propagation Models for TDE

**Ideal propagation model**



