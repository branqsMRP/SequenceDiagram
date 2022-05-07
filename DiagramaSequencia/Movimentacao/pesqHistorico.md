```` mermaid
sequenceDiagram

% alterar as classes com as classes corretas 
actor AD as Admin/Default
participant S as Sistema
participant BM as Busca Movimentação
participant VB as Valida Busca 
participant P as Pesquisa

AD->>S: Preencha os itens que deseja pesquisar
activate AD 
activate S

S->>BM: buscMov() 
activate BM

    alt Está preenchido
    BM->>VB: materialOK()
    activate VB
    VB->>BM: listaMaterial()
    else Não está preenchido
    VB-->>BM: Erro Inclusão
    deactivate VB
    end

deactivate BM

VB->>P: pesqMov()
activate P
P-->>S: Pesquisa concluida
deactivate P

S->>AD: Pesquisa
deactivate S
deactivate AD


````