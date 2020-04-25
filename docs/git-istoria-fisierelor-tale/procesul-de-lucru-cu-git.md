# Procesul de lucru cu Git

Ca să putem înțelege mai bine git și cum funcționează el, este important să înțelegem câteva principii de bază în git, cum ar fi: ce este un remote, ce sunt branch-urile și cum le folosim, ce sunt conflictele, când apar ele, și nu numai. Vom încerca însă să menținem lucrurile cât mai simple.

## 💻 Local vs. Remote

În general veți folosi o platformă de genul GitHub, GitLab, etc. unde vă veți ține codul. Acestea se folosesc de sistemul git pentru a putea și ele reține toate modificările la codul vostru, dar ele fac mult mai multe. Vom trece prin câteva exemple pe pagina despre [GitHub](github.md).

![https://backlog.com/git-tutorial/creating-a-repository/](../../.gitbook/assets/image%20%288%29.png)

Remote-ul este acel repository care este practic un "source of truth", adică repo-ul care se află pe una din platformele menționate mai sus. Toate repo-urile locale comunică cu cel remote.

Tu când vrei să lucrezi la proiect, iei de pe remote ultimele modificări, lucrezi ce lucrezi, iar la finalul zilei urci modificările pentru a le putea accesa și camarazii tăi.

> Pentru a adăuga un remote la repo-ul tău creat mai devreme, vei folosi comanda`git remote add origin <url>` unde URL-ul îl luați de pe platforma unde ați creat repo-ul remote.

## ⌨ Lucrul cu un repo remote



## 🤷‍♂️ Ce este un branch?

Ca să simplificăm puțin lucrurile, imaginați-vă un copac. Plantatul copacului se poate asocia cu `git init`. În timp, acest copac crește, lucru care se poate asocia cu fiecare `git commit`. Trunchiul se numește **master**, deoarece din trunchi ies crengile copacului. În timp, acest copac cum tot crește, îi pot ieși și crengi. Aceste crengi putem spune că **derivă din master**. Aceste crengi pot în continuare să aibă alte crengi, și tot așa.

Un repo de git funcționează aproape la fel ca un copac, dar în git, aceste crengi se pot _îmbina înapoi_ în **master**, proces care se numește **merge**.

## 🤨 Exemplu de flow

Să ne imaginăm un proiect mai mare. În general **master** conține cod stabil, care este ok pentru utilizat. Din master, derivă alte branch-uir, de exemplu cel de **develop**, care conține cod în lucru de programatori. Acest branch mai are la rândul lui alte branch-uri derivate pentru diverse **feature**-uri, care atunci când sunt gata se pot integra \(**merge**\) înapoi în develop. Atunci când se consideră codul gata de un **release**, se face merge acestuia cu branch-ul respectiv, care automat va fi **merge**-uit și cu **master**.

Dacă nu înțelegeți prea bine ce se întâmplă, nu vă faceți griji. Cu cât lucrați mai mult cu git veți înțelege.

![](../../.gitbook/assets/image%20%287%29.png)







