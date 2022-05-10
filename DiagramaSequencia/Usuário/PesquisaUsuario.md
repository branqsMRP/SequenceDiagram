````mermaid
sequenceDiagram

    actor A as Administrador
    participant S as inputBuscaUser
    participant P as UsuarioBuscaAction

    % pesquisa por ID 

    A->>S: ID Usuário, Nome, Perfil, Ativo
    activate A
    activate S

    S->>P: buscarUsuario(idUsuario, nome, perfil, ativo)
    activate P
    P-->>S: Usuarios
    deactivate P

    S->>A: Lista Usuarios
    deactivate S
    deactivate A


````