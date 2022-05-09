````mermaid
sequenceDiagram

    actor A as Administrador
    participant S as Sistema
    participant P as Pesquisa

    % pesquisa por ID 

    A->>S: ID Usuário
    activate A
    activate S

    S->>P: buscarUsuario(idUsuario)
    activate P
    P-->>S: ID Usuario
    deactivate P

    S->>A: ID Usuario
    deactivate S
    deactivate A

    % pesquisa por nome

    A->>S: Nome
    activate A
    activate S

    S->>P: buscarUsuario(nome)
    activate P
    P-->>S: Nome
    deactivate P

    S->>A: Nome
    deactivate S
    deactivate A

    % pesquisa por perfil 

    A->>S: Perfil
    activate A
    activate S

    S->>P: buscarUsuario(perfil)
    activate P
    P-->>S: Perfil
    deactivate P

    S->>A: Perfil
    deactivate S
    deactivate A

    % pesquisa por ativo

    A->>S: Ativo
    activate A
    activate S

    S->>P: buscarUsuario(ativo)
    activate P
    P-->>S: Ativo
    deactivate P

    S->>A: Ativo
    deactivate S
    deactivate A
````