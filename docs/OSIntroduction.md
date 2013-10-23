###01.10.2013
Links
- hard links (physical links)
- soft links (referenza), ciano, rosso se non esiste referenza, si usano questi

cut, paste per csv
cut -d “;” -f 1 t.csv

redirezione errore
comando 2> file


Permessi
-rw-rw-r-- 1 christianf christianf  121 ott  1 11:23 test 
				utente      gruppo   data ultima mod   nome

user group others all

r+u (read per utente)
w-go (meno write per group e others)

###02.10.2013
Software libero
codice sorgente, licenza non restritiva, modificabile e devo poter distribuire le modifiche
OpenSource


apt-get install tree
va in /var/cache/apt/archives

//rimuovere file in /var/cache/apt/archives
apt-get clean

//per aggiornare pacchetti alle versioni più recenti
apt-get upgrade

//per aggiornare da 13.04 a 13.10
//cambiare /etc/apt/sources.list al nuovo nome dist
apt-get update
apt-get dist-upgrade

//ripara installazioni di pacchetti rotti
apt-get -f install
dpkg-reconfigure -a

//rimuovi programma
apt-get remove ...

//rimuovi programma e file di configurazioni
apt-get purge …

//rimuovi pacchetti e dipendenza non più usate
apt-get autoremove

//per reinstallare pacchetto anche se presente
apt-get –reinstall install ..

//per simulare installamento, deletamento, etc
apt-get –simulate install/remove/purge/etc

//installare pacchetto .deb (anche con --simulate)
dpkg -i xyz.deb
// -i installa

//a quale pacchetto appartiene un file
dpkg -L file

//qual'è il pacchetto a cui appartiene il file
dpkg -S file



RETI

route -n
//default gateway, per vedere la configurazione del cancello per fuori

subnet mask AND ip

subnet mask definisce indirizzi per il server e per i client




###03.10.2013
ESPRESSIONI REGOLARI
metacaratteri
^ inizio della riga
$ fine della riga
. qualsiasi carattere
\ escape un carattere, interpretalo letteralmente
| or
() un gruppo di caratteri, una serie di caratteri
[] intervalli o classi di caratteri

esempio
[abc] = a,b o c
[a-d] = a,b,c o d
[a-z] = una lettera minuscola
[a-zA-Z] = una lettera 
[0-9] = un numero
[^a] = tutti i caratteri tranne che a
[^abc] = tutti i caratteri tranne che a,b e c

quantificatori, quantifiers
* zero o più volte	(greedy)
+ 1 o più volte		(greedy)
? 0 o 1 volta
{n} n volte
{n,m} n fino a m volte
{n,} almeno n volte

(greedy) sono golosi, cercano di far corrsipondere il pezzo di testo più lungo possibile
es.
uno "due" "tre"
".*"
estrae ^"due" "tre"^

1) se metto un ? dopo un quantificatore diventa non greedy
".*?"
prende "due"

2)
"[^"]"
prende "due"

Quando facciamo un gruppo abbiamo due effetti:
usare un quantificatore dopo
o
assegnare quel gruppo di caratteri ad una variabile

es.
(..)..(..)
in vi con \1 e \2, in altri con $1 e $2


es. in vi

aaa:bbb
aa:bb
abc:abcd

regex: 1,$ s/\(.*\):\(.*\)/\2:\1/



Per sostituire tutti i domain di link in href con google.it

<a href="http://redoddity.it/pippo.html">redoddity.it</a>
<a href="https://pippo.it" style="display:inline-block;">vai su http://redoddity.com</a>

1,$ s/\(href="https\?:\/\/\)[0-9a-z\.\-]\+/\1google.it


P.IVA
02418690216
REGEX:
	1,$ /[0-9]\{11\}/

Codice Fiscale
FEICRS93A07A952H
REGEX:
	1,$ /[A-Z]\{6\}[0-9]\{2\}[A-O][0-9]\{2\}[A-Z][0-9]\{3\}[A-Z]/

IPv4
127.0.0.1
REGEX:
	1,$ s/\([0-9]\{1,3\}\.\)\{3\}[0-9]\{1,3\}
	1,$ s/\(\(2[0-5][0-9]\)\|\(1[0-9][0-9]\)\|\([1-9][0-9]\)\|\([0-9]\)\)\.\(\(2[0-5][0-9]\)\|\(1[0-9][0-9]\)\|\([1-9][0-9]\)\|\([0-9]\)\)\.\(\(2[0-5][0-9]\)\|\(1[0-9][0-9]\)\|\([1-9][0-9]\)\|\([0-9]\)\)\.\(\(2[0-5][0-9]\)\|\(1[0-9][0-9]\)\|\([1-9][0-9]\)\|\([0-9]\)\)/
	1,$ s/
		\(
			\([0-9]\)\|
			\([0-9]{2}\)\|
			\(1[0-9]{2}\)\|
			\(2[0-4][0-9]\)\|
			\(25[0-5]\)\|
		\)
	\)/



###04/10/2013

export VAR 
crea variabile d'ambiente, accessibile a tutti i figli

PIPPO="pippo"
echo $PIPPO

bash
//per creare una nuova istanza di una bash

ps
//vedere i processi lanciati da questa shell

######CICLO FOR
for i in .....;
do comando;done



###Servizi
in /etc/init.d/

service SERVIZIO OPTION

###runlevels
per avviare/stoppare servizi a diversi stati del pc

il pc ha 2 

file di configurazione di un runlevel sono in /etc/rc2.d/
ci stanno i link per i script
sintassi
S(per start)XYZ(ordine)nome
c'e' anche K(per kill)

vale solo per servizi in /etc/init.d/

Configurazioni di apache risiedono in /etc/apache2

mods-available ci stanno tutti i mod a disp
mods-enabled contengono link a mods-available

in /etc/php5/apache2/php.ini ci sono le conf di php
come max file size, mem limit


in /etc/apache2/sites-available
troviamo la configurazione del sito default

deve essere leggibile da www-data, dall'utente che serve i siti web

/etc/hosts dove definiamo il nome fasullo

/etc/apache2/sites-available/ mettere la configurazione

/etc/apache2/sites-enabled/ il link verso available

/home/christianf/siti/ dove mettiamo i nostri siti

/var/log/apache2/ troviamo i log