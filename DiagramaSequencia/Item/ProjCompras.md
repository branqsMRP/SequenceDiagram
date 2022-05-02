````mermaid
sequenceDiagram

% diagrama da tela de Projeção de Compras

    actor CA as Compras/Admin
    participant S as Sistema
    participant IM as Inclusão Material
    participant VI as Verificador Inclusão
    participant LM as Lista Material 
    participant P as Projeção

    CA->>S: Projeção de Compras
    activate S
    S->>IM: inclusaoMaterial()
    % alterar depois para ter a classe correta
    activate IM
    
    alt Está preenchido
    IM->>VI: materialOK()
    VI->>LM: 
    else Não está preenchido
    end
````