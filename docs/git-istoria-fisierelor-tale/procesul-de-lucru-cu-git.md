# Procesul de lucru cu Git

## 💻 Local vs. Remote



## 🤷‍♂️ Ce este un branch?

Ca să simplificăm puțin lucrurile, imaginați-vă un copac. Plantatul copacului se poate asocia cu `git init`. În timp, acest copac crește, lucru care se poate asocia cu fiecare `git commit`. Trunchiul se numește **master**, deoarece din trunchi ies crengile copacului. În timp, acest copac cum tot crește, îi pot ieși și crengi. Aceste crengi putem spune că **derivă din master**. Aceste crengi pot în continuare să aibă alte crengi, și tot așa.

Un repo de git funcționează aproape la fel ca un copac, dar în git, aceste crengi se pot _îmbina înapoi_ în **master**, proces care se numește **merge**.

## 🤨Exemplu de flow

Să ne imaginăm un proiect mai mare. În general **master** conține cod stabil, care este ok pentru utilizat. Din master, derivă alte branch-uir, de exemplu cel de **develop**, care conține cod în lucru de programatori. Acest branch mai are la rândul lui alte branch-uri derivate pentru diverse **feature**-uri, care atunci când sunt gata se pot integra \(**merge**\) înapoi în develop. Atunci când se consideră codul gata de un **release**, se face merge acestuia cu branch-ul respectiv, care automat va fi **merge**-uit și cu **master**.

Dacă nu înțelegeți prea bine ce se întâmplă, nu vă faceți griji. Cu cât lucrați mai mult cu git veți înțelege.

![](../../.gitbook/assets/image%20%287%29.png)







