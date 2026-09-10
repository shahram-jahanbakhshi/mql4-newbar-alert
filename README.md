# MQL4 New Bar Alert

A lightweight MQL4 class to detect **new bar events** across multiple timeframes simultaneously and trigger alerts in MetaTrader 4.

![Alert Popup](Screenshots/alert-popup.png)

## ✨ Features

- Monitor multiple timeframes at once (M1, M5, M15, H1, H4, D1, etc.)
- Accurate detection using `iTime` (the most reliable method in MQL4)
- Optional sound alert via `PlaySound`
- Object-oriented design with the `CNewBarAlert` class
- No external dependencies
- Works with both Expert Advisors and Indicators

## 📦 Installation

1. Copy `CNewBarAlert.mqh` to your MetaTrader 4 Include folder: MQL4/Include/CNewBarAlert.mqh
2. Copy `NewBarAlert_Example.mq4` to your Experts folder: MQL4/Experts/NewBarAlert_Example.mq4
3.  In MetaEditor, press `F7` to compile.
4. Drag the Expert Advisor onto a chart.

## 🚀 Usage

```mql4
#include <CNewBarAlert.mqh>

CNewBarAlert barAlert;

int OnInit()
{
barAlert.AddTimeframe(PERIOD_M1);
barAlert.AddTimeframe(PERIOD_M5);
barAlert.AddTimeframe(PERIOD_H1);
barAlert.AddTimeframe(PERIOD_H4);
barAlert.SetSound(true, "alert.wav");
barAlert.Init();
return(INIT_SUCCEEDED);
}

void OnTick()
{
barAlert.Check();
}
```
## 📋 API Reference
Method	Description
AddTimeframe(tf)	Adds a timeframe to the watch list
Init()	Initializes the class (call in OnInit)
Check()	Call in OnTick; triggers alerts on new bars
SetSound(enable, file)	Enables/disables sound alerts and sets the sound file
## ⚠️ Notes
Alert and PlaySound do not work in the Strategy Tester.

For live testing, run the EA on a live chart.

The class stores the last bar time per timeframe internally, so no duplicate alerts occur.

## 📄 License
This project is licensed under the MIT License – see the LICENSE file for details.

## 👤 Author
Shahram Jahanbakhshi – GitHub

text

Feel free to replace `shahram` and `shahram - jahanbakhshi` with your own details. If you'd like me to add badges (e.g., MQL4, MIT) or a Table of Contents, just let me know!
