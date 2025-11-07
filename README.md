# PhysioNet: Digitization of ECGImages

Extract the ECG time-series data from scans and photographs of paper printouts of the ECGs. 


You will build models to extract time series data from Electrocardiogram (ECG) images. ECGs are used to diagnose and guide treatment for heart disease. They exist as physical printouts, scanned images, photographs, or time series. Medical-grade ECG software currently works best on time series. Tools for extracting time series from ECG images can help convert billions of ECG images collected globally over decades into data for training better diagnostic models to improve clinical outcomes.



ECGs have been used for decades to diagnose and guide treatment for heart diseases. While modern machines store ECGs as time-series data, hard copy printouts, scans, and photos remain very common in clinical use. ECG images, even in electronic format, are not compatible or suitable for machine learning and the current medical-grade software, which only operate on time series.

Billions of hard copies, image-only electronic copies, scanned images, or photographs are estimated to exist globally. Clinical ECGs have specific subtleties that make their interpretation difficult for generic computer vision tools. Hence, electronic images are not enough. Having tools to digitize these ECG images into time series can help convert decades of data collected globally to train better models and improve cardiovascular diagnosis and treatment.

This is not a trivial task, however. Physical printouts, scanning, and photography introduce imaging artifacts (misalignments, rotations, reflections, aspect ratio issues, blurring, scanning resolution, etc.). ECG specifications such as multi-lead interrelationships corresponding to the physical placement of electrodes on the body, variability in ECG data collection methods, varied sampling frequencies, signal lengths, locations of leads on ECG images from different vendors, and noisiness of the original time-series data add to the challenges of the problem.

This competition is a rerun of the 2024 PhysioNet Competition on ECG digitization with fresh data. In this competition, you will build a model that extracts the original ECG time-series data from images of paper ECGs. The idea is to bring older or image-only ECGs into the AI age, allowing today's tools to utilize them effectively.

Your work could help unlock billions of historical ECG images, support improved cardiovascular care, and expand access to critical health insights, particularly in areas where digital records are limited.

Evaluation
The evaluation metric for this competition is a modified signal-to-noise ratio (SNR), designed to assess the quality of time series ECG reconstructed from ECG images against the ground-truth ECG time series.

To ensure that submissions are not unfairly penalized for minor alignment issues that are irrelevant for ECG interpretation, the metric first aligns the predicted signal with the ground-truth signal. This alignment procedure corrects for two types of discrepancies:

Time Shifts: It finds the optimal horizontal shift (up to a maximum of 0.2 seconds) that maximizes the cross-correlation between your prediction and the ground truth.

Vertical Shifts: It calculates and removes any constant vertical (amplitude) offset between the two signals after they are time-aligned.

The final score is calculated by comparing the power of the true signal to the power of the reconstruction error (noise). The signal powers and noise powers are first summed across all 12 leads before a single SNR is computed for that entire ECG record. The competition score is the average of these individual ECG SNRs, converted to decibel scale. A higher SNR value indicates a more accurate reconstruction with less noise.

Submission File:

For each ID in the test set, you must predict a value for the value variable. The file should contain a header and have the following format:

id,value

'62_0_I',0.0

'62_1_II',0.3

'62_2_I',0.4

etc.


Acknowledgements
Use of the Competition Datasets in any academic work or research papers should use the following citations:

Shivashankara KK, Deepanshi, Shervedani AM, Reyna MA, Clifford GD, Sameni R. ECG-Image-Kit: a synthetic image generation toolbox to facilitate deep learning-based electrocardiogram digitization. Physiological Measurement 2024; 45:055019. DOI: 10.1088/1361-6579/ad4954

Reyna MA, Deepanshi, Weigle J, Koscova Z, Campbell K, Shivashankara KK, Saghafi S, Nikookar S, Motie-Shirazi M, Kiarashi Y, Seyedi S, Hassannia M, Bjørnstad AM, Stenhede E, Ranjbar A, Clifford GD, and Sameni R. ECG-Image-Database: A dataset of ECG images with real-world imaging and scanning artifacts; a foundation for computerized ECG image digitization and analysis, 2024. DOI: 10.48550/arXiv.2409.16612.

Reyna MA, Deepanshi, Weigle J, Koscova Z, Campbell K, Seyedi S, Elola A, Bahrami Rad A, Shah AJ, Bhatia NK, Clifford GD, Sameni R. Digitization and Classification of ECG Images: The George B. Moody PhysioNet Challenge 2024; Computing in Cardiology 2024; 51: 1-4.

Citation:

Matthew A. Reyna, Deepanshi, James Weigle, Zuzana Koscova, Kiersten Campbell, Salman Seyedi, Andoni Elola, Ali Bahrami Rad, Amit J Shah, Neal K. Bhatia, Yao Yan, Sohier Dane, Addison Howard, Gari D. Clifford, and Reza Sameni. PhysioNet - Digitization of ECG Images. https://kaggle.com/competitions/physionet-ecg-image-digitization, 2025. Kaggle.
