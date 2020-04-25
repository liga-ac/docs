# Cum instalăm Git?

Bineînțeles, Git este valabil atât pe Windows, cât și pe MacOS și Linux. Vom lua pe rând fiecare.

{% tabs %}
{% tab title="Windows" %}
Cea mai simplă metodă de instalare pe Windows este prin executabilul oficial.

1. **Descarcă** executabilul de pe [git-scm.com](https://git-scm.com).
2. **Rulează executabilul** și continuă instalarea. Setările default ar trebui să fie ok, dar te rugăm să citești întotdeauna ce scrie în _wizard_ pentru a nu întâmpina probleme.
3. **Intră în Command Line** \(caută `cmd` în Start\) și rulează comanda:

   ```text
   C:\users\userultău> git --version
   git version 2.26.1.windows.1
   ```

   _Versiunea afișată poate să difere._

4. **Configurează username-ul și email-ul** cu care vor fi asociate modificările în codul sursă. \(tot în Command Line\). Înlocuiește user-ul și email-ul între ghilimele.

   ```text
   git config --global user.name "John Smith"
   git config --global user.email "johm.smith@gmail.com"
   ```

{% hint style="danger" %}
**Dacă comenzile nu funcționează**, verifică în Control Panel dacă este într-adevăr instalat Git. Dacă nu, mergi înapoi la 1. Dacă da, încearcă să dai un restart la calculator.
{% endhint %}
{% endtab %}

{% tab title="Linux" %}
Vom folosi Ubuntu ca și exemplu.

1. **Deschide Terminal-ul** cu combinația de taste `Ctrl + Alt + T`
2. **Instalează Git** cu `apt-get`

   ```text
   sudo apt-get update
   sudo apt-get install git
   ```

3. **Verifică** dacă instalarea a avut succes.

   ```text
   git --version
   git version 2.26.1.windows.1
   ```

   _Versiunea afișată poate să difere._

4. **Configurează username-ul și email-ul** cu care vor fi asociate modificările în codul sursă. \(tot în Command Line\). Înlocuiește user-ul și email-ul între ghilimele.

   ```text
   git config --global user.name "John Smith"
   git config --global user.email "johm.smith@gmail.com"
   ```

{% hint style="danger" %}
**Dacă comenzile nu funcționează**, verifică să nu fi rulat git cu sudo, încearcă să redeschizi terminalul, sau restartează calculatorul.
{% endhint %}
{% endtab %}

{% tab title="MacOS" %}
Pe MacOS de asemenea există un executabil, pe care îl găsești pe [git-scm.com](https://git-scm.com), dar de data asta vom alege [Homebrew](https://brew.sh/), deoarece vă veți întâlni cu el în viitor.

1. **Deschide Terminal-ul**. Poți prin a deschide Spotlight \(Cmd + Space\) și scriind „Terminal”.
2. **Instalează Homebrew**. Folosește comanda de mai jos și urmărește cerințele ce apar în terminal.

   ```text
   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
   ```

3. **Instalează git**.

   ```text
   brew install git
   ```

4. **Verifică** dacă instalarea a avut succes.

   ```text
   git --version
   git version 2.26.1.windows.1
   ```

   _Versiunea afișată poate să difere._

5. **Configurează username-ul și email-ul** cu care vor fi asociate modificările în codul sursă. \(tot în Command Line\). Înlocuiește user-ul și email-ul între ghilimele.

   ```text
   git config --global user.name "John Smith"
   git config --global user.email "johm.smith@gmail.com"
   ```
{% endtab %}
{% endtabs %}

Acum că l-ai instalat, poți continua să faci **Primii pași în Git...**

