# Szubienica

Prosta gra Wisielec

# zasady
Jeden z graczy wpisuje słowo lub zdanie, a drugi gracz ma 10 szans na odgadnięcie hasła.

# Scenariusz gry
Przeanalizujmy przebieg przykładowej rozgrywki.

Note left of komputer: wylosowane slowo\n = `ALKOHOL`
komputer -> gracz: wylosowalem slowo
Note right of gracz: stan szubienicy = 0
Note left of komputer: `*******`

gracz --> komputer: czy jest w nim litera `a`?
komputer -> gracz: tak
Note left of komputer: `A******`

gracz --> komputer: czy jest w nim litera `e`?
komputer -> gracz: nie
Note right of gracz: stan szubienicy = 1

gracz --> komputer: czy jest w nim litera `i`?
komputer -> gracz: nie
Note right of gracz: stan szubienicy = 2

gracz --> komputer: czy jest w nim litera `o`?
komputer -> gracz: tak
Note left of komputer: `A**O*O*`

gracz --> komputer: czy jest w nim litera `m`?
komputer -> gracz: nie
Note right of gracz: stan szubienicy = 3

gracz --> komputer: czy jest w nim litera `l`?
komputer -> gracz: tak
Note left of komputer: `AL*O*OL`

gracz --> komputer: czy jest w nim litera `k`?
komputer -> gracz: tak
Note left of komputer: `ALKO*OL`

gracz --> komputer: czy jest w nim litera `h`?
komputer -> gracz: tak, wygrales !!!
Note left of komputer: `ALKOHOL`
Projekt
Rozgrywka - instancja Gry, obiekt utworzony z klasy Gra.
Gra - klasa dostarczająca wszystkich funkcjonalności rozgrywki (bieżący stan rozgrywki oraz metody umożliwiające obserwację rozgrywki).
Stan rozgrywki
W pierwszym kroku należy ustalić, w jaki sposób w obiekcie rozgrywka reprezentowany będzie jego stan.

Wyobraźmy sobie następującą sytuację - rozgrywka trwa i zostaje zahibernowana na pewien czas.

Pytanie: co i jak należy zapamiętać, aby można było tę rozgrywkę skutecznie odhibernować i ją kontynuować?

Na pewno musimy zapamiętać odgadywane słowo.
Ponadto musimy zapamiętać litery już odgadnięte.
I jeszcze musimy zapamiętać liczbę nieudanych prób - to na jej podstawie tworzona jest szubienica.
Dodatkowe ustalenia:

jeśli gracz dwu- lub wielokrotnie poda poprawną literę, nie skutkuje to dla niego negatywnymi konsekwencjami - po prostu otrzyma zwrotną informację, że litera jest w odgadywanym słowie,
jeśli gracz dwu- lub wielokrotnie poda niepoprawną literę, za każdym razem otrzyma odpowiedź, że litery nie ma w słowie i zwiększona będzie liczba nieudanych prób odgadnięcia,
jeśli gracz domyśla się brzmienia słowa, to musi kolejno podawać litery - nie może podać go w całości, aby zakończyć grę.
Ad. 1. Odgadywane słowo reprezentowane będzie przez string.

Ad. 2. Litery odgadnięte możemy zapamiętywać na liście List<char>, choć lepszym rozwiązaniem byłoby ich zapamiętanie w strukturze zbioru HashSet<char> - nie będą wtedy brane pod uwagę duplikaty.

Ad. 3. Liczba nieudanych prób może być reprezentowana przez zmienną typu int.

Listę odgarniętych liter oraz liczbę nieudanych prób możemy "zapamiętać" inaczej -- w formie wzorca do odgadnięcia (składającego się z symboli pustych, np. gwiazdki, i odgadniętych już liter) oraz aktualnego stanu szubienicy.

Aktualny wzorzec zapamiętamy w zmiennej typu StringBuilder -- ponieważ przy kolejnych trafieniach będziemy odsłaniać odpowiednie litery, a ten typ pozwala na swobodne operowanie na zawartości napisu.
