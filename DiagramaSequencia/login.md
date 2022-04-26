```mermaid
sequenceDiagram
    % diagrama da tela de Login
    actor Colaborador
    actor Sistema
    Sistema->>Colaborador: Você não está logado.
    Colaborador->>Sistema: Login()
    Colaborador->>Sistema: Senha() 
    Sistema-->>Colaborador: Você está logado!
```