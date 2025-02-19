# ECG Analysis - Sleep Patterns
##### Given a sample file containing 32399 seconds (~9 hours) of ECG data with a sample rate of 250hz (32399*250=8.099.750 lines) we will proceed to analyze the signal in order to predict the various sleep stages.
> We can confirm our guesses with the sleep.txt file that contains accurate sleep stages for 30 second intervals

# Methodology

 - Find r-peaks with a threshold of 0.35mV in order to then find the rr intervals to give us an understanding of the heart rate variability in the given sample file
 - Resample to a lower sample rate if the signal is fuzzy
 - Calculate the total power of the signal
 - Calculate VLF,LF,HF,LF/HF ratio
 > VLF (0.0033-0.04)

 > LF (0.04-0.15)
 
 > HF (0.15-0.4) 
 - Create predictions for the sleep stages based on the features calculated above for every 30 seconds
 - Compare with sleep.txt 
 > LF<0.296 && ratio<=3.37 = REM_Wake

 > LF<=0.296 && ratio>3.37 = NREM

 > LF>0.296 && total<=0.186 = NREM
 
 > LF>0.296 && total>0.186 = REM_Wake
.