# Technische keuzes en architectuur

Abacus zal worden gedraaid op een gesloten netwerk zonder internettoegang. De backend draait op één machine en kan via de webbrowser (frontend) worden benaderd vanaf andere computers op het netwerk.

Voor de frontend wordt TypeScript gebruikt, een meer uitgebreide versie van JavaScript met typing. Voor de gebruikersinterface wordt de populaire library React gebruikt.

De backend wordt gemaakt met Rust, een high-level programmeertaal waarmee je efficiënt kunt programmeren. Het unieke systeem van '[ownership](https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html)' in Rust voorkomt geheugenfouten, en de taal heeft een '[strict type system](https://doc.rust-lang.org/book/ch03-02-data-types.html)' waardoor minder bugs ontstaan. Ook is dit een populaire, open-source programmeertaal met een grote community.

Voor de database wordt SQLite gebruikt. Deze library is populair, lichtgewicht en gebruiksvriendelijk voor developers, en bovendien is SQLite een '[zero-configuration database](https://www.sqlite.org/zeroconf.html)'. Dit betekent dat installeren niet nodig is, zodat de developer meteen aan de slag kan.

Voor meer informatie over onze keuzes en de onderbouwingen hiervan lees je het document [Overwegingen talen en frameworks](https://github.com/kiesraad/abacus/blob/main/documentatie/softwarearchitectuur/overwegingen-talen-en-frameworks.md).

Voor de architectuur kun je beginnen bij het [Overzicht van de softwarearchitectuur](https://github.com/kiesraad/abacus/blob/main/documentatie/softwarearchitectuur/Overzicht.md).

De UI/UX designs vind je in onze [Figma](https://www.figma.com/design/xHDfsv69Nhmk3IrWC0303B/Public---Kiesraad---Abacus-optelsoftware?node-id=3190-28385&t=VnghjibSJMqrQepm-1).
