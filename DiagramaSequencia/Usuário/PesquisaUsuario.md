````mermaid
sequenceDiagram

    actor A as Administrador
    participant S as Sistema
    participant P as Pesquisa

    A->>S: Busca de Usuario
    activate A
    activate S

    S->>P: buscUser()
    activate P
    P-->>S: resultPesq()
    deactivate P

    S->>A: Pesquisa Concluida
    deactivate S
    deactivate A
````