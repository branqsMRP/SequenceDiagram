````mermaid
sequenceDiagram

    actor U as Usuario
    participant S as Sistema
    participant A as Aplicação

    U->>S: Sair do sistema
    activate U
    activate S

    S->>A: logOff()
    activate A
    A-->>S: Logoff
    deactivate A

    S->>U: Usuário saiu do sistema com exito
    deactivate S
    deactivate U
````