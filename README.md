<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:4A0D2E,50:C2185B,100:FF8FC7&height=200&section=header&text=CycleSenseAI&fontSize=54&fontColor=FFFFFF&fontAlignY=36&desc=A%20menstrual%20cycle%20tracker%20that%20learns%20your%20rhythm&descSize=16&descAlignY=58" width="100%" alt="CycleSenseAI"/>

<p>
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python"/>
  <img src="https://img.shields.io/badge/PyTorch%20LSTM-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white" alt="PyTorch"/>
  <img src="https://img.shields.io/badge/CustomTkinter-1F6FEB?style=for-the-badge" alt="CustomTkinter"/>
  <img src="https://img.shields.io/badge/Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white" alt="Supabase"/>
  <img src="https://img.shields.io/badge/Gemini-8E75B2?style=for-the-badge&logo=googlegemini&logoColor=white" alt="Gemini"/>
  <img src="https://img.shields.io/badge/License-MIT-FF4FA3?style=for-the-badge" alt="MIT License"/>
</p>

</div>

---

## Why I built it

Most period apps predict the next date with a simple average, which breaks as soon as a cycle runs early or late. Many also send private health data to servers you know nothing about.

**CycleSenseAI** is a desktop app that predicts the next cycle with an **LSTM model trained on real cycle data**, explains which phase you are in, and lets you talk to a period-focused chatbot about symptoms and mood, all behind your own secure account.

## Features

| | |
|---|---|
| **Next-cycle prediction** | A PyTorch LSTM reads your recent cycle history and predicts the next start date. |
| **Calendar tracker** | Mark period days on a monthly calendar, choose period length, skip a month or move between months. |
| **Cycle phase** | Works out your current phase from the last start date, cycle length and period length, and explains it. |
| **Mood check-in** | Tap Happy, Sad or Angry and the chatbot opens with advice for that mood. |
| **Period chatbot** | A Gemini assistant kept strictly on topic: symptoms, remedies and mood swings, in short practical answers. |
| **Insights** | Cycle history plus quick guides on keeping cycles regular, exercise and yoga, and diet. |
| **Accounts** | Sign up, log in and reset a forgotten password, with data stored in Supabase. |

## How the prediction works

```
Dates you mark in the calendar ──> 5 cycle features ──> scaler (scaler.pkl) ──> LSTM (64 hidden units) ──> predicted cycle length ──> next start date
```

- **Data:** the [Menstrual Cycle Data](https://www.kaggle.com/datasets/nikitabisht/menstrual-cycle-data) set from Kaggle.
- **Model:** a single-layer LSTM with a linear output head (`model_lstm.py`), weights in `Dataset_pth_file/period_lstm_model.pth`.

## Run it

```bash
git clone https://github.com/21Afnan/CycleSenseAI.git
cd CycleSenseAI
pip install customtkinter pillow torch scikit-learn supabase google-generativeai
```

Set three environment variables (your own Supabase project and Gemini key):

```bash
set SUPABASE_URL=https://your-project.supabase.co
set SUPABASE_KEY=your_supabase_anon_key
set GEMINI_API_KEY=your_gemini_key
```

On macOS or Linux use `export` instead of `set`. Then start the app:

```bash
python main.py
```

## Project structure

```
CycleSenseAI/
├── main.py                 # entry point
├── First_Page.py, Getstarted.py
├── SignUp.py, Log_In.py, Forgot_Password.py
├── Database.py, config.py  # Supabase connection and auth
├── tracker.py              # calendar and LSTM prediction
├── model_lstm.py           # LSTM definition
├── Phase_calculation.py    # current cycle phase
├── insights.py             # dashboard, moods, guides
├── bot2.py                 # Gemini period chatbot
└── Dataset_pth_file/       # dataset, trained weights, scaler
```

## Disclaimer

CycleSenseAI is a learning project, not medical advice. Please see a doctor for any health concern.

---

<div align="center">

**Afnan Shoukat**

<a href="mailto:afnanshoukat35@gmail.com"><img src="https://img.shields.io/badge/Email-afnanshoukat35%40gmail.com-FF4FA3?style=for-the-badge&logo=gmail&logoColor=white&labelColor=4A0D2E" alt="Email"/></a>
<a href="https://www.linkedin.com/in/afnanshoukat"><img src="https://img.shields.io/badge/LinkedIn-Afnan%20Shoukat-FF4FA3?style=for-the-badge&logo=linkedin&logoColor=white&labelColor=4A0D2E" alt="LinkedIn"/></a>
<a href="https://github.com/21Afnan"><img src="https://img.shields.io/badge/GitHub-21Afnan-FF4FA3?style=for-the-badge&logo=github&logoColor=white&labelColor=4A0D2E" alt="GitHub"/></a>

Released under the [MIT License](LICENSE).

</div>
