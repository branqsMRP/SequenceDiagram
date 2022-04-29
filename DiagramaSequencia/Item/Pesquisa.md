````mermaid
sequenceDiagram 
    actor A as Almoxarifado/Admin
    participant S as Sistema
    participant P as Pesquisa
    participant VP as Verificador Pesquisa
    participant BD as Banco de Dados

    % Pesquisa por ID

    A->>S: Digite o id do item que será pesquisado()
    Activate A
    Activate S
    S->>P: pesquisarItens()
    Activate P

    alt Pesquisa de Itens
        P->>VP: validate()        
        Activate VP
        VP->>BD: buscarItem()
        Deactivate VP
        Activate BD
        BD-->>P: getItem()
        deactivate BD
                opt Pesquisa de Itens Fabricados
                    P->>VP: validate()        
                    Activate VP
                    VP->>BD: buscarItemFabricado()
                    Activate BD
                    BD-->>P: getAllItensFabricados()
                    deactivate BD
                end
        
    else
        VP-->>P: erro: string
        deactivate VP
    end


    P->>S: getItens()    
    deactivate P
    S->>A: Pesquisa realizada()
    deactivate S

    % Pesquisa por nome

    opt Pesquisa por nome opcional
    A->>S: Digite o nome do item que será pesquisado()
    Activate S
    S->>P: pesquisarItens()
    Activate P

    alt Pesquisa de Itens
        P->>VP: validate()         
        Activate VP
        VP->>BD: buscarItem()
        Deactivate VP
        Activate BD
        BD-->>P: getItem()
        deactivate BD
            opt Pesquisa de Itens Fabricados
                P->>VP: validate()        
                Activate VP
                VP->>BD: buscarItemFabricado()
                Activate BD
                BD-->>P: getAllItensFabricados()
                deactivate BD
            end
        
    else
        VP-->>P: erro: string
        deactivate VP
    end

    P->>S: getItens()    
    deactivate P
    S->>A: Pesquisa realizada()
    deactivate S
    deactivate A
    end


````