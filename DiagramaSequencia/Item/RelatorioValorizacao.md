````mermaid
sequenceDiagram 
    actor CA as Compras/Admin
    participant S as Sistema
    participant P as Pesquisa
    participant VP as Verificador Pesquisa
    participant BD as Banco de Dados
    participant PC as Pesquisa Cotação
    participant C as Cotação
    participant VC as Verificador Cotação


    % Pesquisa por ID

    CA->>S: Digite o id do item que será pesquisado()
    Activate CA
    Activate S
    S->>P: Item_BuscarValorizacaoItem()
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
    S->>CA: Pesquisa realizada()
    deactivate S

    % Pesquisa por nome

    opt Pesquisa por nome opcional
    CA->>S: Digite o nome do item que será pesquisado()
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
    S->>CA: Pesquisa realizada()
    deactivate S
    end

 % Pesquisa de cotação

    opt Pesquisa de Cotação 
    CA->>S: Ao clicar em Nome()
    activate S
    S->>PC: pesquisarCotacoes()
    activate PC
    PC->>C: atualizarCotacao()
    activate C

        alt Validação Cotação
            C->>VC: validar_AtualizarCotacoes()
            activate VC
            VC-->>C: item: string, cotacao: int
            deactivate VC
        else 
            
            VC-->>C: erro: string
            activate VC
            deactivate VC
        end
    C-->>PC: cotacao()
    deactivate C
    PC-->>S: item: string, cotacao: int
    deactivate PC
    S->>CA: Atualização de cotação realizada()
    deactivate S 
    deactivate CA
    end


````