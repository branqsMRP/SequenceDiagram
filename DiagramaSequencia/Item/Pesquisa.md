````mermaid
sequenceDiagram 
    actor A as Almoxarifado
    actor S as Sistema
    participant P as Pesquisa
    participant VP as Verificador Pesquisa
    participant BD as Banco de Dados

    % Pesquisa por ID

    A->>S: Digite o id do item que será pesquisado()
    Activate A
    Activate S
    S->>P: pesqItem()
    Activate P

    alt Pesquisa de Itens
        P->>VP: VerPesq()        
        Activate VP
        VP->>BD: BuscBD()
        Activate BD
        BD-->>P: pesquisa: int
        deactivate BD
        
    else
        VP-->>P: erro: string
        deactivate VP
    end

    P->>S: resultPesq()    
    deactivate P
    S->>A: Pesquisa realizada()
    deactivate S

    % Pesquisa por nome

    opt Pesquisa por nome opcional
    A->>S: Digite o nome do item que será pesquisado()
    Activate S
    S->>P: pesqItem()
    Activate P

    alt Pesquisa de Itens
        P->>VP: VerPesq()        
        Activate VP
        VP->>BD: BuscBD()
        Activate BD
        BD-->>P: pesquisa: int
        deactivate BD
        
    else
        VP-->>P: erro: string
        deactivate VP
    end

    P->>S: resultPesq()    
    deactivate P
    S->>A: Pesquisa realizada()
    deactivate S
    deactivate A
    end


````