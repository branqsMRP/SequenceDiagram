````mermaid
sequenceDiagram

actor AA as Admin/Almoxarifado
participant S as Sistema
participant II as Inclusão Item
participant VI as Valida Item
participant LI as Lista de Item
participant ME as Movimentação de Estoque

AA->>S: Digite o item que quer adicionar ao estoque
activate AA
activate S

S->>II: incluirItem()
activate II

    alt Está preenchido
    II->>VI: materialOK()
    activate VI
    VI->>LI: listaMaterial()
    activate LI
            opt Exclusão item selecionado
            LI-->>II: Inclua novamente
            deactivate LI
            end
    else Não está preenchido
    VI-->>II: erro inclusão
    deactivate VI
    end

LI->>ME: movEstoque()
activate ME
````