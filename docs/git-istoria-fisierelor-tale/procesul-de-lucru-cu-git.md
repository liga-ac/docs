# Procesul de lucru cu Git

Ca să putem înțelege mai bine git și cum funcționează el, este important să înțelegem câteva principii de bază în git, cum ar fi: ce este un remote, ce sunt branch-urile și cum le folosim, ce sunt conflictele, când apar ele, și nu numai. Vom încerca însă să menținem lucrurile cât mai simple.

## 💻 Local vs. Remote

În general veți folosi o platformă de genul GitHub, GitLab, etc. unde vă veți ține codul. Acestea se folosesc de sistemul git pentru a putea și ele reține toate modificările la codul vostru, dar ele fac mult mai multe. Vom trece prin câteva exemple pe pagina despre [GitHub](github.md).

![https://backlog.com/git-tutorial/creating-a-repository/](../../.gitbook/assets/image%20%2810%29.png)

Remote-ul este acel repository care este practic un "source of truth", adică repo-ul care se află pe una din platformele menționate mai sus. Toate repo-urile locale comunică cu cel remote.

Tu când vrei să lucrezi la proiect, iei de pe remote ultimele modificări, lucrezi ce lucrezi, iar la finalul zilei urci modificările pentru a le putea accesa și camarazii tăi.

{% hint style="info" %}
**Tip:** Un repo remote poate fi asociat cu Google Drive sau Dropbox. Când faci modificări la un fișier la tine pe calculator, îl încari pe Google Drive/Dropbox, același lucru se aplică și în git, dar puțin mai avansat.
{% endhint %}

> Pentru a adăuga un remote la repo-ul tău creat mai devreme, vei folosi comanda`git remote add origin <url>` unde URL-ul îl luați de pe platforma unde ați creat repo-ul remote.

## ⌨ Lucrul cu un repo remote

Când lucrăm cu un repository remote, apar câteva variabile în plus. În cazul în care lucrezi singur pe un proiect, treabă stă destul de simplu.

![&#xAF;\\_\(&#x30C4;\)\_/&#xAF;](../../.gitbook/assets/image%20%282%29.png)

În afară de punctul 3, cam așa stă treaba.

### 🤺 git push

Știm că `git commit` salvează modificările în repo-ul local, ei bine `git push` ia commit-urile respective și le încarcă în repo-ul remote.

```bash
$ git push origin master
```

{% hint style="info" %}
`master` este branch-ul default. Vom explica ce sunt branch-urile mai jos.
{% endhint %}

În principiu, oricând faci modificări este recomandat să le faci push. Nu este nevoie la fiecare commit să faci asta, poți face câte commit-uri locale dorești, iar când crezi că e momentul, le faci push pe remote. O dată ce le-ai push-uit, acestea vor fi vizibile pe platforma ce o folosești.

![&#xCE;nainte de push vs. dup&#x103; push. Modific&#x103;rile locale au fost aplicate pe remote.](../../.gitbook/assets/image%20%281%29.png)

{% hint style="info" %}
**Ne aducem aminte:** Când am rulat `git remote add`**`origin`**`<url>`, am pus la remote denumirea "**origin**". Aceasta poate fi orice, dar în general veți vedea origin.

În exemplul de mai sus, **origin master** este repo-ul remote, iar atunci când facem push, modificările din **master**-ul local vor fi aplicate în remote.
{% endhint %}

**O dată ce începi să lucrezi cu alte persoane pe un proiect**, trebuie să fii atent la mai multe lucruri. În primul rând dacă nu ai destulă experiență, este bine să colaborați și să nu lucrați amândoi pe acceași bucată de cod în același timp. O dată ce faceți amândoi push la același fișier, este aproape sigur că veți întâmpina conflicte, care, pot să vă provoace dureri de cap dacă nu sunteți atenți, iar acest lucru vă spun din experiență 🤷‍♂️.

**Apar comenzi noi cu care veți lucra.** Va trebui să faceți `fetch` la modificări, să puteți vedea cine ce a modificat, unde și cum. În plus, ca să adăugați codul scris de restul în local, trebuie să faceți `pull`. Această operație iarăși **poate genera conflicte** dacă altcineva a făcut `push` la fișiere unde ai lucrat și tu, dar nu ai făcut `commit` sau `stash`.

Sunt multe comenzi? Stai liniștit, nu e atâta de greu pe cât pare.

### 📉 git fetch

O operație „non-destructivă”. Când o rulezi, aceasta cere la remote toate commit-urile ce s-au mai făcut, dar nu le și aplică peste repo-ul local. Aceasta o folosești înainte de a face pull. Altfel, git nu va ști dacă există modificări noi.

```bash
$ git fetch origin
```

### 📥 git pull

Faci `pull` atunci când vrei să aplici modificările de pe remote la tine în repo-ul local.

```bash
$ git pull origin
```

`Pull` este o operație „destructivă”. Aceasta va adăuga toate modificările de pe remote în repo-ul vostru. Este important să știți că dacă faceți `pull` dar aveți modificări la care nu ați făcut `commit`, vă veți trezi cu conflicte. Oricând vreți să faceți `pull`, faceți `commit` înainte.

### 📦 git stash

În `git stash` nu vom intra în detaliu deoarece nu îl veți folosi prea des. In layman's terms, se poate spune că el pune modificările curente într-o cutie, le lasă în colțul camerei, iar când ai nevoie de ele mai târziu le scoți și le aplici peste ce ai. Poți citi mai multe în [documentația oficială](https://git-scm.com/docs/git-stash).

## 🤷‍♂️Ce este un branch?

Ca să simplificăm puțin lucrurile, imaginați-vă un copac. Plantatul copacului se poate asocia cu `git init`. În timp, acest copac crește, lucru care se poate asocia cu fiecare `git commit`. Trunchiul se numește **master**, deoarece din trunchi ies crengile copacului. În timp, acest copac cum tot crește, îi pot ieși și crengi. Aceste crengi putem spune că **derivă din master**. Aceste crengi pot în continuare să aibă alte crengi, și tot așa.

Un repo de git funcționează aproape la fel ca un copac, dar în git, aceste crengi se pot _îmbina înapoi_ în **master**, proces care se numește **merge**.

## 🤨 Exemplu de flow

Să ne imaginăm un proiect mai mare. În general **master** conține cod stabil, care este ok de utilizat. Din **master**, derivă alte branch-uri, de exemplu cel de **develop**, care conține cod în lucru de programatori. Acest branch mai are la rândul lui alte branch-uri derivate pentru diverse **feature**-uri, care atunci când sunt gata se pot integra \(**merge**\) înapoi în **develop**. Atunci când se consideră codul gata de un **release**, se face merge acestuia cu branch-ul respectiv, care automat va fi **merge**-uit și cu **master**.

Dacă nu înțelegeți prea bine ce se întâmplă, nu vă faceți griji. Cu cât lucrați mai mult cu git veți înțelege.

![](../../.gitbook/assets/image%20%289%29.png)







