# Primii paşi în Git

În acest capitol vom vedea câteva comenzi de bază ale git, vom trece prin ele destul de succint și ca să înțelegeți mai bine tot procesul, ar fi recomandat să vă jucați puțin mai mult cu comenzile să vă intre puțin în reflex.

{% hint style="info" %}
Vom folosi termeni în limba engleză exclusiv deoarece așa îi veți găsi peste tot pe internet și vă va fi mai ușor să folosiți git.
{% endhint %}

## 🚩 Termeni de bază

Acești câțiva termeni sunt de bază în git, vom defini pe scurt aici de înseamnă, dar vor fi explicați mai pe larg în următoarele capitole. **Nu** este o listă exhaustivă.

1. **working directory** - folderul cu proiectul tău
2. **repository** - este practic folderul `.git` din proiectul tau. Acesta poate fi local \(i.e. calculatorul tău\) și/sau remote \(i.e. pe GitHub\). Creat cu`git init` sau `git clone`.  **Acesta conține baza de date** cu modificările în timp în proiectul tău.
3. **changes** - modificările pe care le-ai făcut în codul tău sursă
4. **staging** - "zona" în care change-urile sunt pregătite să fie salvate. Comanda `git add`
5. **commit** - operația de salvare a modificărilor în baza de date git. Comanda `git commit`

## ⚒Primul proiect cu git

Înainte de a face primul proiect cu git, este nevoie să îi "_găsești locul_", adică undeva prin calculatorul tău. Creaază mai întâi un folder unde dorești să te joci cu git. Vei avea nevoie și de un Terminal \(Linux, MacOS\) sau Command Line \(Windows\).

{% tabs %}
{% tab title="Windows" %}
În Windows puteți folosi și Command Line, PowerShell, sau Git Bash dacă faceți Click Dreapta în folderul cu proiectul vostru.

![](../../.gitbook/assets/image%20%285%29.png)

{% hint style="info" %}
**Tip:** Puteți instala un Terminal de Linux în Windows. Este chiar recomandat deoarece veți folosi destul de mult un terminal de Linux la laboratoare în facultate și este mult mai versatil și simplu de folosit. Nu aveți nevoie de mașină virtuală. Aflați mai multe despre [Windows Subsystem for Linux](https://devblogs.microsoft.com/commandline/an-in-depth-tutorial-on-linux-development-on-windows-with-wsl-and-visual-studio-code/).
{% endhint %}
{% endtab %}

{% tab title="MacOS" %}
![https://www.howtogeek.com/210147/how-to-open-terminal-in-the-current-os-x-finder-location/](../../.gitbook/assets/image%20%286%29.png)
{% endtab %}

{% tab title="Linux" %}
![groovypost.com/howto/open-command-window-terminal-window-specific-folder-windows-mac-linux/](../../.gitbook/assets/image%20%284%29.png)
{% endtab %}
{% endtabs %}

{% hint style="danger" %}
**Toate comenzile vor fi în varianta de Linux \(și implicit MacOS\).** Comenzile pentru PowerShell vor fi la fel. Unde e cazul, vor fi specificate diferențele.

* **Caracterul `$` nu trebuie copiat,** el doar denotă o comandă de rulat.
* **Caracterul `#` denotă un comentariu**, ****nu trebuie copiat.
* **Caracterele `[ ]` și conținut înăuntrul lor** reprezintă text care diferă de la calculator la calculator, iar în unele cazuri va trebui să înlocuiți cu cazul vostru.
{% endhint %}

### git init

Acum că suntem în folderul pentru proiect, putem inițializa git:

```bash
$ git init
Initialized empty Git repository in [path_spre_folder]/.git/
```

Comanda `init` va crea un **repository local** \(pe scurt repo\), adică un folder `.git` în folderul curent. Acesta este ascuns și conține întreaga bază de date cu toate modificările pe care le veți face în proiect.

**Notă:** Puteți crea un repo și într-un proiect deja început, nu e nevoie să fie gol folderul.

### git status

Acum că aveți repo-ul, puteți crea fișiere în proiectul vostru. Vom începe cu un simplu `myfile.txt`. În Terminal puteți folosi comanda `touch myfile.txt` pentru a crea un fișier gol. În Windows va fi mai simplu cu un `Click Dreapta > New > Text Document`.

Folosind comanda `git status` puteți vedea modificările curente. Citiți ce spune comanda, e chiar destul de simplu de înțeles.

```bash
$ git status # iar output-ul este următorul
On branch master # la încept avem un singur branch

No commits yet # încă nu am făcut nici un commit

Untracked files: # acestea sunt fișiere care sunt „unstaged”
  (use "git add <file>..." to include in what will be committed)

        myfile.txt

nothing added to commit but untracked files present (use "git add" to track)
```

### git add

În continuare dorim să salvăm acest fișier în repo. Pentru a putea face asta, îl _stage-uim_, adică îi spunem la git „bă, am câteva fișiere pe care vreau să le salvez acolo la tine”.

```bash
# varianta 1
$ git add myfile.txt # această comandă va face stage la fișierul specificat.

# varianta 2
$ git add . # cu acel punct, facem stage la toate fișierele modificate.
            # nu întotdeauna vrem să facem asta, de exemplu
            # știm că există fișiere unde avem greșeli iar pe alea
            # încă nu vrem să le salvăm

# aceste comenzi nu afișează nimic

# iar acum dacă rulăm git status putem observa fișierele gata de commit
$ git status
On branch master

No commits yet

Changes to be committed: # <----------- vedeți diferența față de înainte
  (use "git rm --cached <file>..." to unstage)

        new file:   myfile.txt
```

### git commit

Acum suntem pregătiți să facem commit. **Atenție**, este necesar să atribuiți fiecărui commit un mesaj care explică ce s-a întâmplat în commit-ul respectiv. Vă va fi mult mai simplu mai târziu să găsiți un anume commit.

```bash
$ git commit -m "[un mesaj explicativ]"
 
[master (root-commit) cbd022c] primul meu commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 myfile.txt
```

### git log

În timp, veți face tot mai multe commit-uri. Le puteți vedea pe toate folosind `git log`. Între timp am mai creat câteva fișiere `file1.txt file2.txt file3.txt`.

```bash
$ git log --oneline # am folosit comanda --oneline pentru a scurta output-ul

b08acc1 (HEAD -> master) uitați ce frumos se vede
508d68e al treilea fisier
6e5b780 al doilea fisier
92d5a26 primul meu commit
```

Grafic, în momentul de față cam așa arată repo-ul vostru.

![](../../.gitbook/assets/image%20%281%29.png)

### git diff

Dacă până aici nu v-a impresionat nimic, acum e momentul să băgați în fișiere ceva text. Puteți da copy paste la niște [Lorem Ipsum](https://www.lipsum.com/). După ce faceți asta, rulați comanda `git diff`.

```bash
$ git diff

diff --git a/myfile.txt b/myfile.txt
index e69de29..62a062e 100644
--- a/myfile.txt
+++ b/myfile.txt
@@ -0,0 +1,7 @@ # Aici vă afișează cu + tot ce ați adăugat.
+Lorem Ipsum is simply dummy text of the printing and typesetting industry.
+
+Lorem Ipsum has been the industry's standard dummy text ever since the 1500s,
+when an unknown printer took a galley of type and scrambled it to make a type specimen book.
+It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged.
+It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages,
+and more recently with desktop publishing software like Aldus PageMaker including versions of Lorem Ipsum.
```

Acum puteți rula `git add .` iar dacă faceți din nou câteva modificări în fișier, veți vedea cu + și/sau - ce ați adăugat respectiv șters.

```bash
$ git diff

diff --git a/myfile.txt b/myfile.txt
index 62a062e..368b619 100644
--- a/myfile.txt
+++ b/myfile.txt
@@ -1,6 +1,5 @@
 Lorem Ipsum is simply dummy text of the printing and typesetting industry.
# am sters linia asta \/
-Lorem Ipsum has been the industry's standard dummy text ever since the 1500s,
 when an unknown printer took a galley of type and scrambled it to make a type specimen book.
 It has survived not only five centuries, but also the leap into electronic typesetting, remaining essentially unchanged.
 It was popularised in the 1960s with the release of Letraset sheets containing Lorem Ipsum passages,
```

După ce faceți commit, git vă spune pe scurt ce a făcut acel commit.

```bash
$ git commit -m "am facut modificari"

[master 7e38969] am facut modificari
 1 file changed, 6 insertions(+) # <------------
```

## Concluzie

Am descris pe scurt termenii importanți în git pentru a ne înțelege mai ușor, am creat primul nostru proiect cu `git init`, am creat un fișier și am rulat `git status` pentru a observa cum git știe că avem modificări nesalvate. Am continuat prin a rula `git add` să facem _stage_ la fișierul respectiv, iar cu `git commit` am salvat modificările în repo. După ce am mai făcut câteva commit-uri, am văzut cum `git log` ne poate arăta istoricul commit-urilor și denumirile lor. Ultima comandă pe care am folosit-o este `git diff`, cu care am putut vedea modificările pe care le-am făcut prin fișiere, linie cu linie, ce am adăugat și ce am șters.

