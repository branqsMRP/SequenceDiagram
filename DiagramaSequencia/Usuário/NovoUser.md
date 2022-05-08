````mermaid
sequenceDiagram

    % trocar as classes pelas corretas
    actor A as Administrador
    participant S as Sistema
    participant VC as Valida Cadastro
    participant C as Cadastro

    A->>S: Cadastro de usuário
    activate A
    activate S

    alt Campo ID preenchido
        S->>VC: cadUser()
        activate VC
        VC->>C: cadUserOK()
        activate C
        C-->>S: Cadastro
        deactivate C
        deactivate VC
    else Campo ID não preenchido
        S->>VC: cadUser()
        activate VC
        VC-->>S: ID do Usuário deve ser preenchido
        deactivate VC
    end

    S->>A: Cadastro concluído
    deactivate S
    deactivate A
````