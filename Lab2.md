What is the Address Resolution Protocol (ARP), and what is its role in a network?

    ARP protokol sluzi za mapiranje IP adresa verzije 4 ili 6 u MAC (Media Access Control) adresu koju svako racunalo dobija unaprijed pri proizvodnji NIC-a (Network Interface Card - najcesce ugradeno u maticne).
    Protokol osigurava ispravno prijevodenje sa tih razlicitih adresa koje nisu iste duzine te se time racunala u lokalnoj mrezi mogu prepoznati kada ih netko izvan njihove lokalne mreze zeli kontaktirati preko njihove javne IP adrese.

What is a Man-in-the-Middle (MitM) attack, and how does ARP spoofing enable it?

    MitM napad je vrsta malicioznog napada u kojem napadac sebe predstavlja kao tocku u komunikaciji izmedu dva uredaja i pokusava presresti podatke prije nego sto dodu do krajnje tocke u komunikaciji. ARP spoofing je nacin za izvodenje tog napada kroz predstavljanje napadaceve MAC adrese kao prave i slanje ARP odgovora kako bi ga mreza(router) prepoznala kao legitimnu tocku komunikacije.

How does an attacker use ARP spoofing to intercept network traffic?

    Neki od clanova mreze salje ARP Request svim clanovima mreze kako bi na temelju IP adrese saznao MAC adresu trazenog racunala. Napadac kao i trazeni korisnik vidi taj request te posalje ARP Reply u kojem se predstavlja kao trazeni uredaj te za trazenu MAC adresu stavlja svoju adresu. Uredaj koji je slao request ne razumije da je rijec o napadacu te pocinje slati podatke na njegovu MAC adresu. Napadac ce te podatke proslijediti na ispravnu MAC adresu kako se ne bi odmah saznalo da je rijec o napadu ili kako bi uredaju sa ispravnom adresom proslijedio ne ispravne podatke.

How is the cookie used to derive the encryption/decryption key?

    Cookie se salje kao string u derive_key funkciju koja ga onda koristi kao seed za generiranje key-a preko moderne KDF funkcije Scrypt.

What REST API request do you need to send to the crypto oracle the secret cookie?

    GET /arp/cookie

How do you obtain the authentication token?

    Moramo zatraziti token od Oracle servera koristeci naredbu: POST username=my_name&password=my_pass /arp/token, ali on zahtjeva autentikaciju. Morat cemo izvrsiti MitM napad da bi ga dobili.

How do you use the authentication token to obtain the cookie?

    Moramo biti autentificirani ili se predstavljati kao vazeci korisnik koristeci token kako bi uspjesno mogli poslat GET /arp/cookie prema Oracle serveru.

What encryption mode is used to encrypt the challenge in this lab?

    Koristi se block cypher mode CBC, kojega nalazimo kao argument u jednoj od funkcija u crypto.py.

What tool can you use to capture network traffic on a local network interface?

    Koristimo TCPDUMP naredbu u konzoli.