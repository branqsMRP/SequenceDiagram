````mermaid 
sequenceDiagram

    % alterar as classes depois para ter a classe correta
    actor AA as Admin/Almoxarifado
    participant S as Sistema
    participant IM as Inclusão Material 
    participant VI as Valida Inclusão
    participant LM as Lista Material
    participant VP as Valida Previsão
    participant PM as Previsão Movimentação 

    AA->>S: Incluir os materiais para Produção
    activate AA
    activate S
    S->>IM: inclusaoMaterial()
    activate IM
    
    alt Está preenchido
    IM->>VI: materialOK()
    activate VI
    VI->>LM: listaMaterial()
    activate LM
        opt Exclusão item selecionado
            LM-->>IM: Inclua novamente. 
            deactivate LM
        end
    else Não está preenchido
    VI-->>IM: Erro Inclusão
    deactivate VI
    end

    alt Enquanto há itens no estoque
    LM->>VP: validaPrev()
    activate LM
    activate VP
    VP->>PM: previsaoMov()
    activate PM
    PM-->>S: Previsão de Movimentação de lote conluída 
    deactivate IM
    deactivate S
    else não há itens no estoque
    VP->>PM: excluirEstoque()
    PM-->>LM: Itens excluidos do lote
    deactivate PM
    deactivate VP
    deactivate LM
    end
        
    S->>AA: Previsão de lote
    activate S
    deactivate S
    deactivate AA
````