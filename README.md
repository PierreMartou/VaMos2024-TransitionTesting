# Complement for the conference VaMoS2024
## What is it ?
This small prototype of a Risk Information System (RIS) is meant to complement the paper "Combinatorial Transition Testing in Dynamically Adaptive Systems", by P. Martou, B. Duhoux, K. Mens and A. Legay.

Its goal is to illustrate with actual code the RIS prototype described in this paper. It mimicks RIS behaviour through terminal messages and a simple GUI coded with Tkinter (standard GUI library for Python). For possible (de)activations of features, please refer to Fig. 1 in the paper.

It is injected with three errors (Section 2). The system has no knowledge of these errors, but has a perfect test oracle which checks the entire system's correctness at each transition and alerts the user would it encounter any behavioural error. You can visually see such errors, as the Emergency Level is displayed for each configuration and the GUI updates between each configuration.

## Description of the Risk Information System (extended version of Section 2 in the paper)

The \emph{Widget} feature determines what graphical information is shown to users, such as a \emph{Map} or \emph{Instructions} on a specific hazard. 
The \emph{Map} is only present if the location services are activated on the device on which the application is currently running. 
In such a case this feature shows the user where the hazard is occurring.
If the user is in the impacted zone of the hazard, it may also show the user a route to a safe place.
In addition to the map, hazard-specific \emph{Instructions} can be shown to users who are in an impacted zone. 
When several hazards occur simultaneously, the different instructions for each hazard are displayed to the user.
For the sake of user interface consistency, the \emph{Map} widget should always be placed above the \emph{Instructions} widget. In case of a \emph{Map} is no longer present (e.g., when location services are turned off), the \emph{Instructions} widget should be on top of the application screen. 

The \emph{EmergencyLevel} feature determines the emergency level of an ongoing hazard which may currently affect the user.
Two different levels are distinguished, \emph{Low} and \emph{High}, depending on the severity of the hazard.
As we consider a cold weather hazard to be less dangerous than a flood, their emergency levels are low and high, respectively.
The emergency level of a hazard determines how users will be informed about the emergency.
In case of low emergency level, only warning messages are sent to the user.
In case of high emergency, the application may issue loud sounds and more intrusive message alerts instead.
The severity, duration or even the location of the ongoing hazard can be indicated in these messages.
For simplicity, let us assume that the \emph{Emergency Level} is implemented as a mere integer variable.
%Martou et al.~\cite{Martou2023CTTVisionPaper} define the \emph{Emergency Level} as a simple integer variable.
A value 0 means that there is no ongoing hazard. 
The variable is set to 1 when an emergency of low level occurs, and
is set to 2 if it has a high emergency level.
When multiple hazards with different emergency levels occur simultaneously, the highest emergency level takes precedence and overrides a lower emergency level.



## Requirements

The only requirement to run this prototype is a standard installation Python3 (preferably version 3.7 and above).

Note that old Python3 installations might not contain the module _Tkinter_ by default. If this is the case, you can install it on Linux with : 
```
sudo apt-get install python3-tk
```

## Usage

To start, please clone the repo and run the main file _main.py_ with no argument. Further instructions are provided within the prototype itself.

We provide three different modes:
- "CIT" will simulate the test suite generated by Combinatorial Interaction Testing (CIT) shown in Table 1. It only finds the interaction error.
- "transition" will illustrate both transition errors described in Section 2 by simulating the associated transitions.
- "free" will let you explore the prototype at your own discretion.

Feel free to explore the code.
