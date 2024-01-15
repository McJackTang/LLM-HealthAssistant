# ALPHA: AnomaLous Physiological Health Assessment Using Large Language Models【AI Health Summit 2023】


# Abstract
This study concentrates on evaluating the efficacy of Large Language Models (LLMs) in healthcare, with a specific focus on their application in personal anomalous health monitoring. Our research primarily investigates the capabilities of LLMs in interpreting and analyzing physiological data obtained from FDA-approved devices. We conducted an extensive analysis using anomalous physiological data gathered in a simulated low-air-pressure plateau environment. This allowed us to assess the precision and reliability of LLMs in understanding and evaluating users' health status with notable specificity. Our findings reveal that LLMs exhibit exceptional performance in determining medical indicators, including a **Mean Absolute Error (MAE) of less than 1 beat per minute for heart rate and less than 1\% for oxygen saturation (SpO2)**. Furthermore, the **Mean Absolute Percentage Error (MAPE) for these evaluations remained below 1\%, with the overall accuracy of health assessments surpassing 85\%**. In image analysis tasks, such as interpreting photoplethysmography (PPG) data, our specially adapted GPT models demonstrated remarkable proficiency,  **achieving less than 1 bpm error in cycle count and  7.28 MAE for heart rate estimation**.  This study highlights LLMs' dual role as health data analysis tools and pivotal elements in advanced AI health assistants, offering personalized health insights and recommendations within the future health assistant framework.

<img src='https://github.com/McJackTang/LLM-HealthAssistant/blob/main/figs/framework.png' width = 100% height = 100%/>

# Data
```Demo_data
├── light_1        # sceneario 
    ├── v01        # subject 
        ├── BVP.csv       # PPG waveform signal, 20fps    
        ├── HR.csv        # Heart Rate, 1fps                                  
        ├── SpO2.csv      # Blood Oxygen, 1fps   
        ├── pngs          # figures plot for PPG
    ├── v02
    ├── ...
├── light_2
├── ...
 ```

# Code  
run ```data_text.py``` with your LLM API

# Experiments  
Tasks are chosen to validate the performance of mainstream LLMs in health-related tasks:(1) calculate average vital information from raw biomedical sensor signals(e.g., the average heart rate for 60 seconds) (2) assess health statuses based on medical knowledge. To do the experiments, open-source physiological datasets are first tested in our system. However, these datasets do not include data from individuals with abnormal health conditions (e.g., arrhythmia), which makes it hard to tell whether the LLMs output the correct assessment. To fill the gap, we conduct a user study under low air pressure to simulate the environment of a highland and collect multiple physiological data for 12 subject tests. Our experiment was approved by the Institutional Review Board (No.20230076). In the low-air condition, blood oxygen may decrease even to hypoxia syndrome, and heart rate, and respiration rate would increase, which enables the collection of physiological data in instances of abnormal health conditions. The detailed results are shown in the following.

## Vitals Calculation
In the pursuit of vital calculation, the primary objective involves tasking the large language model with calculating the average values of vital signs (e.g., HR, SpO2) over continuous time intervals. This experimental study encompasses two distinct tasks: (1) **Single-Task**, where a solitary vital sign is provided as input along with a corresponding prompt to compute a singular value; (2) **Multi-Task**, which involves inputting two vital signs simultaneously and prompting the model to compute two values concurrently. The Single-Task is specifically designed to evaluate the accuracy and reliability of the Large Language Model (LLM), while the Multi-Task is intended to assess the model's proficiency in processing and interpreting complex information efficiently. Our findings indicate that LLMs demonstrate commendable performance in both of these tasks.
<img src='https://github.com/McJackTang/LLM-HealthAssistant/blob/main/figs/Vitals Calculation.jpg' width = 100% height = 100%/>

## Health Status Assessment
The objective of the multi-classification mission is to evaluate the health status based on the analysis of vital signs, encompassing various distinct and blended vital sign datasets in a manner similar to the structure outlined. This assessment adheres to the established guidelines <https://www.who.int/news-room/questions-and-answers/item/oxygen> provided by the World Health Organization (WHO). For example, an abnormal heart rate (HR) exceeding 100 and an extremely abnormal state surpassing 130 are indicative of deviations from the norm. Similarly, deviations in oxygen saturation (SpO2) are considered abnormal when falling below 95 and extremely abnormal when dropping below 92.
<img src='https://github.com/McJackTang/LLM-HealthAssistant/blob/main/figs/Health Status Assessment.jpg' width = 100% height = 100%/>

## Medical Image Analysis  
In addition to textual information, dynamic medical vital images such as PPG or ECG play a crucial role in assessing the health condition of people. To evaluate the ability of the Large Language Model (LLM) to comprehend PPG graphs, a specialized GPT model was tasked with counting the cycles in the images and subsequently calculating the heart rate through analysis. **To the best of our knowledge, we are the first to design and fine-tune a GPTs model referred to as the "visual counter" accessible at https://chat.openai.com/g/g-SR8nCXyWI-visual-counter.** Our tailored GPTs model could achieve 0.556 MAE and 0.889 MAE for peak and trough count respectively, **which leads to 7.283 MAE and 9\% MAPE for heart rate estimation**.

<div style="text-align: center;">
<img src='https://github.com/McJackTang/LLM-HealthAssistant/blob/main/figs/Sample.png' width = 50% height = 50%/>
</div>
<div style="text-align: center;">
<img src='https://github.com/McJackTang/LLM-HealthAssistant/blob/main/figs/hr_bland_altman.png' width =50% height = 50%/>
</div>

# Citation
[ALPHA: AnomaLous Physiological Health Assessment Using Large Language Models](https://arxiv.org/abs/2311.12524)
```
@misc{tang2023alpha,
    title={ALPHA: AnomaLous Physiological Health Assessment Using Large Language Models},
    author={Jiankai Tang and Kegang Wang and Hongming Hu and Xiyuxing Zhang and Peiyu Wang and Xin Liu and Yuntao Wang},
    year={2023},
    eprint={2311.12524},
    archivePrefix={arXiv},
    primaryClass={cs.LG}
}
```
