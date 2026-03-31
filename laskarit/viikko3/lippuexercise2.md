sequenceDiagram
    %% Participants
    participant Main as main()
    participant Laitehallinto as HKLLaitehallinto
    participant Lataaja as Lataajalaite(rautatietori)
    participant Lukija1 as Lukijalaite(ratikka6)
    participant Lukija2 as Lukijalaite(bussi244)
    participant Kioski as Kioski(lippu_luukku)
    participant Kortti as Matkakortti(kallen_kortti)

    %% Object creation
    activate Main
    Main->>Laitehallinto: create HKLLaitehallinto()
    activate Laitehallinto
    deactivate Laitehallinto

    Main->>Lataaja: create Lataajalaite()
    activate Lataaja
    deactivate Lataaja

    Main->>Lukija1: create Lukijalaite()
    activate Lukija1
    deactivate Lukija1

    Main->>Lukija2: create Lukijalaite()
    activate Lukija2
    deactivate Lukija2

    Main->>Kioski: create Kioski()
    activate Kioski
    deactivate Kioski

    %% Adding devices to management
    Main->>Laitehallinto: lisaa_lataaja(rautatietori)
    Main->>Laitehallinto: lisaa_lukija(ratikka6)
    Main->>Laitehallinto: lisaa_lukija(bussi244)

    %% Buying a travel card
    Main->>Kioski: osta_matkakortti("Kalle")
    activate Kioski

    Kioski->>Kortti: create Matkakortti("Kalle")
    Kortti-->>Kioski: return kallen_kortti

    Kioski-->>Main: return kallen_kortti
    deactivate Kioski





    %% Loading value
    Main->>Lataaja: lataa_arvoa(Kortti, 3)
    activate Lataaja
    Lataaja->>Kortti: kasvata_arvoa(3)
    deactivate Lataaja

    %% Buying tickets
    Main->>Lukija1: osta_lippu(Kortti, 0)
    activate Lukija1
    Lukija1->>Kortti: vahenna_arvoa(1.5)
    deactivate Lukija1

    Main->>Lukija2: osta_lippu(Kortti, 2)
    activate Lukija2
    Lukija2->>Kortti: vahenna_arvoa(3.5)
    deactivate Lukija2

deactivate Main